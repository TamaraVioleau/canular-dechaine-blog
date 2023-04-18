<script>
  import InfoAuthors from "../components/InfoAuthors.svelte";

  // JS pour le compteur de mots dans l'écriture d'un article
  // longueur maximale dans le textarea
  let myMaxLength = 2500;
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

  let articles = [];

  let articleContent = "";
  let articleTitle = "";
  let articleAlt = "";
  let selectedCategoryId = "";

  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

  const getUserInfo = async () => {
    const response = await fetch(`${API_BASE_URL}/users/me`, {
      headers: {
        Authorization: "Bearer " + localStorage.getItem("token"),
      },
    });
    const json = await response.json();
    return json.data;
  };

  const postComment = async () => {
    const userInfo = await getUserInfo();
    const categoriesId = await getCategories();
    const response = await fetch(
      import.meta.env.VITE_URL_DIRECTUS + "/items/articles",
      {
        method: "POST",
        headers: {
          "content-type": "application/json",
          Authorization: "Bearer " + localStorage.getItem("token"),
        },
        body: JSON.stringify({
          title: articleTitle,
          content: articleContent,
          users_id: userInfo.id,
          categories_id: selectedCategoryId,
          alt:  articleAlt,
        }),
      }
    );
    const json = await response.json();
    return json.data;
  };

  const handleSubmitForm = async (event) => {
    event.preventDefault();
    const userInfo = await getUserInfo();
    const article = await postComment();
    article.users_id = userInfo; // Ajoutez les informations de l'utilisateur au commentaire
    articles.push(article);
    articles = [...articles];
    articleContent = "";
  };
</script>

<main>
  <InfoAuthors />
  <!-- dans action mettre le nom de la page (ex: /profil)  -->
  <form
    action=""
    method="post"
    id="articles"
    name="informations"
    on:submit={handleSubmitForm}
  >
    <wrapper class="wrapper__right">
      <section
        class="section__writearticle"
        aria-labelledby="ecrire-un-article"
      >
        <article class="article__writearticle">
          <h3 id="ecrire-un-article">Ecrire un article :</h3>
          <label for="category"> Catégorie de l'article :</label>
          <select
            id="category"
            name="category"
            bind:value={selectedCategoryId}
            required
          >
            <option value="">Choisir la catégorie</option>
            {#each categories as category}
              <option value={category.id}>{category.name}</option>
            {/each}
          </select>
          <label for="titre">Titre de l'article : </label>
          <input
            type="text"
            name="titre"
            id="titre"
            bind:value={articleTitle}
          />
          <label for="image">Image de l'article : </label>
          <input
            type="file"
            name="image"
            id="image"
            accept="image/png, image/jpeg, image/WebpImage"
            title="Importer une image"
            aria-label="Importer une image"
          />
          <label for="image">Description courte de l'image : </label>
          <input
            type="text"
            name="description image"
            id="description"
            bind:value={articleAlt}
          />
          <label for="textarea">Contenu de l'article :</label>
          <textarea
            name="textarea"
            id="textarea"
            maxlength={myMaxLength}
            on:input={handleInput}
            bind:value={articleContent}
            placeholder="Ecrit de la bonne humeur ici"
          />
          <p>
            Nombre de caractères restant : <span id="characterCounter"
              >{charactersRemaining}</span
            >/<span id="maximum">{myMaxLength}</span>
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
    </wrapper>
  </form>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    @extend %blocprofilregister;
    @media screen and (min-width: 580px) {
      padding: 7.5rem;
    }
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

      .wrapper__right {
        min-width: 390px;

        .section__writearticle {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
          margin-top: 2rem;
          @media screen and (min-width: 1024px) {
            margin-top: 0;
          }
          @media screen and (min-width: 1440px) {
         min-height:820px;
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
            }
            input {
              padding: 1rem;
              background: $color-greenlight;
              border: 1px solid white;
              border-radius: 5px;
            }
            input[type="file"] {
              font-size: 1.5rem;
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
          @media screen and (min-width: 1440px) {
            flex-direction: row;
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
  }
</style>
