<script>
</script>

<main>
  <wrapper class="wrapper--left">
    <!-- dans action mettre le nom de la page (ex: /profil)  -->
    <form action="" method="post" id="connexion" name="connexion">
      <section class="section--login" aria-labelledby="login">
        <h1 id="login">Se connecter</h1>

        <details open>
          <summary>Voir le formulaire</summary>
          <article class="article--login" aria-label="formulaire de connexion">
            <label for="pseudo">Pseudo : </label>
            <input type="text" name="pseudo" id="pseudo" required/>
            <label for="pwd">Mot de passe : </label>
            <input type="password" name="pwd" id="pwd" required/>
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="Se connecter"
              spellcheck="false"
              aria-label="Se connecter"
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

  <wrapper class="wrapper--right"
    ><form action="" method="post" id="inscription" name="inscription">
      <section class="section--register" aria-labelledby="register">
        <h1 id="statistiques">S'enregistrer :</h1>

        <details>
          <summary>Voir le formulaire</summary>
          <article
            class="article--register"
            aria-label="formulaire d'inscription"
          >
            <label for="pseudo">Pseudo : </label>
            <input type="text" name="pseudo" id="pseudo" required/>
            <label for="email">E-mail : </label>
            <input type="email" name="email" id="email" required/>
            <label for="pwd">Mot de passe : </label>
            <input type="password" name="pwd" id="pwd" required/>
          </article>
          <div class="buttons">
            <input
              class="submit"
              type="submit"
              name="submit"
              value="S'enregistrer"
              spellcheck="false"
              aria-label="s'enregistrer"
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
    @extend %blocprofilregister;

    .wrapper--left {
      min-width: 390px;
      form {
        @media screen and (min-width: 580px) {
          width: 95%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 770px) {
          width: 90%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 1024px) {
          min-width: 40%;
          min-width: 390px;
        }

        .section--login {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
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

            .article--login {
              margin-top: 2rem;
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
                background: $color-greenlight;
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
            gap: 1.5rem;

            input {
              @extend %inputformbutton;
            }
          }
        }
      }
    }

    .wrapper--right {
      min-width: 390px;
      form {
        @media screen and (min-width: 580px) {
          width: 95%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 770px) {
          width: 90%;
          min-width: 390px;
          margin: auto;
        }
        @media screen and (min-width: 1024px) {
          min-width: 40%;
          min-width: 390px;
        }
        .section--register {
          @extend %glassmorphism;
          @extend %paddingprofilregister;
          margin-top: 2rem;
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

            .article--register {
              margin-top: 2rem;
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
                background: $color-greenlight;
                border: 1px solid white;
                border-radius: 5px;
                max-width: 285px;
              }
            }
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2rem;
            gap: 1.5rem;

            input {
              @extend %inputformbutton;
            }
          }
        }
      }
    }
  }
</style>
