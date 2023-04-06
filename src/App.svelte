<script>
  import Router from "svelte-spa-router";

  import Footer from "./lib/Footer.svelte";
  import Homepage from "./lib/Homepage.svelte";
  import ErrorPage from "./lib/ErrorPage.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import Navbar from "./lib/Navbar.svelte";


  const routes = {
    "/": Homepage,
    "/login": Register,
    "/articles": PageArticles,
    
  }
</script>

<Navbar/>
<Router {routes}/>
<Footer/>

<!--
  <Navbar />
<Homepage />
<Footer />
<SearchPage/>
<PageProfilAuthors/>
<PageProfilMembers/>
<SearchPage/>
<Register/>
<PageArticles/>
<ErrorPage />
 -->

<style lang="scss">
</style>
