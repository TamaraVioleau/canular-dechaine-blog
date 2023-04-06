<script>
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
</script>

<Navbar />
<Homepage />
<PageArticles/>
<PageProfilAuthors/>
<PageProfilMembers/>
<SearchPage/>
<Register/>
<ModifiedArticle/>
<Footer />

<!--
  
<ErrorPage/>
 -->

<style lang="scss">
</style>
