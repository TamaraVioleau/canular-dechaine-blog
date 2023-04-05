<script>
  let myMaxLength = 500;

  // Définir le seuil d'alerte pour informer l'utilisateur du nombre de caractères restants
  let myAlertThreshold = 95;

  // Initialiser le compteur de caractères à 0
  let characterCount = 0;

  // Initialiser les caractères restants avec la longueur maximale autorisée
  let charactersRemaining = myMaxLength;

  // Fonction pour gérer l'événement d'entrée (input) sur le textarea
  const handleInput = (e) => {
    // Mettre à jour le nombre de caractères en fonction de la longueur du texte dans le textarea
    characterCount = e.target.value.length;

    // Calculer les caractères restants en soustrayant le nombre de caractères actuels de la longueur maximale autorisée
    charactersRemaining = myMaxLength - characterCount;
  };
</script>

<main>
  <div class="wrap">
    <section class="picture">
      <img src="https://picsum.photos/200" alt="foto" />
    </section>
    <div class="article">
      <h2>TITRE ARTICLE</h2>
      <p aria-label="Texte de l'article">
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ratione quasi
        aliquid magnam aspernatur, porro iure in incidunt magni nulla? Tempora
        doloremque molestiae magnam nisi ex dolores delectus atque enim et.
        Neque ad impedit porro beatae blanditiis ab saepe reiciendis alias
        dignissimos esse deserunt quasi iure repellendus molestias animi
        distinctio fuga asperiores iusto, magnam, id, dicta voluptas! Delectus
        voluptates tempora quibusdam. Non quaerat omnis magnam obcaecati
        voluptatum ut recusandae consequuntur nemo ad. Pariatur quas nisi quod
        optio est cupiditate praesentium distinctio similique nemo impedit!
        Atque ea consequuntur eos id ipsa fugit. Nostrum perspiciatis sit
        similique cum placeat doloremque quod dolores voluptas harum tenetur, id
        nihil adipisci suscipit temporibus, quidem aliquam voluptates.
        dignissimos esse deserunt quasi iure repellendus molestias animi
        distinctio fuga asperiores iusto, magnam, id, dicta voluptas! Delectus
        voluptates tempora quibusdam. Non quaerat omnis magnam obcaecati
        voluptatum ut recusandae consequuntur nemo ad. Pariatur quas nisi quod
        optio est cupiditate praesentium distinctio similique nemo impedit!
        Atque ea consequuntur eos id ipsa fugit. Nostrum perspiciatis sit
        similique cum placeat doloremque quod dolores voluptas harum tenetur, id
        nihil adipisci suscipit temporibus, quidem aliquam voluptates.
        optio est cupiditate praesentium distinctio similique nemo impedit!
        Atque ea consequuntur eos id ipsa fugit. Nostrum perspiciatis sit
        similique cum placeat doloremque quod dolores voluptas harum tenetur, id
        nihil adipisci suscipit temporibus, quidem aliquam voluptates.
        dignissimos esse deserunt quasi iure repellendus molestias animi
        distinctio fuga asperiores iusto, magnam, id, dicta voluptas! Delectus
        voluptates tempora quibusdam. Non quaerat omnis magnam obcaecati
        voluptatum ut recusandae consequuntur nemo ad. Pariatur quas nisi quod
        optio est cupiditate praesentium distinctio similique nemo impedit!
        Atque ea consequuntur eos id ipsa fugit. Nostrum perspiciatis sit
        similique cum placeat doloremque quod dolores voluptas harum tenetur, id
        nihil adipisci suscipit temporibus, quidem aliquam voluptates.
      </p>
    </div>

    <div class="write">
      <label for="textarea" />
      <textarea
        name="textarea"
        id="textarea"
        maxlength={myMaxLength}
        on:input={handleInput}
        placeholder="Modifié l'article"
      />
      <p class="counter">
        Nombre de caractères restant : <span id="characterCounter"
          >{charactersRemaining}</span
        >/<span id="maximum">{myMaxLength}</span>
      </p>
      <div class="buttons">
        <input
          class="submit"
          type="submit"
          name="submit"
          value="Envoyer"
          spellcheck="false"
          aria-label="Envoyer article"
        />
      </div>

    </div>
    
  </div>
</main>

<style lang="scss">
  .wrap {
    display: block;

    padding:3rem;

    .picture {
      display: block;
      width: 100%;
      max-width: 100%;
      height: auto;

      box-shadow: 0 px 10px 0 rgb(31 38 135 / 45%);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      border-radius: 5px;
      border: 1px solid rgba(255, 255, 255, 0.18);
      img {
        width: 100%;
        height: 25rem;
      }
    }
    h2 {
      text-align: center;
      padding: 2rem;
      font-family: Tahoma;
    }
    p {
      font-family: Tahoma;
      padding: 2rem;
    }

    .article {
      display: block;

      padding: 00.625rem;
      box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      border-radius: 5px;
      border: 1px solid rgba(255, 255, 255, 0.18);
    }
    .write {
      display: block;

      box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      border-radius: 10px;
      border: 1px solid rgba(255, 255, 255, 0.18);
      width: 100%;
      margin-top: 30px;
    }

    #textarea {
      display: block;
      height: 40rem;
      width: 95%;
      margin: 2rem auto;
      resize: vertical;
      font-size: 1rem;
      min-height: 100px;
      border-radius: 5px;
      border: 1px solid #ccc;
      padding: 1rem;
    }
    .counter {
      position: fixed;
      bottom: 3.5rem;
      left: 1rem;
      font-size: 1.2rem;
  
 
  
      
     

      
    }
    .buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  
}

.submit {
  background-color:  rgba(136, 217, 143, 0.23);
  color: rgb(19, 18, 18);
  padding: 1rem 2rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  
}
      
     
            
            
      
    }
  
</style>
