<footer>
  <button id="button__contact"
    ><a href="/">
      <input
        class="submit"
        type="submit"
        name="submit"
        value="Enregistrer"
        spellcheck="false"
        aria-label="Enregistrer les informations"
      /></a
    ></button
  >
  <div class="social">
    <button><a href=""><i class="fa-brands fa-facebook" /></a></button>
    <button><a href=""><i class="fa-brands fa-twitter" /></a></button>
    <button><a href=""><i class="fa-brands fa-instagram" /></a></button>
  </div>
  <ul>
    <li>Mentions légales</li>
    <li>Politique de confidentialité</li>
    <li>A propos</li>
  </ul>
</footer>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  footer {
    color: #312140;
    font-family: Tahoma;
    @extend %glassmorphism;
    border-radius: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #f8f8f8;
    padding: 3rem;
    gap: 3rem;
    #button__contact {
      margin-top: 2.3rem;
      display: flex;
      justify-content: center;
      background: none;
      border: none;
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

    .social {
      display: flex;
      gap: 1rem;

      button {
        background-color: none;
        border: none;
        a {
          font-size: 5rem;
          i {
          }
        }
      }
    }
  }
</style>
