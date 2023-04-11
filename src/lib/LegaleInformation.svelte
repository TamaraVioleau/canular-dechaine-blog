<script>


</script>
<div class="wrapper">
<main >
  <h2>Mentions légales , Cookies etc</h2>
  <p id="mention-legale" aria-label="Texte des mentions legales">
    Bonjour ! Voici un exemple de texte que vous pouvez utiliser pour la page
    mention légale de votre site internet : Mentions légales Présentation du
    site : Le présent site est la propriété de [nom de l'entreprise], [forme
    juridique de l'entreprise] au capital de [montant du capital social] euros,
    immatriculée au Registre du Commerce et des Sociétés de [ville
    d'immatriculation] sous le numéro [numéro d'immatriculation], dont le siège
    social est situé à [adresse du siège social]. Directeur de la publication :
    [nom du directeur de la publication]. Hébergeur du site : [nom et adresse de
    l'hébergeur du site]. Propriété intellectuelle : Le présent site et
    l'ensemble de son contenu, y compris textes, images, vidéos, logos, icônes,
    sont la propriété exclusive de [nom de l'entreprise] ou de tiers ayant
    autorisé [nom de l'entreprise] à les utiliser. Toute reproduction,
    représentation, modification, publication, transmission, dénaturation,
    totale ou partielle du site ou de son contenu, par quelque procédé que ce
    soit, et sur quelque support que ce soit est interdite. Données personnelles
    : [Indiquez les informations relatives à la collecte et au traitement des
    données personnelles de vos utilisateurs]. Responsabilité : [Indiquez les
    informations relatives à la responsabilité de votre entreprise et les
    conditions d'utilisation de votre site]. Liens hypertextes : [Indiquez les
    informations relatives aux liens hypertextes présents sur votre site].
    Cookies : [Indiquez les informations relatives à l'utilisation des cookies
    sur votre site]. Droit applicable et juridiction compétente : Les présentes
    mentions légales sont soumises au droit français. Tout litige relatif à
    l'interprétation ou à l'exécution des présentes mentions légales sera de la
    compétence exclusive des tribunaux français.
  </p>
</main>
</div>

<style lang="scss">
   @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  .wrapper{
       
       @extend %glassmorphism;
       padding: 3rem;
       margin: 2rem;
    }
    
  main {
    font-family: $police;
    background-color: $color-white;
    padding: 3rem;
    color: $color-black;
    display: flex;
    justify-content: center;
    flex-direction: column;
    
  
    h2 {
     text-align: center;
     padding: 3rem;
     font-weight: bold;
    }
    P{
        line-height: 1.5;
    }
    

      

      
  }
</style>
