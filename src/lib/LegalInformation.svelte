<script>
   import { link } from "svelte-spa-router";
</script>

<main>
  <article>
    <h3>Mentions légales</h3>
    <p class="paragraph" aria-label="Introduction mentions légales">
      Le présent site est édité par <strong>Canular déchainé</strong>, dont le
      siège social est situé en <strong>France</strong>. Représentants légaux et
      directeurs de la publication :
      <strong>Sébastien, Frédéric et Tamara.</strong>
    </p>

    <p class="paragraph" aria-label="Hébergement site">
      Hébergement : Le site est hébergé par <strong>[Nom de l'hébergeur]</strong
      >. Le site est accessible à l'adresse suivante : www.[NomDeDomaine].com
    </p>

    <h4>Propriété intellectuelle</h4>
    <p class="paragraph" aria-label="propriété intellectuelle">
      L'ensemble des éléments composant ce site, y compris les textes, images,
      vidéos, illustrations et graphismes, sont protégés par les lois en vigueur
      sur la propriété intellectuelle et sont la propriété exclusive de <strong
        >Canular déchainé</strong
      >, sauf mention contraire.
    </p>
    <p class="paragraph" aria-label="reproduction interdite">
      Toute reproduction, distribution, modification, adaptation, retransmission
      ou publication, même partielle, de ces éléments est strictement interdite
      sans l'accord express par écrit de <strong>Canular déchainé</strong>.
    </p>

    <h4>Responsabilité</h4>
    <p class="paragraph" aria-label="Informations de responsabilité">
      Les informations publiées sur ce site sont fournies à titre humoristique
      et satirique, et ne sauraient engager la responsabilité de <strong
        >Canular déchainé</strong
      > ou de ses collaborateurs. Le site contient des fausses informations et ne
      doit pas être pris au sérieux.
    </p>
    <p class="paragraph" aria-label="Hébergement site">
      <strong>Canular déchainé</strong> se réserve le droit de modifier ou de supprimer,
      sans préavis, tout contenu du site qui ne respecterait pas les normes éthiques
      du blog ou qui enfreindrait la législation en vigueur.
    </p>

    <h4>Protection des données personnelles</h4>
    <p class="paragraph" aria-label="RGPD">
      Conformément à la loi Informatique et Libertés du 6 janvier 1978 et au
      Règlement Général sur la Protection des Données (RGPD) en vigueur depuis
      le 25 mai 2018, les utilisateurs du site disposent d'un droit d'accès, de
      rectification, de suppression et d'opposition à l'utilisation de leurs
      données personnelles. Pour exercer ce droit, il suffit d'envoyer un
      courriel à <strong>Canular déchainé</strong>.
    </p>

    <p class="paragraph" aria-label="données personnelles">
      Les données personnelles collectées sur ce site sont uniquement destinées
      à l'usage de <strong>Canular déchainé</strong> et ne seront en aucun cas transmises
      ou vendues à des tiers sans l'accord préalable des utilisateurs concernés.
    </p>

    <h4>Liens hypertextes</h4>
    <p class="paragraph" aria-label="données personnelles">
      Les liens hypertextes présents sur ce site peuvent renvoyer vers d'autres
      sites ou ressources externes. <strong>Canular déchainé</strong> ne peut être
      tenue pour responsable du contenu de ces sites ou ressources externes, et décline
      toute responsabilité quant à leur accessibilité et à leur disponibilité.
    </p>

    <h4>Modification des mentions légales</h4>
    <p class="paragraph" aria-label="données personnelles">
      <strong>Canular déchainé</strong> se réserve le droit de modifier les présentes
      mentions légales à tout moment et sans préavis. Les utilisateurs sont donc
      invités à les consulter régulièrement.
    </p>

    <h4>Loi applicable et attribution de juridiction</h4>
    <p class="paragraph" aria-label="données personnelles">
      Les présentes mentions légales sont soumises au droit français. En cas de
      litige, les tribunaux compétents seront ceux du ressort de la Cour
      d'appel, sauf dispositions contraires d'ordre public.
    </p>
    <footer>
      <aside aria-label="Date de publication et auteur">
        <time datetime="24/04/2023" aria-label="Date de publication">
          {new Date().toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric",
          })}
        </time> <span aria-hidden="true"> || </span>

        <cite title="Canular Déchainé" aria-label="Auteur">Canular Déchainé</cite>
      </aside>
    </footer>
  </article>
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
    @media screen and (min-width: 580px) {
      padding: 3rem;
    }
    display: flex;
    justify-content: center;
    flex-direction: column;
    article {
      display: block;
      padding: 2rem;
      margin: 3rem;
      @extend %glassmorphism;
      @media screen and (min-width: 770px) {
        padding-inline: 17vw;
        padding-top: 5rem;
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
      h3 {
        @extend %h3;
      }
      h4 {
        @extend %h4;
      }
      .paragraph {
        font-family: $police;
        padding: 2rem;
        @extend %p;
      }

      footer {
        display: flex;
        flex-wrap: wrap;
        padding: 1rem;
        margin: 1rem;
        justify-content: space-between;
        aside {
          display: flex;
          margin-right: 1rem;
          font-size: 1.3rem;
          gap: 1rem;
          time {
            font-style: italic;
          }
          cite {
            font-style: normal;
            font-weight: bold;
          }
        }
      }
    }
  }
  strong {
    font-weight: bolder;
  }
</style>
