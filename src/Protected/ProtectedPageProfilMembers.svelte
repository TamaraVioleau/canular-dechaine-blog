<script>
  import { onMount } from "svelte";
  import ErrorPage from "../lib/ErrorPage.svelte";
  import PageProfilMembers from "../lib/PageProfilMembers.svelte";


  let hasAccess = false;

onMount(async () => {
  const role = await getUserRole();
  if (role === "213b3c24-fb05-446d-ab79-fd05adbbd6e2" || role === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5") {
    hasAccess = true;
  }
});

// Renvoie le rôle de l'utilisateur actuellement connecté
const getCurrentUserRole = async () => {
  const token = window.localStorage.getItem("token");
  if (!token) {
    return null;
  }

  const response = await fetch(`${import.meta.env.VITE_URL_DIRECTUS}/users/me`, {
    headers: {
      Authorization: `Bearer ${token}`
    }
  });
  const json = await response.json();
  return json.data.role;
};

// Appelle l'API pour obtenir le rôle de l'utilisateur connecté
const getUserRole = async () => {
  const role = await getCurrentUserRole();
  if (role === "213b3c24-fb05-446d-ab79-fd05adbbd6e2" || role === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5") {
    return role;
  }
  return null;
};
</script>


{#if hasAccess}
<PageProfilMembers/>
{:else}
  <p><ErrorPage /></p>
{/if}