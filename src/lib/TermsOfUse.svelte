<script>
  import { link } from "svelte-spa-router";
</script>

<main>
  <article>
    <h3>Conditions d'utilisations</h3>

    <h4>1. Introduction</h4>
    <p class="paragraph" aria-label="Introduction">
      Les présentes conditions d'utilisation (ci-après, les « Conditions »)
      régissent l'accès et l'utilisation du site web Canular Déchainé (ci-après,
      le « Site ») par les utilisateurs (ci-après, les « Utilisateurs »). En
      accédant et en utilisant le Site, les Utilisateurs acceptent les présentes
      Conditions et s'engagent à les respecter.
    </p>

    <h4>2. Contenu du Site</h4>
    <p class="paragraph" aria-label="Contenu du Site">
      Le Site est destiné à fournir des informations parodiques et humoristiques
      sur divers sujets tels que la politique, les arts, la cuisine, le sport,
      la société, les célébrités, les sciences, le numérique et l'horoscope. Les
      articles publiés sur le Site sont des œuvres de fiction et ne doivent pas
      être pris au sérieux. Les Utilisateurs sont encouragés à vérifier la
      véracité des informations avec d'autres sources.
    </p>

    <h4>3. Propriété intellectuelle</h4>
    <p class="paragraph" aria-label="Propriété intellectuelle">
      Les contenus du Site, y compris les articles, les images, les vidéos et
      les graphiques, sont protégés par les lois sur les droits d'auteur et les
      marques déposées. Toute utilisation non autorisée, y compris la
      reproduction, la distribution, la modification ou la publication, sans
      l'autorisation écrite préalable de Canular Déchainé est strictement
      interdite.
    </p>

    <h4>4. Comportement des utilisateurs</h4>
    <p class="paragraph" aria-label="Comportement des utilisateurs">
      Les Utilisateurs s'engagent à utiliser le Site de manière responsable et
      respectueuse. Ils ne doivent pas publier, partager ou diffuser des
      contenus illégaux, offensants, diffamatoires, racistes, sexistes,
      discriminatoires, obscènes ou incitant à la haine ou à la violence. Les
      Utilisateurs sont également responsables de respecter les droits d'autrui,
      notamment en matière de propriété intellectuelle.
    </p>

    <h4>5. Responsabilité</h4>
    <p class="paragraph" aria-label="Responsabilité">
      Canular Déchainé ne peut être tenu responsable des dommages directs ou
      indirects, y compris les dommages matériels, les pertes de données ou de
      profits, ou les troubles à la vie privée, résultant de l'utilisation ou de
      l'impossibilité d'utiliser le Site.
    </p>

    <h4>6. Liens vers d'autres sites</h4>
    <p class="paragraph" aria-label="Liens vers d'autres sites">
      Le Site peut contenir des liens vers des sites web tiers. Canular Déchainé
      n'est pas responsable du contenu, de la disponibilité ou de la politique
      de confidentialité de ces sites. Les Utilisateurs sont encouragés à
      consulter les conditions d'utilisation et les politiques de
      confidentialité de ces sites avant de les utiliser.
    </p>

    <h4>7. Modification des Conditions</h4>
    <p class="paragraph" aria-label="modification des conditions">
      Canular Déchainé se réserve le droit de modifier les présentes Conditions
      à tout moment et sans préavis. Les Utilisateurs sont responsables de
      vérifier régulièrement les Conditions pour prendre connaissance des
      éventuelles modifications. L'utilisation continue du Site après la
      publication de modifications des Conditions constitue une acceptation de
      ces modifications.
    </p>

    <h4>8. Loi applicable et juridiction</h4>
    <p class="paragraph" aria-label="Loi applicable et juridiction">
        Les présentes Conditions sont régies par le droit français. Tout litige découlant de l'utilisation du Site sera soumis à la compétence exclusive des tribunaux français.
    </p>

    <h4>9. Contact</h4>
    <p class="paragraph" aria-label="Contact">Si vous avez des questions concernant les présentes Conditions ou votre utilisation
    du Site, n'hésitez pas à nous contacter à l'adresse e-mail suivante : [adresse
    e-mail de contact]. Date de dernière mise à jour : [date de la dernière mise
    à jour des conditions d'utilisation] </p>

    <footer>
      <aside aria-label="Date de publication et auteur">
        <time datetime="24/04/2023" aria-label="Date de publication">
          {new Date().toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric",
          })}
        </time> <span aria-hidden="true"> || </span>

        <cite title="Canular Déchainé" aria-label="Auteur"
          >Canular Déchainé</cite
        >
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
