<script>
  // JS pour le compteur de mots dans l'écriture d'un article
  // Définir la longueur maximale autorisée pour le textarea
  let myMaxLength = 500;

  // Définir le seuil d'alerte pour informer l'utilisateur du nombre de caractères restants
  let myAlertThreshold = 95;

  // Initialiser le compteur de caractères à 0
  let characterCount = 0;

  // Initialiser les caractères restants avec la longueur maximale autorisée
  let charactersRemaining = myMaxLength;

  // Fonction pour gérer l'événement d'entrée (input) sur le textarea
  const handleInput = (e) => {
    // Mettre à jour le nombre de caractères en fonction de la longueur du texte dans le textarea
    characterCount = e.target.value.length;

    // Calculer les caractères restants en soustrayant le nombre de caractères actuels de la longueur maximale autorisée
    charactersRemaining = myMaxLength - characterCount;
  };

  //////////////// Requête pour récupérer les catégories /////////////////////////////////////////
  //création d'une variable qui récupère les informations sous forme de tableau
  let categories = [];

  const getCategories = async () => {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/items/categories";
    const response = await fetch(endpoint);
    const json = await response.json();

    // Récupération des données et incrémentation dans le tableau
    categories = json.data;
  };
  getCategories();

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
            "Authorization": `Bearer ${token}`,
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

<main>
  <!-- dans action mettre le nom de la page (ex: /profil)  -->
  <form action="" method="post" id="informations" name="informations">
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
          <label for="nom">Nom : </label>
          <input type="text" name="nom" id="nom" />
          <label for="prénom">Prénom : </label>
          <input type="text" name="prénom" id="prénom" />
          <label for="email">E-mail : </label>
          <input type="email" name="E-mail" id="email" />
          <label for="pwd">Mot de passe : </label>
          <input type="password" name="pwd" id="pwd" />
          <label for="DateEnregistrement">Date d'enregistrement : </label>
          <p id="DateEnregistrement"> {new Date(userData.date_created).toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric"
          })}</p>
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

    <wrapper class="wrapper__right">
      <section
        class="section__writearticle"
        aria-labelledby="ecrire-un-article"
      >
        <article class="article__writearticle">
          <h3 id="ecrire-un-article">Ecrire un article :</h3>
          <label for="category"> Catégorie de l'article :</label>
          <select id="category" name="category" required>
      <option value="">Choisir la catégorie</option>
      {#each categories as category}
        <option value={category.id}>{category.name}</option>
      {/each}
    </select>
          <label for="titre">Titre de l'article : </label>
          <input type="text" name="titre" id="titre" />
          <label for="image">Image de l'article : </label>
          <input
            type="file"
            name="image"
            id="image"
            accept="image/png, image/jpeg, image/WebpImage"
            title="Importer une image"
            aria-label="Importer une image"
          />
          <label for="textarea">Contenu de l'article :</label>
          <textarea
            name="textarea"
            id="textarea"
            maxlength={myMaxLength}
            on:input={handleInput}
            placeholder="Ecrit de la bonne humeur ici"
          />
          <p>
            Nombre de caractères restant : <span id="characterCounter"
              >{charactersRemaining}</span
            >/<span id="maximum">{myMaxLength}</span>
          </p>
        </article>
      </section>
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
    </wrapper>
  </form>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    @extend %blocprofilregister;
    form {
      @media screen and (min-width: 580px) {
        width: 95%;
        margin: auto;
      }
      @media screen and (min-width: 770px) {
        width: 90%;
        margin: auto;
      }
      @media screen and (min-width: 1024px) {
        display: flex;
        justify-content: center;
        gap: 10rem;
        margin: auto;
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

      .wrapper__right {
        min-width: 390px;

        .section__writearticle {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
          margin-top: 2rem;
          @media screen and (min-width: 1024px) {
            margin-top: 0;
          }

          .article__writearticle {
            background-color: $color-white;
            padding: 1.5rem;
            max-width: 500px;
            margin-top: 2rem;
            background-color: $color-white;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            margin: auto;
            h3 {
              font-size: 2rem;
              font-weight: bolder;
              margin-bottom: 2rem;
            }
            label {
              padding: 1rem 0;
              font-weight: bolder;
            }
            select {
              width: 100%;
              padding: 1rem;
              font-size: 1.5rem;
              max-width: 285px;
            }
            input {
              padding: 1rem;
              background: $color-greenlight;
              border: 1px solid white;
              border-radius: 5px;
              max-width: 285px;
            }
            input[type="file"] {
              font-size: 1.5rem;
              max-width: 285px;
            }

            #image {
              border: none;
              background: none;
              padding: 1rem 0;
            }
            #textarea {
              height: 200px;
            }

            p {
              font-size: 1.2rem;
              padding: 1rem;
            }
          }
        }

        .buttons {
          @extend %glassmorphism;
          margin-top: 2rem;
          display: flex;
          justify-content: center;
          padding: 2rem;
          @media screen and (min-width: 580px) {
            padding: 1.5rem 3.5rem;
          }
          input {
            @extend  %inputformbutton;
          }
        }
      }
    }
  }
</style>
