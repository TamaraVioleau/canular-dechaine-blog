<script>
</script>

<main>
  <div class="wrapper__latest">
    <h2 class="title_like">Articles les plus aimés</h2>
    <article aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>

      <img src="https://picsum.photos/200/300/?blur" alt="photo" />

      <p aria-label="Texte de l'article">
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
        fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
        eveniet deserunt earum labore numquam
      </p>

      <button class="btn-read-more" aria-label="Lire la suite"
        ><a href="lien_vers_la_page_de_l'article">Lire la suite</a></button
      >

      <section class="section__dateauthor">
        <aside class="date" aria-label="Date de publication">24/03/2023</aside>

        <aside class="author" aria-label="Auteur de l'article">
          Sarah Croche
        </aside>
      </section>
    </article>
    
  </div>
  <div class="wrapper__like">
    <h2 class="title_like">Articles les plus aimés</h2>
    <article aria-label="Article">
      <h3 aria-label="Titre de l'article">Titre article</h3>

      <img src="https://picsum.photos/200/300/?blur" alt="photo" />

      <p aria-label="Texte de l'article">
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Perspiciatis
        fugiat aspernatur, alias iusto cumque repudiandae porro quam assumenda
        eveniet deserunt earum labore numquam
      </p>

      <button class="btn-read-more" aria-label="Lire la suite"
        ><a href="lien_vers_la_page_de_l'article">Lire la suite</a></button
      >

      <section class="section__dateauthor">
        <aside class="date" aria-label="Date de publication">24/03/2023</aside>

        <aside class="author" aria-label="Auteur de l'article">
          Sarah Croche
        </aside>
      </section>
    </article>
  </div>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    font-family: Tahoma;
    @media screen and (min-width: 1024px) {
      display: flex;
      flex-direction: row;
    }

    .wrapper__latest {
      h2 {
        text-align: center;
        padding-top: 5px;
        font-weight: bold;
        text-transform: uppercase;
        position: relative;
        padding: 3rem;
      }

      article {
        @extend %glassmorphism;
        margin: 3rem;

        h3 {
          text-align: center;
          font-weight: bold;
          color: #312140;
          font-family: Tahoma;
          padding: 2rem;
        }
        img {
          display: none;
          @media screen and (min-width: 1024px) {
            display: block;
            width: 200px;
            height: 200px;
            margin: 2rem;
            box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.18);
          }
        }

        p {
          display: flex;
          justify-content: space-evenly;
          padding-top: 2rem;
          margin-bottom: 2rem;
          font-family: Tahoma;
          padding-left: 1rem;
          padding-right: 1rem;
          text-align: left;
        }

        button {
          background-color: #88d98f3b;
          border: 1px solid transparent;
          border-radius: 5px;
          font-size: 14px;
          padding: 10px;
        }
        .btn-read-more a {
          text-decoration: none;
          color: #312140;
          font-family: Tahoma;
        }

        .section__dateauthor {
          display: flex;
          justify-content: flex-end;
          padding: 1rem;
          margin-top: 1rem;
          .date {
            display: flex;
            margin-right: 1rem;
          }
          .author {
            display: flex;
            justify-content: flex-end;
            font-weight: bold;
          }
        }
      }
    }

    .wrapper__like {
      h2 {
        text-align: center;
        padding-top: 5px;
        font-weight: bold;
        text-transform: uppercase;
        position: relative;
        padding: 3rem;
      }

      article {
        @extend %glassmorphism;
        margin: 3rem;

        h3 {
          text-align: center;
          font-weight: bold;
          color: #312140;
          font-family: Tahoma;
          padding: 2rem;
        }
        img {
          display: none;
          @media screen and (min-width: 1024px) {
            display: block;
            width: 200px;
            height: 200px;
            margin: 2rem;
            box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.18);
          }
        }

        p {
          display: flex;
          justify-content: space-evenly;
          padding-top: 2rem;
          margin-bottom: 2rem;
          font-family: Tahoma;
          padding-left: 1rem;
          padding-right: 1rem;
          text-align: left;
        }

        button {
          background-color: #88d98f3b;
          border: 1px solid transparent;
          border-radius: 5px;
          font-size: 14px;
          padding: 10px;
        }
        .btn-read-more a {
          text-decoration: none;
          color: #312140;
          font-family: Tahoma;
        }

       .section__dateauthor {
          display: flex;
          justify-content: flex-end;
          padding: 1rem;
          margin-top: 1rem;
          .date {
            display: flex;
            margin-right: 1rem;
          }
          .author {
            display: flex;
            justify-content: flex-end;
            font-weight: bold;
          }
        }
      }
    }
  }

  /*   //FIN DU BON CODE




  .article:first-of-type {
    margin-bottom: 4rem;
  }

  h2 {
    //bon h2

  }

  img {
    display: none;

    .header:nth-child(n + 4) {
      display: none;
    }
    .btn-read-more a {
      text-decoration: none;
    }
  } */
  /* 
  //////
  @media screen and (min-width: 1024px) {
    article {
      display: grid;
      grid-template-columns: 1fr 2fr;
      grid-template-areas:
        "img title"
        "img text"
        "date_author button ";
      grid-gap: 1rem;
    }

    img {
      display: block;
      grid-area: img;
      width: 200px;
      height: 200px;
      border-radius: 10px;
      padding: 5px;
    }

    h3 {
      grid-area: title;
    }

    p {
      grid-area: text;
      padding: 0;
      margin: -30px 5px 10px 5px;
      text-align: left;
      line-height: 1.5;
    }

    button {
      grid-area: button;
      width: 50%;
      justify-self: end;
      margin: 25px;
    }
    .btn-read-more a {
      text-decoration: none;
    }

    .date_author {
      grid-area: date_author;
      align-self: end;
      padding: 0;
      margin-top: 0;
      justify-self: start;
      transform: translateY(-50px);
    }

    .header {
      display: flex;
      flex-direction: column;
      padding: 20px;
      margin: 20px;
      text-align: left;
    }
  }
 */
</style>
