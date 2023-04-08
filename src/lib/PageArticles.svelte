<script>
  export let params;

  // Initialise les variables pour stocker l'ID de la catégorie, le nom de la catégorie et les articles
  let categoryId;
  let categoryName;
  let articles = [];

  // Le $: permet de réagir aux changements de params.id et mettre à jour categoryId, categoryName, et articles
  $: if (params.id) {
    categoryId = params.id;
    // Appelle la fonction 'getCategoryName()' pour récupérer le nom de la catégorie
    getCategoryName();
    // Appelle la fonction 'getArticles()' pour récupérer les articles de la catégorie
    getArticles();
  }

  // Récupération des articles de la catégorie
  const getArticles = async () => {
    const endpoint = `${
      import.meta.env.VITE_URL_DIRECTUS
    }/items/articles?filter[categories_id][_eq]=${categoryId}`;
    const response = await fetch(endpoint);
    const json = await response.json();
    articles = json.data;
  };

  // Récupération du nom de la catégorie
  const getCategoryName = async () => {
    const endpoint = `${
      import.meta.env.VITE_URL_DIRECTUS
    }/items/categories/${categoryId}`;
    const response = await fetch(endpoint);
    const json = await response.json();
    categoryName = json.data.name;
  };
</script>

<main>
  <h2>Les articles pour la catégorie {categoryName}</h2>
  <div class="wrapper">
    {#each articles as article}
      <section aria-label="Article">
        <article>
          <img src={article.image} alt="{article.alt}" />
          <h3 aria-label="Titre de l'article">{article.title}</h3>
          <p aria-label={article.content}>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit.
            Perspiciatis fugiat aspernatur, alias iusto cumque repudiandae porro
            quam assumenda eveniet deserunt earum labore numquam. Lorem ipsum,
            dolor sit amet consectetur adipisicing elit. Perspiciatis fugiat
            aspernatur, sit amet consectetur adipisicing elit. Lorem ipsum,
            dolor sit amet fugiat aspernatur, sit amet.Lorem ipsum, dolor sit
            amet consectetur adipisicing elit. Perspiciatis fugiat aspernatur,
            alias iusto cumque repudiandae porro quam assumenda eveniet deserunt
            earum labore numquam.
          </p>
        </article>
        <footer class="footer__dateauthor">
          <aside
            class="aside__dateauthor"
            aria-label="Date de publication et auteur"
          >
            <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
            <cite title="nom de l'auteur">Sarah Croche</cite>
          </aside>
          <button class="btn-read-more" aria-label="Lire la suite"
            ><a href="lien_vers_la_page_de_l'article">Lire la suite</a></button
          >
        </footer>
      </section>
    {/each}

    <!-- SUITE DES ARTICLES -->
    <section aria-label="Article">
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet fugiat
          aspernatur, sit amet.Lorem ipsum, dolor sit amet consectetur
          adipisicing elit. Perspiciatis fugiat aspernatur, alias iusto cumque
          repudiandae porro quam assumenda eveniet deserunt earum labore
          numquam.
        </p>
      </article>
      <footer class="footer__dateauthor">
        <aside
          class="aside__dateauthor"
          aria-label="Date de publication et auteur"
        >
          <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
          <cite title="nom de l'auteur">Sarah Croche</cite>
        </aside>
        <a
          class="btn-read-more"
          use:link
          href="/articles"
          role="button"
          aria-label="Aller à la page de l'article">Lire la suite</a
        >
      </footer>
    </section>
    <section aria-label="Article">
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet fugiat
          aspernatur, sit amet.Lorem ipsum, dolor sit amet consectetur
          adipisicing elit. Perspiciatis fugiat aspernatur, alias iusto cumque
          repudiandae porro quam assumenda eveniet deserunt earum labore
          numquam.
        </p>
      </article>
      <footer class="footer__dateauthor">
        <aside
          class="aside__dateauthor"
          aria-label="Date de publication et auteur"
        >
          <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
          <cite title="nom de l'auteur">Sarah Croche</cite>
        </aside>
        <a
          class="btn-read-more"
          use:link
          href="/articles"
          role="button"
          aria-label="Aller à la page de l'article">Lire la suite</a
        >
      </footer>
    </section>
    <section aria-label="Article">
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet fugiat
          aspernatur, sit amet.Lorem ipsum, dolor sit amet consectetur
          adipisicing elit. Perspiciatis fugiat aspernatur, alias iusto cumque
          repudiandae porro quam assumenda eveniet deserunt earum labore
          numquam.
        </p>
      </article>
      <footer class="footer__dateauthor">
        <aside
          class="aside__dateauthor"
          aria-label="Date de publication et auteur"
        >
          <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
          <cite title="nom de l'auteur">Sarah Croche</cite>
        </aside>
        <a
          class="btn-read-more"
          use:link
          href="/articles"
          role="button"
          aria-label="Aller à la page de l'article">Lire la suite</a
        >
      </footer>
    </section>
    <section aria-label="Article">
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet fugiat
          aspernatur, sit amet.Lorem ipsum, dolor sit amet consectetur
          adipisicing elit. Perspiciatis fugiat aspernatur, alias iusto cumque
          repudiandae porro quam assumenda eveniet deserunt earum labore
          numquam.
        </p>
      </article>
      <footer class="footer__dateauthor">
        <aside
          class="aside__dateauthor"
          aria-label="Date de publication et auteur"
        >
          <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
          <cite title="nom de l'auteur">Sarah Croche</cite>
        </aside>
        <a
          class="btn-read-more"
          use:link
          href="/articles"
          role="button"
          aria-label="Aller à la page de l'article">Lire la suite</a
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
    display: flex;
    justify-content: center;
    flex-direction: column;
    h2 {
      font-weight: bold;
      padding: 3rem;
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
            text-align: center;
            font-weight: bold;
            padding: 2rem;
          }
          p {
            line-height: 2rem;
            padding: 1rem;
            text-align: left;
            height: 112px;
            margin: 1rem;

            display: -webkit-box;
            -webkit-line-clamp: 5;
            -webkit-box-orient: vertical;
            text-overflow: ellipsis;
            overflow: hidden;
            @media screen and (min-width: 1024px) {
              height: 172px;
              display: -webkit-box;
              -webkit-line-clamp: 8;
              -webkit-box-orient: vertical;
              overflow: hidden;
              text-overflow: ellipsis;
            }
          }
        }

        .footer__dateauthor {
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
