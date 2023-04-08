<script>
  import { link } from "svelte-spa-router";
</script>

<main>
  <div class="wrapper__latest">
    <h2>Articles les plus récents</h2>
    <section aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <p aria-label="Texte de l'article">
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
  <div class="wrapper__like">
    <h2>Articles les plus aimés</h2>
    <section aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>
      <article>
        <img src="https://picsum.photos/900/400" alt="photo" />
        <p aria-label="Texte de l'article">
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
    @media screen and (min-width: 1024px) {
      display: flex;
      flex-direction: row;
      justify-content: center;
    }

    .wrapper__latest {
      @media screen and (min-width: 1024px) {
        max-width: 50%;
        margin-top: 3rem;
      }

      h2 {
        @extend %h2;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        h3 {
          text-align: center;
          font-weight: bold;
          color: $color-black;
          padding: 2rem;
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
              min-width: 160px;
              height: 160px;
              margin: 2rem;
              box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
              backdrop-filter: blur(4px);
              -webkit-backdrop-filter: blur(4px);
              border-radius: 10px;
              border: 1px solid rgba(255, 255, 255, 0.18);
              object-fit: cover;
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
              height: 172px;
              display: -webkit-box;
              -webkit-line-clamp: 7;
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
    }

    .wrapper__like {
      @media screen and (min-width: 1024px) {
        max-width: 50%;
        margin-top: 3rem;
        border-left: 1px solid black;
      }

      h2 {
  @extend %h2;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        h3 {
          text-align: center;
          font-weight: bold;
          padding: 2rem;
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
              min-width: 160px;
              height: 160px;
              margin: 2rem;
              box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
              backdrop-filter: blur(4px);
              -webkit-backdrop-filter: blur(4px);
              border-radius: 10px;
              border: 1px solid rgba(255, 255, 255, 0.18);
              object-fit: cover;
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
              height: 172px;
              display: -webkit-box;
              -webkit-line-clamp: 7;
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
    }
  }
</style>
