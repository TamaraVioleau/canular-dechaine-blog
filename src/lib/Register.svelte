<script>
  var details = document.querySelectorAll("details");

  details.forEach(function (detail) {
    detail.addEventListener("click", function () {
      details.forEach(function (otherDetail) {
        if (otherDetail !== detail) {
          otherDetail.open = false;
        }
      });
    });
  });

  /////////// login ///////////

  //fonction push qui permet de naviguer entre les différentes pages de l'application
  import { push } from "svelte-spa-router";

  // variable reload qui permet de déterminer si la page doit être rechargée après l'authentification
  export let reload = false;

  // variables pour stocker les identifiants
  let email = "";
  let password = "";

  // variable qui vérifie si un token est déjà présent dans le localStorage (si oui, token supprimé et rechargement de la page)
  const isLogged = window.localStorage.getItem("token") != null;
  if (isLogged) {
    window.localStorage.removeItem("token");
    location.reload();
  }

  // Fonction appelée lors de la soumission du formulaire et qui appelle la fonction login pour obtenir un token pour le stocker dans le localStorage
  const handleSubmitForm = async (event) => {
    event.preventDefault();
    const token = await login();
    window.localStorage.setItem("token", token);

    if (reload) {
      location.reload();
    } else {
      // Naviguer vers la page d'accueil grace à svelte-spa-router
      push("/");
    }
  };

  // fonction login qui permet de récupérer le token
  const login = async () => {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/auth/login";

    const response = await fetch(endpoint, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        email: email,
        password: password,
      }),
    });

    // Extraction du contenu du body de la réponse au format json
    const json = await response.json();

    // Lit uniquement le token du json
    const token = json.data.access_token;
    return token;
  };

  /////////// Register ///////////////

  let pseudo = "";
  let mail = "";
  let pwd = "";

  const handleSubmit = async (event) => {
    event.preventDefault();

    const data = {
      pseudo: pseudo,
      mail: mail,
      pwd: pwd,
    };

    try {
      await register(data);
    } catch (error) {
      console.error(error);
    }
  };

  async function register(data) {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/users";
    const membersRoleID = "213b3c24-fb05-446d-ab79-fd05adbbd6e2";

    try {
      const response = await fetch(endpoint, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          email: data.mail,
          password: data.pwd,
          pseudo: data.pseudo,
          role: membersRoleID,
          status: "active", // définir le statut de l'utilisateur sur actif
        }),
      });

      if (response.ok) {
        const json = await response.json();
      } else {
        throw new Error("Failed to register user");
      }
    } catch (error) {
      console.error(error);
    }
  }
</script>

<main>
  <wrapper class="wrapper--left">
    <!-- dans action mettre le nom de la page (ex: /profil)  -->
    <form
      on:submit={handleSubmitForm}
      action=""
      method="post"
      id="connexion"
      name="connexion"
    >
      <section class="section--login" aria-labelledby="login">
        <h1 id="login">Se connecter</h1>

        <details open>
          <summary>Voir le formulaire</summary>
          <article class="article--login" aria-label="formulaire de connexion">
            <label for="email">E-mail : </label>
            <input
              type="email"
              name="email"
              bind:value={email}
              id="email"
              required
            />
            <label for="pwd">Mot de passe : </label>
            <input
              type="password"
              name="pwd"
              id="pwd"
              bind:value={password}
              required
            />
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="Se connecter"
              spellcheck="false"
              aria-label="Se connecter"
            />
            <input
              class="reset"
              type="reset"
              name="reset"
              value="Réinitialiser"
              aria-label="réinitialisation"
            />
          </div>
        </details>
      </section>
    </form>
  </wrapper>

  <wrapper class="wrapper--right"
    ><form
      on:submit={handleSubmit}
      action=""
      method="post"
      id="inscription"
      name="inscription"
    >
      <section class="section--register" aria-labelledby="register">
        <h1 id="statistiques">S'enregistrer :</h1>

        <details>
          <summary>Voir le formulaire</summary>
          <article
            class="article--register"
            aria-label="formulaire d'inscription"
          >
            <label for="pseudo">Pseudo : </label>
            <input
              type="text"
              name="pseudo"
              id="pseudo"
              bind:value={pseudo}
              required
            />
            <label for="email">E-mail : </label>
            <input
              type="email"
              name="email"
              id="email"
              bind:value={mail}
              required
            />
            <label for="pwd">Mot de passe : </label>
            <input
              type="password"
              name="pwd"
              id="pwd"
              bind:value={pwd}
              required
            />
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="S'enregistrer"
              spellcheck="false"
              aria-label="s'enregistrer"
            />
            <input
              class="reset"
              type="reset"
              name="reset"
              value="Réinitialiser"
              aria-label="réinitialisation"
            />
          </div>
        </details>
      </section>
    </form>
  </wrapper>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    @extend %blocprofilregister;

    .wrapper--left {
      min-width: 390px;
      form {
        @media screen and (min-width: 580px) {
          width: 95%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 770px) {
          width: 90%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 1024px) {
          min-width: 40%;
          min-width: 390px;
        }

        .section--login {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
          h1 {
            font-size: 3rem;
            font-weight: bolder;
            display: flex;
            align-items: center;
            line-height: 3rem;
            justify-content: center;
          }
          details {
            summary {
              padding: 2rem;
              cursor: pointer;
              font-weight: bold;
            }

            .article--login {
              margin-top: 2rem;
              padding: 1.5rem;
              display: flex;
              flex-direction: column;
              max-width: 500px;
              margin: auto;

              label {
                padding: 1rem 0;
                font-weight: bolder;
              }
              input {
                padding: 1rem;
                background: $color-greenlight;
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
            gap: 1.5rem;

            input {
              @extend %inputformbutton;
            }
          }
        }
      }
    }

    .wrapper--right {
      min-width: 390px;
      form {
        @media screen and (min-width: 580px) {
          width: 95%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 770px) {
          width: 90%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 1024px) {
          min-width: 40%;
          min-width: 390px;
        }
        .section--register {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
          margin-top: 2rem;
          @media screen and (min-width: 1024px) {
            margin-top: 0;
          }

          h1 {
            font-size: 3rem;
            font-weight: bolder;
            display: flex;
            align-items: center;
            line-height: 3rem;
            justify-content: center;
          }

          details {
            summary {
              padding: 2rem;
              cursor: pointer;
              font-weight: bold;
            }

            .article--register {
              margin-top: 2rem;
              padding: 1.5rem;
              display: flex;
              flex-direction: column;
              max-width: 500px;
              margin: auto;
              label {
                padding: 1rem 0;
                font-weight: bolder;
              }

              input {
                padding: 1rem;
                background: $color-greenlight;
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
            gap: 1.5rem;

            input {
              @extend %inputformbutton;
            }
          }
        }
      }
    }
  }
</style>
