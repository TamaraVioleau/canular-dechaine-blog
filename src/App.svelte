<script>
 

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

  
 import Router from "svelte-spa-router";
  import LegaleInformation from "./lib/LegaleInformation.svelte";
  const routes = {
    "/": Homepage,
    "/connexion": Register,
    "/articles/:id": PageArticles,
    "/article": PageArticle,
  };
</script>


<LegaleInformation />
<!---<Router {routes} />
<PageArticle/>
<ModifiedArticle/>
<SearchPage/>
<Navbar />
  <Register />
<PageProfilAuthors />
<PageProfilMembers />
<Footer />

<!-- 



-->

<!--

 -->
