<script>
  import TextareaComments from "../components/TextareaModificationArticle.svelte";


  export let params = {};
  const article_id = params.article_id;

  const getArticle = async (id) => {
    const endpoint =
      import.meta.env.VITE_URL_DIRECTUS + "/items/articles/" + id;
    const response = await fetch(endpoint);
    console.log("response", response);
    const json = await response.json();
    console.log("json", json);
    return json.data;
  };

</script>

<main>
  {#await getArticle(article_id)}
  <p>En chargement. Je cherche les données sur l'api...</p>
{:then article}
  <article>
    <img  src={import.meta.env.VITE_URL_DIRECTUS + "/assets/" + article.image}
    alt={article.alt}/>
    <h3>{article.title}</h3>
    <p id="preview" aria-label="Texte de l'article" aria-live="polite" aria-atomic="true">
      {article.content}
    </p>
  </article>
  {/await}

  <TextareaComments {params} />
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
