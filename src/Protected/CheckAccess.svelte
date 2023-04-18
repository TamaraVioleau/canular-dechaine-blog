<script context="module">
export const allowedAccess = {
  "/profil-membre": ["e2a5bde2-09ab-44e4-8669-c9dc34c157e5", "213b3c24-fb05-446d-ab79-fd05adbbd6e2"],
  "/profil-auteur": ["645cbe7e-cdf9-409c-bc58-863ce065dfbb", "e2a5bde2-09ab-44e4-8669-c9dc34c157e5"],
  "/modification/:article_id": ["645cbe7e-cdf9-409c-bc58-863ce065dfbb", "e2a5bde2-09ab-44e4-8669-c9dc34c157e5"],
};

export const checkAccess = (route, userId) => {
  const allowedUsers = allowedAccess[route];

  if (!allowedUsers) {
    return true; // La page n'a pas de restriction d'accès
  }

  return allowedUsers.includes(userId);
};

</script>