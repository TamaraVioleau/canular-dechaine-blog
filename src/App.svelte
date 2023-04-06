<script>

  import Router from "svelte-spa-router";

  import Homepage from "./lib/Homepage.svelte";
  import ErrorPage from "./lib/ErrorPage.svelte";
  import Footer from "./lib/Footer.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import PageArticle from "./lib/PageArticle.svelte";
  import Navbar from "./lib/Navbar.svelte";
  import CommentsArticlePage from "./components/CommentsArticlePage.svelte";

  

</script>
<Navbar/>

<Router {routes}/>

<Homepage />
<PageArticle/>
<ModifiedArticle/>
<PageArticles/>
<SearchPage/>

<Register/>
<PageProfilAuthors/>
<PageProfilMembers/>

<Footer/>
<style lang="scss">
</style>
