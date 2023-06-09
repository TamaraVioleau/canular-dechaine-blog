<script>
  import { onMount } from "svelte";
  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

  //Récupération du nombre d'articles
  let userData = {};
  let articleCount = "";

  const getAuthorArticleCount = async (authorId) => {
    try {
      const response = await fetch(
        `${API_BASE_URL}/items/articles?filter[users_id][_eq]=${authorId}`
      );
      if (response.ok) {
        const json = await response.json();
        return json.data.length;
      } else {
        console.error("Failed to fetch author's articles");
        return 0;
      }
    } catch (error) {
      console.error(error);
      return 0;
    }
  };

  onMount(async () => {
    const token = window.localStorage.getItem("token");

    if (!token) {
      // Redirigez l'utilisateur vers la page de connexion si nécessaire
    } else {
      try {
        const response = await fetch(`${API_BASE_URL}/users/me`, {
          headers: {
            Authorization: `Bearer ${token}`,
          },
        });

        if (response.ok) {
          userData = await response.json();
          userData = userData.data;

          // Récupère le nombre d'articles écrits par l'auteur connecté
          articleCount = await getAuthorArticleCount(userData.id);
        } else {
          console.error("Failed to fetch user data");
        }
      } catch (error) {
        console.error(error);
      }
    }
  });

  //Modification des informations personnelles
  async function updateUser(event) {
    event.preventDefault();

    const email = document.getElementById("email").value;
    const pwd = document.getElementById("pwd").value;

    try {
      const response = await fetch(`${API_BASE_URL}/users/${userData.id}`, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
          Authorization: `Bearer ${window.localStorage.getItem("token")}`,
        },
        body: JSON.stringify({
          email: email,
          password: pwd,
        }),
      });

      if (response.ok) {
        const updatedUser = await response.json();
        userData = updatedUser.data;
        alert("Les informations de l'utilisateur ont été mises à jour");
      } else {
        console.error("Failed to update user data");
        alert("Échec de la mise à jour des informations de l'utilisateur");
      }
    } catch (error) {
      console.error(error);
      alert("Échec de la mise à jour des informations de l'utilisateur");
    }
  }
</script>

<form
  action=""
  method="post"
  on:submit|preventDefault={updateUser}
  id="informations"
  name="informations"
>
  <wrapper class="wrapper__left">
    <section
      class="section__informations"
      aria-labelledby="userpseudo userstatut"
    >
      <header aria-label="avatar pseudo statut">
        <img
          src={import.meta.env.VITE_URL_DIRECTUS +
            "/assets/" +
            userData.imgprofil}
          alt="avatar par défaut des membres"
        />
        <article class="article__pseudostatut">
          <h1 id="userpseudo">{userData.pseudo}</h1>
          <h2 id="userstatut">Auteur</h2>
        </article>
      </header>
      <article
        class="article__infoperso"
        aria-label="informations personnelles"
      >
        <label for="email">E-mail : </label>
        <input type="email" name="E-mail" id="email" />
        <label for="pwd">Mot de passe : </label>
        <input type="password" name="pwd" id="pwd" />
        <label for="DateEnregistrement">Date d'enregistrement : </label>
        <p id="DateEnregistrement">
          {new Date(userData.date_created).toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric",
          })}
        </p>
      </article>
      <div class="buttons">
        <input
          class="submit"
          type="submit"
          name="submit"
          value="Enregistrer"
          spellcheck="false"
          aria-label="Enregistrer les informations"
        />
        <input
          class="reset"
          type="reset"
          name="reset"
          value="Réinitialiser"
          aria-label="Réinitialiser les informations"
        />
      </div>
    </section>
    <section class="section__statistics" aria-labelledby="statistiques">
      <article class="article__statistics">
        <h3 id="statistiques">Statistiques :</h3>
        <ol>
          <li>
            <h4>Tous mes articles :</h4>
            <p>{articleCount} articles</p>
          </li>
        </ol>
      </article>
    </section>
  </wrapper>
</form>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  form {
    @media screen and (min-width: 580px) {
    }
    @media screen and (min-width: 770px) {
    }
    @media screen and (min-width: 1024px) {
      display: flex;
      justify-content: center;
    }
    @media screen and (min-width: 1200px) {
    }
    .wrapper__left {
      min-width: 390px;

      .section__informations {
        @extend %glassmorphism;
        @extend %paddingprofilregister;

        @media screen and (min-width: 580px) {
          padding: 3.5rem;
        }
        @media screen and (min-width: 1024px) {
          min-height: 546px;
        }

        header {
          display: flex;
          justify-content: center;
          align-items: center;
          line-height: 3rem;
          padding: 1rem;
          img {
            height: 75px;
            margin-right: 2.5rem;
          }
          .article__pseudostatut {
            text-align: center;
            background: none;

            h1 {
              font-size: 3rem;
              font-weight: bolder;
            }
            h2 {
              font-size: 2.4rem;
            }
          }
        }
        .article__infoperso {
          margin-top: 2rem;
          background-color: $color-white;
          padding: 1.5rem;
          display: flex;
          flex-direction: column;
          max-width: 500px;
          margin: auto;
          label {
            padding: 1rem 0;
            font-weight: bolder;
          }
          #image {
            border: none;
            background: none;
            padding: 1rem 0;
          }
          input {
            padding: 1rem;
            background: $color-greenlight;
            border: 1px solid white;
            border-radius: 5px;
            max-width: 285px;
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
            gap: 1.5rem;
          }
        }
      }

      .section__statistics {
        @extend %glassmorphism;
        @extend %paddingprofilregister;
        margin-top: 2rem;

        .article__statistics {
          background-color: $color-white;
          padding: 1.5rem;
          max-width: 500px;
          margin: auto;

          h3 {
            font-size: 2rem;
            font-weight: bolder;
            margin-bottom: 2rem;
          }
          ol {
            list-style: disc;
            margin-left: 4rem;
            li {
              h4 {
                font-weight: bold;
                margin-bottom: 1rem;
              }
            }
          }
        }
      }
      .buttons {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 2rem;
        @media screen and (min-width: 770px) {
          flex-direction: row;
        }
        @media screen and (min-width: 1024px) {
          flex-direction: column;
        }
        .submit,
        .reset {
          @extend %button;
          min-width: 220px;
          box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
        }
        .submit:active,
        .reset:active {
          @extend %buttonactive;
        }
        .submit:hover,
        .reset:hover {
          background-color: $color-greenlight;
        }

        @media screen and (min-width: 580px) {
          padding: 1.5rem 3.5rem;
        }

        input {
          @extend %inputformbutton;
        }
      }
    }
  }
</style>
