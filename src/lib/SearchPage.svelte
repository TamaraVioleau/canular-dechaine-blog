<script>
</script>

<main>
  <h2>Résultat de votre recherche pour [....]</h2>
  <div class="flex">
    <div class="wrapper__left">
      <section aria-label="Article">
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <article>
          <img src="https://picsum.photos/900/400" alt="photo" />
          <p aria-label="Texte de l'article">
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
          <a
            class="btn-read-more"
            href="/articles"
            role="button"
            aria-label="Aller à la nouvelle page">Lire la suite</a
          >
        </footer>
      </section>
    </div>
    <div class="wrapper__right">
      <section aria-label="Article">
        <h3 aria-label="Titre de l'article">Titre article</h3>
        <article>
          <img src="https://picsum.photos/900/400" alt="photo" />
          <p aria-label="Texte de l'article">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit.
            Perspiciatis fugiat aspernatur, alias iusto cumque repudiandae porro
            quam assumenda eveniet deserunt earum labore numquam. Lorem ipsum,
            dolor sit amet consectetur adipisicing elit. Perspiciatis fugiat
            aspernatur, sit amet consectetur adipisicing elit. Lorem ipsum,
            dolor sit amet
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
            href="/articles"
            role="button"
            aria-label="Aller à la nouvelle page">Lire la suite</a
          >
        </footer>
      </section>
    </div>
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
      font-weight: bold;
      padding: 3rem;
    }
    .flex {
      @media screen and (min-width: 1024px) {
        display: flex;
        flex-direction: row;
        justify-content: center;
      }

      .wrapper__left {
        @media screen and (min-width: 1024px) {
          max-width: 535px;
          margin-top: 3rem;
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
      }

      .wrapper__right {
        @media screen and (min-width: 1024px) {
          max-width: 535px;
          margin-top: 3rem;
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
      }
    }
  }
</style>
