<script>
  import { link } from "svelte-spa-router";
  import { onMount } from "svelte";

  let articles = [];

  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;
  const getArticles = async () => {
    const endpoint = `${API_BASE_URL}/items/articles?sort=-date_created&limit=3&fields=*,users_id.pseudo,date_created`;
    const response = await fetch(endpoint);
    const json = await response.json();
    articles = json.data;
  };

  onMount(() => {
    getArticles();
  });
</script>

<main>
  <div class="wrapper__latest">
    <h2 aria-label="Titre de la section des articles les plus récents">
      Articles les plus récents
    </h2>
    {#each articles as article}
      <section aria-label="Article">
        <h3 id="article__title-left">{article.title}</h3>
        <article>
          <img
            src={import.meta.env.VITE_URL_DIRECTUS + "/assets/" + article.image}
            alt={article.alt}
          />
          <p id="article_p-left" aria-label="Texte de l'article">
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
  <div class="wrapper__like">
    <h2 aria-label="Titre de la section des articles les plus aimés">
      Articles les plus aimés
    </h2>
    <section aria-label="Article">
      <h3 id="article__title-right">Titre article</h3>
      <article>
        <img src="https://picsum.photos/900/400" alt="photo de l'articlelink" />
        <p id="article_p-right" aria-label="Texte de l'article">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non
          risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec,
          ultricies sed, dolor. Cras elementum ultrices diam. Maecenas ligula
          massa, varius a, semper congue, euismod non, mi. Proin porttitor, orci
          nec nonummy molestie, enim est eleifend mi, non fermentum diam nisl
          sit amet erat. Duis semper. Duis arcu massa, scelerisque vitae,
          consequat in, pretium a, enim. Pellentesque congue. Ut in risus
          volutpat libero pharetra tempor. Cras vestibulum bibendum augue.
          Praesent egestas leo in pede. Praesent blandit odio eu enim.
          Pellentesque sed dui ut augue blandit sodales. Vestibulum ante ipsum
          primis in faucibus orci luctus et ultrices posuere cubilia Curae;
          Aliquam nibh. Mauris ac mauris sed pede pellentesque fermentum.
          Maecenas adipiscing ante non diam sodales hendrerit.
        </p>
      </article>

      <footer>
        <aside aria-label="Date de publication et auteur">
          <time datetime="2023-04-05" aria-label="Date de publication"
            >5 avril 2023</time
          > <span aria-hidden="true"> || </span>
          <cite title="nom de l'auteur" aria-label="Auteur">Sarah Croche</cite>
        </aside>

        <a
          class="btn-read-more"
          use:link
          href="/articles"
          aria-labelledby="article__title-left">Lire la suite</a
        >
      </footer>
    </section>
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
    @media screen and (min-width: 1024px) {
      display: flex;
      flex-direction: row;
      justify-content: center;
    }

    .wrapper__latest,
    .wrapper__like {
      @media screen and (min-width: 1024px) {
        max-width: 50%;
        padding-inline: 2rem;
      }

      h2 {
        @extend %h2;
        text-align: center;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
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
    .wrapper__like {
      @media screen and (min-width: 1024px) {
        border-left: 1px solid $color-black;
      }
    }
  }
</style>
