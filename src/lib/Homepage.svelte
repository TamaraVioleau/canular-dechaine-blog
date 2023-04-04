<script>
</script>

<main>
  <div class="wrapper__latest">
    <h2>Articles les plus récents</h2>
    <section aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>
      <article>
        <img src="https://picsum.photos/200/300/?blur" alt="photo" />
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet fugiat
          aspernatur, sit amet.
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
  </div>
  <div class="wrapper__like">
    <h2>Articles les plus aimés</h2>
    <section aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>
      <article>
        <img src="https://picsum.photos/200/300/?blur" alt="photo" />
        <p aria-label="Texte de l'article">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
          fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
          eveniet deserunt earum labore numquam. Lorem ipsum, dolor sit amet
          consectetur adipisicing elit. Perspiciatis fugiat aspernatur, sit amet
          consectetur adipisicing elit. Lorem ipsum, dolor sit amet
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
  </div>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    font-family: Tahoma;
    background-color: #f8f8f8;
    @media screen and (min-width: 1024px) {
      display: flex;
      flex-direction: row;
    }

    .wrapper__latest {
      @media screen and (min-width: 1024px) {
        width: 50%;
        border-right: 1px solid #312140;
      }
      h2 {
        text-align: center;
        padding-top: 5px;
        font-weight: bold;
        text-transform: uppercase;
        position: relative;
        padding: 3rem;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        h3 {
          text-align: center;
          font-weight: bold;
          color: #312140;
          font-family: Tahoma;
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
            font-family: Tahoma;
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
          button {
            background-color: #88d98f3b;
            border: 1px solid transparent;
            border-radius: 5px;
            font-size: 14px;
            padding: 2rem;
            margin:2rem;
            
          }
          .btn-read-more a {
            text-decoration: none;
            color: #312140;
            font-family: Tahoma;
          }
        }
      }
    }

    .wrapper__like {
      @media screen and (min-width: 1024px) {
        width: 50%;
        
      }

      h2 {
        text-align: center;
        padding-top: 5px;
        font-weight: bold;
        text-transform: uppercase;
        position: relative;
        padding: 3rem;
      }

      section {
        @extend %glassmorphism;
        margin: 3rem;
        h3 {
          text-align: center;
          font-weight: bold;
          color: #312140;
          font-family: Tahoma;
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
            font-family: Tahoma;
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
          button {
            background-color: #88d98f3b;
            border: 1px solid transparent;
            border-radius: 5px;
            font-size: 14px;
            padding: 2rem;
            margin: 2rem;
          }
          .btn-read-more a {
            text-decoration: none;
            color: #312140;
            font-family: Tahoma;
          }
        }
      }
    }
  }
</style>
