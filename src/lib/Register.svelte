<script>
</script>

<main>
  <!-- dans action mettre le nom de la page (ex: /profil)  -->
  <form action="" method="post" id="connexion" name="connexion">
    <wrapper class="wrapper__left">
      <section class="section__login" aria-labelledby="login">
        <h1 id="login">Se connecter</h1>

        <article class="article__login" aria-label="formulaire de connexion">
          <label for="pseudo">Pseudo : </label>
          <input type="text" name="pseudo" id="pseudo" />
          <label for="pwd">Mot de passe : </label>
          <input type="password" name="pwd" id="pwd" />
        </article>
      </section>
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
    </wrapper>
  </form>

  <form action="" method="post" id="inscription" name="inscription">
    <wrapper class="wrapper__right">
      <section class="section__register" aria-labelledby="register">
        <h1 id="statistiques">S'enregistrer :</h1>

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
      </section>
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
    </wrapper>
  </form>
</main>

<!--
<main>
  <section class="login">
    <h2>Se connecter</h2>

    <form class="login-form">
      <label for="username">Pseudo :</label>
      <input type="text" id="username" name="username" required />

      <label for="password">Mot de passe :</label>
      <input type="password" id="password" name="password" required />

      <button type="submit">Se connecter</button>
    </form>
  </section>

  <section class="register">
    <h2>S'inscrire</h2>

    <form class="register-form">
      <label for="reg-username">Pseudo :</label>
      <input type="text" id="reg-username" name="reg-username" required />

      <label for="email">E-mail :</label>
      <input type="email" id="email" name="email" required />

      <label for="reg-password">Mot de passe :</label>
      <input type="password" id="reg-password" name="reg-password" required />

      <div class="form-group checkbox-group">
        <input type="checkbox" id="accept-terms" name="accept-terms" required />
        <label for="accept-terms"
          >J'ai lu et j'accepte les présentes conditions d'utilisation.</label
        >
      </div>

      <button type="submit">S'inscrire</button>
    </form>
  </section>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-evenly;
    align-content: center;
    color: #312140;
    font-family: Tahoma;
    background-color: #f8f8f8;
    min-height: 100vh;

    @media screen and (min-width: 580px) {
        width: 95%;
        margin: auto;
      }
      @media screen and (min-width: 770px) {
        width: 90%;
        margin: auto;
      }

    section {
      @extend %glassmorphism;
     width: 70vh;
     height: 70vh;
      margin-top: 10rem;
      gap: 10rem;
      
      


      h2 {
        text-align: center;
        font-weight: bold;
        font-size: 2rem;
        margin: 5rem;
      }
    }

    form {
      display: flex;
      flex-direction: column;

      input {
        padding: 5px;
        background: rgba(136, 217, 143, 0.23);
        max-width: 70%;
        font-size: 1rem;
        line-height: 1.5;
        border: none;
        max-width: 285px;
      }
    }

    .checkbox-group {
      display: flex;
    }

    button {
      background: rgba(136, 217, 143, 0.23);
      border: 1px solid black;
      border-radius: 5px;
      font-size: 1.5rem;
      width: 30vh;
      
    }

    .login-form {
      margin-bottom: 20px;

      @media (min-width: 768px) {
        margin-right: 10px;
        margin-bottom: 0;
      }
    }

    @media (min-width: 768px) {
      flex-direction: row;

      .register-form {
        margin-left: 10px;
      }
    }
  }
</style>
-->
<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";
  main {
    
    color: #312140;
    font-family: Tahoma;
    background-color: #f8f8f8;
    padding: 2.3rem;
    // padding: clamp(2.3rem, 5.5vw, 23rem);
    min-height: 100vh;
    @media screen and (min-width: 580px) {
      padding: 3.5rem;
    }
    @media screen and (min-width: 770px) {
      padding: 5rem 10rem;
    }
    @media screen and (min-width: 1024px) {
      padding: 5rem 0rem;
      display: flex;
        justify-content: center;
        gap: 10rem;
        margin: auto;
        align-items: flex-start;
        min-height: 100vh;
        

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
        min-height: 100vh;
      }
      @media screen and (min-width: 1200px) {
      }
      .section__login {
        @extend %glassmorphism;
        padding: 1.5rem;
        // padding: clamp(1.5rem, 5.5vw, 15rem);
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
        @extend %glassmorphism;
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
      .section__register {
        @extend %glassmorphism;
        padding: 1.5rem;
        margin-top: 2.3rem;
        @media screen and (min-width: 580px) {
          padding: 1.5rem 3.5rem;
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
        @extend %glassmorphism;
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
</style>
