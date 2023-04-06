<script>

  import Router from "svelte-spa-router";
  import ErrorPage from "./lib/ErrorPage.svelte";
  import Footer from "./lib/Footer.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import Navbar from "./lib/Navbar.svelte";

  import Homepage from "./lib/Homepage.svelte";
  import PageArticle from "./lib/PageArticle.svelte";

  import CommentsArticlePage from "./components/CommentsArticlePage.svelte";
  import UpDown from "./components/UpDown.svelte";



  const routes = {
    "/": Homepage,
    "/connexion": Register,
    "/articles": PageArticles,
    "/article": PageArticle,
  }
</script>

<Navbar/>

<Router {routes}/>
<Footer/>

<!--
  <Navbar />
<Homepage />
<Footer />

<PageArticle/>
<UpDown/>

<SearchPage/>
<PageProfilAuthors/>
<PageProfilMembers/>
<SearchPage/>
<Register/>
<PageArticles/>
<ModifiedArticle/>
<Footer/>

 -->


<style lang="scss">
</style>
