<script>
</script>

<main>
  <div class="contact">
    <h2>Nous Contacter</h2>
  </div>
  <div class="information">
    <div class="information_name">
      <form>
        <label for="nom-prenom" aria-label="Saisir votre nom et prénom">Nom et prénom :</label>
        <input type="text" id="nom-prenom" name="nom-prenom" aria-label="Saisir votre nom et prénom" />
      </form>
    </div>
    <div class="information_mail">
      <form>
        <label for="email" aria-label="Saisir votre adresse e-mail">E-mail :</label>
        <input type="email" id="email" name="email" aria-label="Saisir votre adresse e-mail" />
      </form>
    </div>
  </div>

  <div class="destination">
    <div class="destination_title">
      <h3>A destination de :</h3>
    </div>
    <div class="destination_menu">
      <label for="select-service" aria-label="Sélectionner un service à contacter"></label>
      <select id="select-service" name="select-service" aria-label="Liste déroulante pour sélectionner un service à contacter">
        <option value="" selected disabled>Selectionner le service</option>
        <option value="auteur">Auteur</option>
        <option value="administrateur">Administrateur</option>
      </select>
    </div>
  </div>
  <div class="comment_content">
    <label for="champ-texte" aria-label="Saisir votre message">Message :</label>
    <textarea id="champ-texte" name="champ-texte" rows="12" cols="40" aria-label="Saisir votre message"></textarea>
    <div class="button">
      <button type="submit">Envoyer</button>
    </div>
  </div>
</main>


<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .information_name {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .information_mail {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  h2 {
    text-align: center;
    padding: 3rem;
    font-weight: bold;
    font-size: 3rem;
    font-family: tahoma;
  }
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  label {
    display: flex;

    padding: 1rem;
  }
  .destination {
    display: flex;
    flex-direction: column;
    text-align: center;
    width: 92%;
    height: 80%;
    @extend %glassmorphism;
  }

  .destination_menu {
    display: flex;
    flex-direction: column;
    padding: 1rem;
  }

  h3 {
    padding: 1.5rem;
    font-family: tahoma;
  }
  .information,
  .comment_content {
    @extend %glassmorphism;
    padding: 2rem;
    margin-bottom: 1rem;
    width: 92%;
    height: 80%;
    margin: 2rem;
  }

  .comment_content textarea {
    width: 100%;
  }
  .button {
    text-align: center;
    padding: 1rem;
  }
  .button button {
    padding: 1rem 2rem;
    background-color: $color-greendark;
    color: #fff;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
  }
  @media screen and (min-width: 770px) {
    form {
      flex-direction: row;
    }

    label {
      display: flex;
    }

    input[type="text"],
    input[type="email"] {
      display: flex;
    }
    .destination {
      display: flex;
      flex-direction: row;
    }
    .destination_menu {
      display: flex;
      flex-direction: row;
    }
  }
</style>
