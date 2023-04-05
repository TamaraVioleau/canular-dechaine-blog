<main>
  <!-- dans action mettre le nom de la page (ex: /profil)  -->
  <form action="" method="post" id="informations" name="informations">
    <wrapper class="wrapper__left">
      <section
        class="section__informations"
        aria-labelledby="userpseudo userstatut"
      >
        <header aria-label="avatar pseudo statut">
          <img
            src="src/assets/avatar-membres.png"
            alt="avatar par défaut des auteurs"
          />
          <article class="article__pseudostatut">
            <h1 id="userpseudo">Lucie Fer</h1>
            <h2 id="userstatut">Membre</h2>
          </article>
        </header>
        <article
          class="article__infoperso"
          aria-label="informations personnelles"
        >
          <label for="nom">Nom : </label>
          <input type="text" name="nom" id="nom" />
          <label for="prénom">Prénom : </label>
          <input type="text" name="prénom" id="prénom" />
          <label for="email">E-mail : </label>
          <input type="email" name="E-mail" id="email" />
          <label for="pwd">Mot de passe : </label>
          <input type="password" name="pwd" id="pwd" />
          <label for="DateEnregistrement">Date d'enregistrement : </label>
          <p id="DateEnregistrement">Ici la date d'enregistrement</p>
        </article>
      </section>     
       <div class="buttons">
        <input
          class="submit"
          type="submit"
          name="submit"
          value="Enregistrer"
          spellcheck="false"
          aria-label="Enregistrer les informations"
        />
        <input
          class="reset"
          type="reset"
          name="reset"
          value="Réinitialiser"
          aria-label="Réinitialiser les informations"
        />
      </div>
    </wrapper>

    <wrapper class="wrapper__right">
      <section class="section__statistics" aria-labelledby="statistiques">
        <article class="article__statistics">
          <h3 id="statistiques">Statistiques :</h3>
          <ol>
            <li>
              <h4>Tous mes commentaires :</h4>
              <p>XX commentaires</p>
            </li>
            <li>
                <h4>Tous mes likes :</h4>
                <p>XX likes</p>
              </li>
          </ol>
        </article>
      </section>
    </wrapper>
  </form>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    color: $color-black;
    font-family: $police;
    background-color: $color-white;
    padding: 2.3rem;
    min-height: 100vh;
    @media screen and (min-width: 580px) {
      padding: 3.5rem;
    }
    @media screen and (min-width: 770px) {
      padding: 5rem 10rem;
    }
    @media screen and (min-width: 1024px) {
      padding: 5rem 0rem;
    }
    form {
      @media screen and (min-width: 580px) {
        width: 95%;
        margin: auto;
      }
      @media screen and (min-width: 770px) {
        width: 90%;
        margin: auto;
      }
      @media screen and (min-width: 1024px) {
        display: flex;
        justify-content: center;
        gap: 10rem;
        margin: auto;
        align-items: center;
        min-height: 100vh;
      }
      @media screen and (min-width: 1200px) {
      }
      .section__informations {
        @extend %glassmorphism;
        padding: 1.5rem;
        @media screen and (min-width: 580px) {
          padding: 3.5rem;
        }

        header {
          display: flex;
          justify-content: center;
          align-items: center;
          line-height: 3rem;

          img {
            height: 75px;
            margin-right: 2.5rem;
          }
          .article__pseudostatut {
            text-align: center;
            background: none;

            h1 {
              font-size: 3rem;
              font-weight: bolder;
            }
            h2 {
              font-size: 2.4rem;
            }
          }
        }

        .article__infoperso {
          margin-top: 2rem;
          background-color: $color-white;
          padding: 1.5rem;
          display: flex;
          flex-direction: column;
          max-width: 500px;
          margin: auto;
          label {
            padding: 1rem 0;
            font-weight: bolder;
          }
          #image {
            border: none;
            background: none;
            padding: 1rem 0;
          }
          input {
            padding: 1rem;
            background: $color-greenlight;
            border: 1px solid white;
            border-radius: 5px;
            max-width: 285px;
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2.3rem;
            gap: 1.5rem;
          }
        }
      }

      .section__statistics {
        @extend %glassmorphism;
        padding: 1.5rem;
        margin-top: 2.3rem;

        @media screen and (min-width: 580px) {
          padding: 3.5rem;
        }
        @media screen and (min-width: 1024px) {
          margin-top: 0;
            min-height:635px;
        }

        .article__statistics {
          background-color: $color-white;
          padding: 1.5rem;
          max-width: 500px;
          margin: auto;
          h3 {
            font-size: 2rem;
            font-weight: bolder;
            margin-bottom: 2rem;
          }
          ol {
            list-style: disc;
            margin-left: 4rem;
            li {
                margin-bottom: 1rem;
              h4 {
                font-weight: bold;
                margin-bottom: 1rem;
              }
            }
          }
        }
      }

      .buttons {
        @extend %glassmorphism;
        margin-top: 2.3rem;
        display: flex;
        justify-content: center;
        padding: 2rem;
        @media screen and (min-width: 580px) {
          padding: 1.5rem 3.5rem;
        }
        input {
          padding: 1rem;
          margin: 1rem;
          background: $color-greenlight;
          border: 1px solid white;
          border-radius: 5px;
          font-size: 1.5rem;
          font-weight: bold;
          max-width: 285px;
        }
      }
    }
  }
</style>
