<script>
  //SCRIPT COMPTEUR DE MOTS
  let myMaxLength = 500;
   // Initialiser le compteur de caractères à 0
  let characterCount = 0;
  // Initialiser les caractères restants avec la longueur maximale autorisée
  let charactersRemaining = myMaxLength;
  // Fonction pour gérer l'événement d'entrée (input) sur le textarea
  const handleInput = (e) => {
    // Mettre à jour le nombre de caractères en fonction de la longueur du texte dans le textarea
    characterCount = e.target.value.length;
    // Calculer les caractères restants en soustrayant le nombre de caractères actuels de la longueur maximale autorisée
    charactersRemaining = myMaxLength - characterCount;
  };

  //SCRIPT PREVIEW TEXTAREA
  let text = "";
  function updatePreview() {
    const preview = document.getElementById("preview");
    preview.innerHTML = text;
  }
</script>

<main>
  <article class="article">
    <img src="https://picsum.photos/200" alt="foto" />
    <h2>TITRE ARTICLE</h2>
    <p id="preview" aria-label="Texte de l'article">
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ratione quasi
      aliquid magnam aspernatur, porro iure in incidunt magni nulla? Tempora
      doloremque molestiae magnam nisi ex dolores delectus atque enim et. Neque
      ad impedit porro beatae blanditiis ab saepe reiciendis alias dignissimos
      esse deserunt quasi iure repellendus molestias animi distinctio fuga
      asperiores iusto, magnam, id, dicta voluptas! Delectus voluptates tempora
      quibusdam. Non quaerat omnis magnam obcaecati voluptatum ut recusandae
      consequuntur nemo ad. Pariatur quas nisi quod optio est cupiditate
      praesentium distinctio similique nemo impedit! Atque ea consequuntur eos
      id ipsa fugit. Nostrum perspiciatis sit similique cum placeat doloremque
      quod dolores voluptas harum tenetur, id nihil adipisci suscipit
      temporibus, quidem aliquam voluptates. dignissimos esse deserunt quasi
      iure repellendus molestias animi distinctio fuga asperiores iusto, magnam,
      id, dicta voluptas! Delectus voluptates tempora quibusdam. Non quaerat
      omnis magnam obcaecati voluptatum ut recusandae consequuntur nemo ad.
      Pariatur quas nisi quod optio est cupiditate praesentium distinctio
      similique nemo impedit! Atque ea consequuntur eos id ipsa fugit. Nostrum
      perspiciatis sit similique cum placeat doloremque quod dolores voluptas
      harum tenetur, id nihil adipisci suscipit temporibus, quidem aliquam
      voluptates. optio est cupiditate praesentium distinctio similique nemo
      impedit! Atque ea consequuntur eos id ipsa fugit. Nostrum perspiciatis sit
      similique cum placeat doloremque quod dolores voluptas harum tenetur, id
      nihil adipisci suscipit temporibus, quidem aliquam voluptates. dignissimos
      esse deserunt quasi iure repellendus molestias animi distinctio fuga
      asperiores iusto, magnam, id, dicta voluptas! Delectus voluptates tempora
      quibusdam. Non quaerat omnis magnam obcaecati voluptatum ut recusandae
      consequuntur nemo ad. Pariatur quas nisi quod optio est cupiditate
      praesentium distinctio similique nemo impedit! Atque ea consequuntur eos
      id ipsa fugit. Nostrum perspiciatis sit similique cum placeat doloremque
      quod dolores voluptas harum tenetur, id nihil adipisci suscipit
      temporibus, quidem aliquam voluptates.
    </p>
  </article>

  <div class="write">
    <label for="textarea" />
    <textarea
      name="textarea"
      id="textarea"
      maxlength={myMaxLength}
      on:input={[handleInput, updatePreview]}
      bind:value={text}      
      spellcheck="true"
      placeholder="Ecrire ici pour modifier l'article"
    />
    <p class="counter">
      Nombre de caractères restant : <span id="characterCounter"
        >{charactersRemaining}</span
      >/<span id="maximum">{myMaxLength}</span>
    </p>
    <div class="buttons">
      <input
        class="submit"
        type="submit"
        name="submit"
        value="Envoyer"
        spellcheck="false"
        aria-label="Envoyer article"
      />
    </div>
  </div>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    padding: 3rem;
    font-family: $police;

    article {
      display: block;
      padding: 00.625rem;
      @extend %glassmorphism;

      img {
        min-width: 100%;
        max-height: 160px;
        object-fit: cover;
        @extend %glassmorphism;
      }

      h2 {
        text-align: center;
        padding: 2rem;

        font-weight: bolder;
      }
      #preview {
        font-family: $police;
        padding: 2rem;
        line-height: 2rem;
      }
    }
    .write {
      display: block;
      @extend %glassmorphism;
      width: 100%;
      margin-top: 30px;
    }

    #textarea {
      display: block;
      height: 40rem;
      width: 95%;
      margin: 2rem auto;
      resize: vertical;
      font-size: 1.6rem;
      min-height: 100px;
      border-radius: 5px;
      border: 1px solid #ccc;
      padding: 1rem;

      textarea::-webkit-resizer,
      textarea::-moz-resizer,
      textarea::-o-resizer,
      textarea::-ms-resizer {
        height: 100px; /* masque l'icon de redimensionnement pour les différents navigateurs */
      }
    }

    .counter {
      position: relative;
      left: 5rem;
      font-size: 1.2rem;
    }
    .buttons {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 1rem;
    }

    .submit {
      background-color: $color-greenlight;
      color: rgb(19, 18, 18);
      padding: 1rem 2rem;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  }
</style>
