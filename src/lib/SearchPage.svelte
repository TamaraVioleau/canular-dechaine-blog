<script>
  import { link } from "svelte-spa-router";
 import { onMount } from "svelte";
 
const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

export let params;

let query;
let articles = [];

onMount(async () => {
  if (params.query) {
    query = decodeURIComponent(params.query);

    const endpoint = `${API_BASE_URL}/items/articles?search=${query}`;
    const response = await fetch(endpoint);
    const json = await response.json();
    articles = json.data;
  }
});
</script>


<main>
  <h2 aria-label="Titre de la section de recherche">
    Résultat de votre recherche pour {query}
  </h2>
  <div class="wrapper">
    {#each articles as article}
      <section aria-label="Article">
        <h3 id="article__title-left">{article.title}</h3>
        <article>
          <img src="https://picsum.photos/900/400" alt="photo" />
          <p id="article_p-left" aria-label="Texte de l'article">
            {article.content}
          </p>
        </article>
        <footer>
          <aside aria-label="Date de publication et auteur">
            <time datetime="2023-04-05" aria-label="Date de publication"
              >5 avril 2023</time
            > <span aria-hidden="true"> || </span>
            <cite title="nom de l'auteur" aria-label="Auteur">Sarah Croche</cite
            >
          </aside>

          <a
          class="btn-read-more"
          use:link
          href={`/article/${article.id}`}
          aria-labelledby="article__title-right">Lire la suite</a
        >
        </footer>
      </section>
    {/each}
  </div>
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
    h2 {
      @extend %h2;
    }

    .wrapper {
      @media screen and (min-width: 1024px) {
        display: flex;
        flex-direction: row;
        justify-content: center;
        padding-inline: 2rem;
        flex-wrap: wrap;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        @media screen and (min-width: 1024px) {
          max-width: 39vw;
        }
        h3 {
          display: -webkit-box;
          -webkit-line-clamp: 1;
          -webkit-box-orient: vertical;
          text-overflow: ellipsis;
          overflow: hidden;
          @extend %h3;
        }
        article {
          @media screen and (min-width: 770px) {
            display: flex;
          }

          img {
            display: none;
            @media screen and (min-width: 770px) {
              display: block;
              min-width: 100px;
              height: 100px;
              margin: 2rem;
              box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
              backdrop-filter: blur(4px);
              -webkit-backdrop-filter: blur(4px);
              border-radius: 10px;
              border: 1px solid rgba(255, 255, 255, 0.18);
              object-fit: cover;
            }
            @media screen and (min-width: 1024px) {
              display: block;
              min-width: 110px;
              height: 160px;
            }
            @media screen and (min-width: 1440px) {
              min-width: 160px;
            }
          }

          p {
            @extend %p;
            padding: 1rem;
            height: 110px;
            margin: 1rem;

            display: -webkit-box;
            -webkit-line-clamp: 4;
            -webkit-box-orient: vertical;
            text-overflow: ellipsis;
            overflow: hidden;
            @media screen and (min-width: 1024px) {
              height: 175px;
              display: -webkit-box;
              -webkit-line-clamp: 7;
              -webkit-box-orient: vertical;
              overflow: hidden;
              text-overflow: ellipsis;
            }
          }
        }

        footer {
          display: flex;
          padding: 1rem;
          margin: 1rem;
          flex-direction: column;
          aside {
            display: flex;
            margin-right: 1rem;
            font-size: 1.3rem;
            gap: 1rem;
            time {
              font-style: italic;
            }
            cite {
              font-style: normal;
              font-weight: bold;
            }
          }
          .btn-read-more {
            @extend %button;
          }
          .btn-read-more:hover {
            background-color: $color-greenlight;
          }
        }
      }
    }
  }
</style>
