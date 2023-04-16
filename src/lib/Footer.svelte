<script>
  import { link } from "svelte-spa-router";

  const links_social = [
    {
      text: "facebook",
      url: "https://www.facebook.com",
    },
    {
      text: "twitter",
      url: "https://twitter.com/",
    },
    {
      text: "instagram",
      url: "https://www.instagram.com/",
    },
  ];

  const links_admin = [
    {
      text: "Mentions légales",
      url: "/mentions-legales",
      label: "Aller aux mentions légales",
    },
    {
      text: "Conditions d'utilisations",
      url: "/conditions-utilisations",
      label: "Aller aux conditions d'utilisation",
    },
    {
      text: "A propos",
      url: "/a-propos",
      label: "Aller à la page à propos",
    },
  ];
</script>

<footer>
  <a
    id="button__contact"
    use:link
    href="/contact"
    role="button"
    aria-label="Aller à la page contact">Nous contacter</a
  >

  <div class="social">
    {#each links_social as social}
      <a href={social.url} aria-label={social.text}
        ><i class="fa-brands fa-{social.text}" alt={social.text} /></a
      >
    {/each}
  </div>
  <ul>
    {#each links_admin as admin}
      <li>
        <a use:link href={admin.url} aria-label={admin.label}>{admin.text}</a>
      </li>
    {/each}
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
          @extend %a-after;
        }
        &:hover:after {
          @extend %ahoverafter;
        }
      }
    }
  }
</style>
