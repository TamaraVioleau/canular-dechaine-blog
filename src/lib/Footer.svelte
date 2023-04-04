<footer>
  <button id="button__contact"><a href="/">Nous contacter</a></button>
  <div class="social">
    <button><a href=""><i class="fa-brands fa-facebook" /></a></button>
    <button><a href=""><i class="fa-brands fa-twitter" /></a></button>
    <button><a href=""><i class="fa-brands fa-instagram" /></a></button>
  </div>
  <ul>
    <li><a href="">Mentions légales</a></li>
    <li><a href="">Politique de confidentialité</a></li>
    <li><a href="">A propos</a></li>
  </ul>
</footer>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  footer {
    color: #312140;
    font-family: Tahoma;
    font-size: 2rem;
    @extend %glassmorphism;
    border-radius: 0;
    display: flex;
    flex-direction: column;
    background-color: #f8f8f8;
    padding: 3rem;
    gap: 3rem;
    #button__contact {
      display: flex;
      align-self: center;
      width: 100%;
      place-content: center;
      padding: 2rem;
      background: rgb(136 217 143 / 23%);
      border: 1px solid white;
      border-radius: 5px;
      font-size: 1.6rem;
      font-weight: bold;
      max-width: 310px;
      a {
        text-decoration: none;
        position: relative;
        color: #312140;
      }
    }

    .social {
      display: flex;
      gap: 4rem;
      justify-content: center;
      button {
        background-color: transparent;
        border: none;
        a {
          font-size: 5rem;
          text-decoration: none;
          position: relative;
          color: #312140;
          i {
          }
        }
      }
    }

    ul {
      @media screen and (min-width: 580px) {
        display: flex;
        flex-wrap: wrap;
       column-gap: 10rem;
      }
      @media screen and (min-width: 580px) {
justify-content: center;
      }
      li:not(:last-child) {
        padding-bottom: 1.8rem;
      }
            li:not(:last-child) {
        padding-bottom: 1.8rem;
      }
      li:last-child {
        padding-top: 0;
      }
      a {
        text-decoration: none;
        position: relative;
        color: #312140;
      }
    }
  }
</style>
