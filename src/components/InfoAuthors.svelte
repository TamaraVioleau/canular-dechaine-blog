<script>
  import { onMount } from "svelte";
  // Récupère l'URL de l'API à partir de la variable d'environnement VITE_URL_DIRECTUS
  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

  // Initialise un objet vide qui contiendra les données de l'utilisateur
  let userData = {};

  // Exécute la fonction lors du montage du composant
  onMount(async () => {
    // Récupère le token d'authentification de l'utilisateur depuis le stockage local du navigateur
    const token = window.localStorage.getItem("token");
    console.log(token);

    // Si le token n'existe pas, redirige l'utilisateur vers la page de connexion
    if (!token) {
      // Redirigez l'utilisateur vers la page de connexion si nécessaire
    } else {
      // Sinon, effectue une requête pour récupérer les données de l'utilisateur
      try {
        const response = await fetch(`${API_BASE_URL}/users/me`, {
          headers: {
            Authorization: `Bearer ${token}`,
          },
        });

        // Si la requête a réussi, met à jour l'objet userData avec les données de l'utilisateur
        if (response.ok) {
          userData = await response.json();
          userData = userData.data;
        } else {
          console.error("Failed to fetch user data");
        }
      } catch (error) {
        console.error(error);
      }
    }
  });
</script>

<form action="" method="post">
  <wrapper class="wrapper__left">
    <section
      class="section__informations"
      aria-labelledby="userpseudo userstatut"
    >
      <header aria-label="avatar pseudo statut">
        <article class="article__pseudostatut">
          <h1 id="userpseudo">{userData.pseudo}</h1>
          <h2 id="userstatut">{userData.roles}</h2>
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
    </section>
    <section class="section__statistics" aria-labelledby="statistiques">
      <article class="article__statistics">
        <h3 id="statistiques">Statistiques :</h3>
        <ol>
          <li>
            <h4>Tous mes articles :</h4>
            <p>XX articles</p>
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
    }
  }
</style>
