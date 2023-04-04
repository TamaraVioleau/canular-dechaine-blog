<footer>
  <button id="button__contact"><a href="/">Contact</a></button>
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
    display: flex;
    flex-direction: column;
    align-items: center;
    #button__contact {
    }

    .social {
      display: flex;
      gap: 1rem;
    }
  }
</style>
