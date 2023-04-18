<script>
    import { onMount } from "svelte";
    import { checkAccess } from "./CheckAccess.svelte";
  import PageProfilAuthors from "../lib/PageProfilAuthors.svelte";
  import ErrorPage from "../lib/ErrorPage.svelte";
  
    let userId;
    onMount(async () => {
      // Récupérez l'identifiant de l'utilisateur connecté depuis Directus
      userId = await fetchUserIdFromDirectus();
    });
  
    const hasAccess = checkAccess("/profil-auteur", userId);
    const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;
    
    async function fetchUserIdFromDirectus() {
      // Récupérez l'identifiant de l'utilisateur connecté depuis Directus
      // Vous devez adapter cette fonction en fonction de la manière dont vous gérez l'authentification dans votre projet
      const response = await fetch(`${API_BASE_URL}/users/me`);
      const data = await response.json();
  
      return data.id;
    }
  </script>
  
  {#if hasAccess}
    <PageProfilAuthors/>
  {:else}
    <p><ErrorPage/></p>
  {/if}