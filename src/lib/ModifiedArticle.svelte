<script>
  // Importe le composant TextareaModification depuis le fichier TextareaModificationArticle.svelte
  import TextareaModification from "../components/TextareaModificationArticle.svelte";

  // Exporte une variable params pour permettre de recevoir des paramètres externes.
  export let params = {};

  // Récupère l'ID de l'article depuis les paramètres.
  const article_id = params.article_id;

  // Fonction asynchrone getArticle qui récupère un article en fonction de son ID.
  const getArticle = async (id) => {
    // Construit l'URL de l'API pour récupérer l'article correspondant à l'ID donné.
    const endpoint =
      import.meta.env.VITE_URL_DIRECTUS + "/items/articles/" + id;

    // Effectue une requête fetch vers l'URL de l'API.
    const response = await fetch(endpoint);
    //console.log("response", response);

    // Attend la réponse et la convertit en objet JSON.
    const json = await response.json();
    //console.log("json", json);

    // Retourne les données de l'article
    return json.data;
  };
</script>

<main>
  <!-- Utilise la syntaxe await pour attendre que la fonction getArticle soit résolue avec l'ID de l'article. -->
  {#await getArticle(article_id)}
  
    <!-- Affiche un message pendant le chargement des données de l'article. -->
    <p>En chargement. Je cherche les données sur l'api...</p>

    <!-- Une fois la promesse résolue, récupère et affiche les informations de l'article. -->
  {:then article}
    <article>
      <img
        src={import.meta.env.VITE_URL_DIRECTUS + "/assets/" + article.image}
        alt={article.alt}
      />
      <h3>{article.title}</h3>
      <p
        id="preview"
        aria-label="Texte de l'article"
        aria-live="polite"
        aria-atomic="true"
      >
        {article.content}
      </p>
    </article>

    <!-- Ferme la syntaxe await -->
  {/await}

  <!-- Inclut le composant TextareaModification en passant les paramètres reçus. -->
  <TextareaModification {params} />
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    font-family: $police;
    background-color: $color-white;
    padding: 3rem;
    color: $color-black;
    @media screen and (min-width: 580px) {
      padding: 3rem;
      @media screen and (min-width: 1024px) {
        display: flex;
        justify-content: center;
        flex-direction: column;
      }
    }

    article {
      display: block;
      padding: 2rem;
      margin: 3rem;
      @extend %glassmorphism;
      @media screen and (min-width: 770px) {
        padding-inline: 17vw;
        padding-top: 5rem;
      }
      @media screen and (min-width: 1024px) {
        padding-inline: 15vw;
        max-width: 910px;
        min-width: 910px;
        align-self: center;
      }
      @media screen and (min-width: 1440px) {
        padding-inline: 10vw;
      }

      img {
        min-width: 100%;
        max-height: 160px;
        max-width: 100%;
        object-fit: cover;
        @extend %glassmorphism;
      }

      h3 {
        @extend %h3;
      }
      #preview {
        font-family: $police;
        padding: 2rem;
        @extend %p;
      }
    }
  }
</style>
