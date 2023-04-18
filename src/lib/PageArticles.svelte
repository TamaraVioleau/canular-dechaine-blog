<script>
  import { link } from "svelte-spa-router";

  export let params;

  let categoryId;
  let categoryName;
  let articles = [];

  $: if (params.id) {
    categoryId = params.id;
    getCategoryName();
    getArticles();
  }

  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

  const getArticles = async () => {
    const endpoint = `${API_BASE_URL}/items/articles?filter[categories_id][_eq]=${categoryId}&fields=*,users_id.*,date_created&sort=-date_created`;
    const response = await fetch(endpoint);
    const json = await response.json();
    articles = json.data;
  };

  const getCategoryName = async () => {
    const endpoint = `${API_BASE_URL}/items/categories/${categoryId}`;
    const response = await fetch(endpoint);
    const json = await response.json();
    categoryName = json.data.name;
  };
</script>

<main>
  <h2 aria-label="Titre de la section des articles les plus aimés">
    Les articles pour la catégorie {categoryName}
  </h2>
  <div class="wrapper">
    {#each articles as article}
      <section aria-label="Article">
        <article>
          <img
            src={import.meta.env.VITE_URL_DIRECTUS + "/assets/" + article.image}
            alt={article.alt}
          />
          <h3 id="article__title">{article.title}</h3>
          <p id="article_p" aria-label="Texte de l'article">
            {article.content}
          </p>
        </article>
        <footer>
          <aside aria-label="Date de publication et auteur">
            <time
              datetime={article.date_created}
              aria-label="Date de publication"
            >
              {new Date(article.date_created).toLocaleDateString("fr-FR", {
                day: "numeric",
                month: "numeric",
                year: "numeric",
              })}
            </time><span aria-hidden="true"> || </span>
            <cite title={article.users_id.pseudo} aria-label="Auteur"
              >{article.users_id.pseudo}</cite
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
    display: flex;
    justify-content: center;
    flex-direction: column;
    min-height: 300px;
    h2 {
      @extend %h2;
    }
    .wrapper {
      @media screen and (min-width: 1024px) {
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
      }
      @media screen and (min-width: 1440px) {
        padding-inline: 5rem;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        @media screen and (min-width: 1024px) {
          max-width: 255px;
        }
        @media screen and (min-width: 1440px) {
          max-width: 360px;
        }

        article {
          display: flex;
          flex-direction: column;
          width: 100%;

          img {
            display: block;
            max-height: 100px;
            margin: 2rem;
            box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.18);
            object-fit: cover;

            @media screen and (min-width: 580px) {
              max-height: 130px;
            }

            @media screen and (min-width: 770px) {
              max-height: 160px;
            }

            @media screen and (min-width: 1024px) {
              min-width: 160px;
              height: 300px;
            }
          }

          h3 {
            @extend %h3;
            display: -webkit-box;
            -webkit-line-clamp: 1;
            -webkit-box-orient: vertical;
            text-overflow: ellipsis;
            overflow: hidden;
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
      section:first-of-type {
        @media screen and (min-width: 1024px) {
          max-width: 570px;
          @media screen and (min-width: 1440px) {
            max-width: 780px;
          }
        }
      }
    }
  }
</style>
