<script>
      import { link } from "svelte-spa-router";
</script>

<main>
  <h2>Nous contacter</h2>
  <form action="/" method="post">
    <section class="informations">
      <div class="information-name">
        <label for="nom-prenom">Nom / Prénom</label>
        <input id="nom-prenom" type="text" name="nom-prenom" />
      </div>
      <div class="information-email">
        <label for="email-input">E-mail</label>
        <input id="email-input" type="email" name="email" />
      </div>

      <label for="contact">A destination de :</label>
      <select id="contact" name="contact">
        <option value="sélection du service" selected disabled
          >Selectionner le service</option
        >
        <option value="auteurs">Auteurs</option>
        <option value="administrateur">Administrateur</option>
      </select>
    </section>
    <section class="message">
      <label for="champ-texte" aria-label="Saisir votre message"
        >Votre message :</label
      >
      <textarea
        name="textarea"
        id="textarea"
        aria-labelledby="textarea-label"
        spellcheck="true"
        placeholder="Ici, écrivez votre message. Indiquez le lien de l'article pour lequel vous nous contacter si c'est le cas."
      />
      <button>
        <input
          class="submit"
          type="submit"
          name="submit"
          value="Envoyer"
          spellcheck="false"
          aria-label="Envoyer article"
        />
      </button>
    </section>
  </form>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    padding: 3rem;
    font-family: $police;
    background-color: $color-white;
    color: $color-black;
    display: flex;
    justify-content: center;
    flex-direction: column;
    @media screen and (min-width: 580px) {
      padding: 3rem;
    }

    h2 {
      @extend %h2;
      text-align: center;
    }
    form {
      display: flex;
      flex-direction: column;

      section {
        display: flex;
        flex-direction: column;
        padding: 2rem;
        margin: 3rem;
        @extend %glassmorphism;
        @media screen and (min-width: 770px) {
          padding-inline: 17vw;
          padding-block: 5rem;
        }
        @media screen and (min-width: 1024px) {
          padding-inline: 15vw;
          max-width: 910px;
          min-width: 910px;
          align-self: center;
        }
        @media screen and (min-width: 1440px) {
          padding-inline: 10vw;
        }
        .information-name,
        .information-email {
          display: flex;
          flex-direction: column;
        }

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
        select {
          width: 100%;
          padding: 1rem;
          font-size: 1.5rem;
          max-width: 285px;
        }

        #textarea {
          height: 40rem;
          resize: vertical;
          min-height: 100px;
          border-radius: 5px;
          border: 1px solid #ccc;
          padding: 2rem;
          @extend %p;
        }
        button {
          display: flex;
          justify-content: center;
          background: transparent;
          border: none;
          max-width: 100%;
          .submit {
            @extend %button;
            min-width: 220px;
            box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
          }
          .submit:active {
            @extend %buttonactive;
          }
          .submit:hover {
            background-color: $color-greenlight;
          }
        }
      }
    }
  }
</style>
