<footer>
  <a href="/"> <button id="button__contact">Nous contacter</button></a>
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
    color: $color-black;
    font-family: Tahoma;
    font-size: 2rem;
    @extend %glassmorphism;
    border-radius: 0;
    display: flex;
    flex-direction: column;
    background-color: $color-white;
    padding: 6rem 3rem;
    row-gap: 6rem;
    a {
      display: flex;
      place-content: center;
      text-decoration: none;
      position: relative;
      color: $color-black;
       #button__contact {     
        cursor: pointer;
        width: 100%;
        padding: 2rem;
        background: $color-greenlight;
        border: 1px solid white;
        border-radius: 5px;
        font-size: 1.6rem;
        font-weight: bold;
        max-width: 310px;
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
          color: $color-black;
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
        justify-content: left;
      }
      @media screen and (min-width: 770px) {
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
        color: $color-black;
        &:after {
          content: "";
          position: absolute;
          left: 0;
          bottom: -5px;
          width: 100%;
          height: 2px;
          background-color: $color-greenlight;
          transform: scaleX(0); /* Masque le soulignement au départ */
          transition: transform 0.2s ease-in-out; /* Transition fluide */
          transform-origin: left; /* Modifie l'orientation du soulignement ici gauche à droite */
        }
        &:hover:after {
          transform: scaleX(1); /* Affiche le soulignement au survol */
        }
      }
    }
  }
</style>
