<script>
  import Router from "svelte-spa-router";
  const onRouteLoaded = () => {
    window.scrollTo(0, 0);
  };

 
  import Navbar from "./lib/Navbar.svelte";
  import Homepage from "./lib/Homepage.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import PageArticle from "./lib/PageArticle.svelte";
  import ErrorPage from "./lib/ErrorPage.svelte";
  import Footer from "./lib/Footer.svelte";
  import CommentsArticlePage from "./components/CommentsArticlePage.svelte";
  import UpDown from "./components/UpDown.svelte";


  import Contact from "./lib/Contact.svelte";
  import LegalInformation from "./lib/LegalInformation.svelte";
  import About from "./lib/About.svelte";
  import TermsOfUse from "./lib/TermsOfUse.svelte";



  const routes = {
    "/": Homepage,
    "/connexion": Register,
    "/articles/:id": PageArticles,
    "/article/:article_id": PageArticle,
    "/modification/:article_id": ModifiedArticle,
    "/profil-membre": PageProfilMembers,
    "/profil-auteur": PageProfilAuthors,
    "/contact": Contact,
    "/mentions-legales": LegalInformation,
    "/a-propos": About,
    "/conditions-utilisations":TermsOfUse,


  };
</script>

<Navbar />
<!-- onRouteLoaded permet le reload de la page et qui renvoie vers le haut -->
<Router {routes} on:routeLoaded={onRouteLoaded} />
<UpDown/>
<Footer />

<!-- 
<ModifiedArticle/>
<SearchPage/>
<Register />
<PageProfilMembers />

<PageArticle/>
-->
