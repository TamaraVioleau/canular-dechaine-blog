<script>
  import { link } from "svelte-spa-router";   
  
  // Fonction de validation pour les emails
    function isValidEmail(email) {
    const emailRegex = /^[\w-]+(\.[\w-]+)*@([\w-]+\.)+[a-zA-Z]{2,7}$/;
    return emailRegex.test(email);
  }

  // Fonction de validation pour les mots de passe
  function isValidPassword(password) {
    // Le mot de passe doit contenir au moins 8 caractères, dont au moins une lettre majuscule,
    // une lettre minuscule, un chiffre et un caractère spécial.
    const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[^\da-zA-Z]).{8,}$/;
    return passwordRegex.test(password);
  }


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


  // Importation de la fonction "push" depuis le module "svelte-spa-router"
  import { push } from "svelte-spa-router";
  // Déclaration de la variable "reload" initialisée à "false"
  export let reload = false;
  // Déclaration des variables "email" et "password" pour le formulaire de login
  let email = "";
  let password = "";
  // Vérifie si l'utilisateur est déjà connecté en vérifiant la présence du token d'authentification dans le local storage
  const isLogged = window.localStorage.getItem("token") != null;
  // Si l'utilisateur est déjà connecté, on supprime le token du local storage et on recharge la page
  if (isLogged) {
    window.localStorage.removeItem("token");
    location.reload();
  }
  // Fonction appelée lors de la soumission du formulaire de login
  const handleSubmitForm = async (event) => {
    event.preventDefault();
    if (!isValidEmail(email)) {
      alert("L'email est invalide");
      return;
    }

    if (!isValidPassword(password)) {
      alert("Le mot de passe est invalide");
      return;
    }
    // Appelle la fonction "login" qui retourne un objet contenant le token d'authentification et l'ID du rôle
    const { token, roleID } = await login(email, password);
    // Enregistre le token d'authentification dans le local storage
    window.localStorage.setItem("token", token);
    console.log("Token:", token);
    // Si la variable "reload" est vraie, on recharge la page
    if (reload) {
      location.reload();
    } else {
      // Redirige l'utilisateur vers la page de profil correspondante en fonction de l'ID du rôle
      if (roleID === "213b3c24-fb05-446d-ab79-fd05adbbd6e2") {
        push("/profil-membre");
      } else if (roleID === "645cbe7e-cdf9-409c-bc58-863ce065dfbb") {
        push("/profil-auteur");
      } else if (roleID === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5") {
        push("/");
      } else {
        console.error("Unknown role ID:", roleID);
      }
    }
  };
  // Fonction qui envoie une requête de login au serveur et retourne le token d'authentification et l'ID du rôle
  const login = async (email, password) => {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/auth/login"; // URL de l'API de login
    // Envoie une requête de type "POST" avec les données de login au format JSON
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
    // Extrait le contenu de la réponse au format JSON
    const json = await response.json();
    // Récupère le token d'authentification depuis le JSON
    const token = json.data.access_token;
    // Envoie une requête pour obtenir les informations de l'utilisateur connecté avec le token d'authentification
    const userResponse = await fetch(
      import.meta.env.VITE_URL_DIRECTUS + "/users/me",
      {
        headers: {
          "Content-Type": "application/json",
          Authorization: `Bearer ${token}`,
        },
      }
    );
    // Extrait les informations de l'utilisateur connecté au format JSON
    const userJson = await userResponse.json();
    console.log("User data:", userJson);
    // Récupère l'ID du rôle depuis les informations de l'utilisateur connecté
    const roleID = userJson.data.role;
    // Retourne un objet contenant le token d'authentification et l'ID du rôle
    return { token, roleID };
  };
  //////////// Register /////////////
  // Initialisation des variables pour stocker les données du formulaire
  let pseudo = "";
  let mail = "";
  let pwd = "";
  // Fonction qui gère la soumission du formulaire
  const handleSubmit = async (event) => {
    event.preventDefault();
    if (!isValidEmail(mail)) {
      alert("L'email est invalide");
      return;
    }

    if (!isValidPassword(pwd)) {
      alert("Le mot de passe est invalide");
      return;
    }    
    const data = {
      pseudo: pseudo,
      mail: mail,
      pwd: pwd,
    };
    try {
      await register(data); // Appel de la fonction "register" qui envoie les données à l'API
      const { token, roleID } = await login(mail, pwd); // Appelle la fonction "login" pour obtenir le jeton d'authentification et l'ID du rôle
      window.localStorage.setItem("token", token); // Stockage du token dans le localStorage
      console.log("Token:", token);
      push("/profil-membre"); // Redirection vers la page du profil membre
    } catch (error) {
      console.error(error); // Affichage d'une erreur éventuelle dans la console
    }
  };
  // Fonction qui envoie les données du formulaire à l'API pour enregistrer un nouvel utilisateur
  async function register(data) {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/users"; // URL de l'API pour enregistrer un nouvel utilisateur
    const membersRoleID = "213b3c24-fb05-446d-ab79-fd05adbbd6e2"; // ID du rôle "members" dans l'API Directus
    try {
      const response = await fetch(endpoint, {
        // Envoi des données à l'API avec la méthode POST
        method: "POST",
        headers: {
          "Content-Type": "application/json", // Format des données envoyées
        },
        body: JSON.stringify({
          // Encodage des données du formulaire en JSON
          email: data.mail,
          password: data.pwd,
          pseudo: data.pseudo,
          role: membersRoleID,
          status: "active", // Statut du nouvel utilisateur
        }),
      });
      if (response.ok) {
        // Si la réponse de l'API est OK
        const json = await response.json(); // Extraction des données de la réponse au format JSON
        const token = json.data.access_token; // Récupération du token d'authentification
        return token; // Retourne le token pour qu'il soit stocké dans le localStorage
      } else {
        throw new Error("Failed to register user"); // Sinon, affiche une erreur
      }
    } catch (error) {
      console.error(error); // Affiche une erreur éventuelle dans la console
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

            <fieldset>
              <legend>Cocher pour valider votre inscription :</legend>
              <input
                id="conditions d'utilisations"
                type="checkbox"
                name="conditions d'utilisations"
                value="conditions d'utilisations"
                required
              />
              <label for="conditions d'utilisations" id="conditions"
                >J'ai lu et j'accepte les <a
                  use:link
                  href="/conditions-utilisations"
                  >présentes conditions d'utilisation</a
                ></label
              >
            </fieldset>
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
              fieldset {
                margin-top: 2rem;
              }
              #conditions {
                font-weight: 500;
              }
              label,
              legend {
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
