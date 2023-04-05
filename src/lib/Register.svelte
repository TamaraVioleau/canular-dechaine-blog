<script>
  var details = document.querySelectorAll("details");

  details.forEach(function (detail) {
    detail.addEventListener("click", function () {
      details.forEach(function (otherDetail) {
        if (otherDetail !== detail) {
          otherDetail.open = false;
        }
      });
    });
  });
</script>

<main>
  <!-- dans action mettre le nom de la page (ex: /profil)  -->

  <wrapper class="wrapper__left">
    <form action="" method="post" id="connexion" name="connexion">
      <section class="section__login section__title" aria-labelledby="login">
        <h1 id="login">Se connecter</h1>

        <details open>
          <summary>Voir le formulaire</summary>
          <article class="article__login" aria-label="formulaire de connexion">
            <label for="pseudo">Pseudo : </label>
            <input type="text" name="pseudo" id="pseudo" />
            <label for="pwd">Mot de passe : </label>
            <input type="password" name="pwd" id="pwd" />
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="Se connecter"
              spellcheck="false"
              aria-label="connexion"
            />
            <input
              class="reset"
              type="reset"
              name="reset"
              value="Réinitialiser"
              aria-label="réinitialisation"
            />
          </div>
        </details>
      </section>
    </form>
  </wrapper>

  <wrapper class="wrapper__right"
    ><form action="" method="post" id="inscription" name="inscription">
      <section class="section__register" aria-labelledby="register">
        <h1 id="statistiques">S'enregistrer :</h1>

        <details>
          <summary>Voir le formulaire</summary>
          <article
            class="article__register"
            aria-label="formulaire d'inscription"
          >
            <label for="pseudo">Pseudo : </label>
            <input type="text" name="pseudo" id="pseudo" />
            <label for="name">Nom : </label>
            <input type="text" name="name" id="name" />
            <label for="firstname">Prénom : </label>
            <input type="text" name="firstname" id="firstname" />
            <label for="email">E-mail : </label>
            <input type="email" name="email" id="email" />
            <label for="pwd">Mot de passe : </label>
            <input type="password" name="pwd" id="pwd" />
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="Se connecter"
              spellcheck="false"
              aria-label="connexion"
            />
            <input
              class="reset"
              type="reset"
              name="reset"
              value="Réinitialiser"
              aria-label="réinitialisation"
            />
          </div>
        </details>
      </section>
    </form>
  </wrapper>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    color: #312140;
    font-family: Tahoma;
    background-color: #f8f8f8;
    padding: 2.3rem;
    min-height: 100vh;
    @media screen and (min-width: 580px) {
      padding: 3.5rem;
    }
    @media screen and (min-width: 770px) {
      padding: 5rem 10rem;
    }
    @media screen and (min-width: 1024px) {
      display: flex;
      justify-content: center;
      gap: 5rem;
      margin: auto;
      min-height: 100vh;
      padding: 5rem 0rem;
    }

    .wrapper__left {
      @media screen and (min-width: 1024px) {
        min-width: 40%;
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
        }
        @media screen and (min-width: 1200px) {
        }

        .section__login {
          @extend %glassmorphism;
          padding: 1.5rem;
          @media screen and (min-width: 580px) {
            padding: 3.5rem;
          }
          h1 {
            font-size: 3rem;
            font-weight: bolder;
            display: flex;
            align-items: center;
            line-height: 3rem;
            justify-content: center;
          }
          details {
            summary {
              padding: 2rem;
              cursor: pointer;
              font-weight: bold;
            }

            .article__login {
              margin-top: 2rem;
              background-color: #f8f8f8;
              padding: 1.5rem;
              display: flex;
              flex-direction: column;
              max-width: 500px;
              margin: auto;

              label {
                padding: 1rem 0;
                font-weight: bolder;
              }
              input {
                padding: 1rem;
                background: rgba(136, 217, 143, 0.23);
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2.3rem;
            gap: 1.5rem;

            input {
              padding: 1rem;
              margin: 1rem;
              background: rgb(136 217 143 / 23%);
              border: 1px solid white;
              border-radius: 5px;
              font-size: 1.5rem;
              font-weight: bold;
              max-width: 285px;
            }
          }
        }
      }
    }

    .wrapper__right {
      @media screen and (min-width: 1024px) {
        min-width: 40%;
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
        }
        @media screen and (min-width: 1200px) {
        }
        .section__register {
          @extend %glassmorphism;
          padding: 1.5rem;
          margin-top: 2.3rem;
          @media screen and (min-width: 580px) {
            padding: 3.5rem;
          }
          @media screen and (min-width: 1024px) {
            margin-top: 0;
          }
          h1 {
            font-size: 3rem;
            font-weight: bolder;
            display: flex;
            align-items: center;
            line-height: 3rem;
            justify-content: center;
          }

          details {
            summary {
              padding: 2rem;
              cursor: pointer;
              font-weight: bold;
            }

            .article__register {
              margin-top: 2rem;
              background-color: #f8f8f8;
              padding: 1.5rem;
              display: flex;
              flex-direction: column;
              max-width: 500px;
              margin: auto;
              label {
                padding: 1rem 0;
                font-weight: bolder;
              }

              input {
                padding: 1rem;
                background: rgba(136, 217, 143, 0.23);
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2.3rem;
            gap: 1.5rem;

            input {
              padding: 1rem;
              margin: 1rem;
              background: rgb(136 217 143 / 23%);
              border: 1px solid white;
              border-radius: 5px;
              font-size: 1.5rem;
              font-weight: bold;
              max-width: 285px;
            }
          }
        }
      }
    }
  }
</style>
