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

<div class="write">
  <label for="textarea" />
  <textarea
    name="textarea"
    id="textarea"
    maxlength={myMaxLength}
    on:input={(event) => {handleInput(event); updatePreview();}}
    bind:value={text}
    spellcheck="true"
    placeholder="Ecrire ici pour modifier l'article"
  />
  <p class="counter">
    Nombre de caractères restant : <span id="characterCounter"
      >{charactersRemaining}</span
    >/<span id="maximum">{myMaxLength}</span>
  </p>
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
</div>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";
  .write {
      display: flex;      
      justify-content: center;
      flex-direction: column;      
      align-self: center;
    @extend %glassmorphism;
    margin: 3rem;
    padding: 2rem;
    @media screen and (min-width: 1024px) {
      max-width: 910px;
      min-width: 910px;
    }
  }

  #textarea {
    display: block;
    height: 40rem;
    width: 95%;
    margin: 2rem auto;
    resize: vertical;
    min-height: 100px;
    border-radius: 5px;
    border: 1px solid #ccc;
    padding: 2rem;
    @extend %p;
  }

  .counter {
    position: relative;
    font-size: 1.2rem;
    display: flex;
    justify-content: center;
    padding-bottom: 2rem;
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
    }
    .submit:active {
      @extend %buttonactive;
    }
    .submit:hover {
      background-color: $color-greenlight;
    }
  }
</style>
