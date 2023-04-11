<script>
  import { link } from "svelte-spa-router";
</script>

<footer>
  <a
    id="button__contact"
    use:link
    href="/"
    role="button"
    aria-label="Aller à la page contact">Nous contacter</a
  >
  <div class="social">
    <a href="/" aria-label="Facebook"><i class="fa-brands fa-facebook" alt="Facebook" /></a>
    <a href="/" aria-label="Twitter"><i class="fa-brands fa-twitter" alt="Twitter" /></a>
    <a href="/" aria-label="Instagram"><i class="fa-brands fa-instagram" alt="Instagram" /></a>
  </div>
  <ul>
    <li><a href="/" aria-label="Aller aux mentions légales">Mentions légales</a></li>
    <li><a href="/" aria-label="Aller à la politique de confidentialité">Politique de confidentialité</a></li>
    <li><a href="/" aria-label="Aller à la page à propos">A propos</a></li>
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
    align-items: center;
    flex-direction: column;
    background-color: $color-white;
    padding: 6rem 3rem;
    row-gap: 6rem;

    #button__contact {
      @extend %button;
      max-width: 50%;
    }
    #button__contact:hover {
      background-color: $color-greenlight;
    } 

    .social {
      display: flex;
      gap: 3rem;
      justify-content: center;
      font-size: 5rem;

      a {
        display: flex;
        height: 75px;
        width: 75px;
        margin: 0 15px;
        border-radius: 8px;
        align-items: center;
        justify-content: center;
        text-decoration: none;      
        color: $color-black;
        i {
          transition: transform 0.5s;
          a:hover {
            transform: scale(0.9);
          }
        }
      }
      a:hover .fa-facebook {
        transform: translateY(2px);
        transition: transform 0.2s ease-in-out;
        color: #3b5998;
      }
      a:hover .fa-twitter {
        transform: translateY(2px);
        transition: transform 0.2s ease-in-out;
        color: #00acee;
      }
      a:hover .fa-instagram {
        transform: translateY(2px);
        transition: transform 0.2s ease-in-out;
        color: #f14843;
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
@extend %a-after;        }
        &:hover:after {
@extend %ahoverafter;
        }
      }
    }
  }
</style>
