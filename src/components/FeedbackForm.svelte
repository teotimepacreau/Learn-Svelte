<script>
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingSelect from "./RatingSelect.svelte";

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  const formBtn = {
    style: "primary",
    type: "submit",
    disabled: true,
  };

  // MINIMUM 40 CHARACTERES DANS LE INPUT AVANT D'AUTORISER LA SOUMISSION DU FORM
  let text = "";
  let min = 10;
  let message;
  let rating;

  const handleSelect = (e) => (rating = e.detail);

  const handleInput = () => {
    if (text.trim().length <= min) {
      message = `
            Text must be at least ${min} characters
            `;
    } else {
      message = null;
      formBtn.disabled = false;
    }
  };

  const handleSubmit = () => {
    {
      if (text.trim().length > min) {
        const newFeedback = {
          id: Math.floor(Math.random() * 1000),
          text,
          rating: +rating, //le +rating c'est pour que le rating passe en nb et non pas en string
        };
        // A LA SOUMISSION DU FORMULAIRE, JE VEUX QU'UNE NOUVELLE CARTE S'AJOUTE, DONC IL FAUT L'OBJECT newFeedback vienne s'ajouter à l'array feedback de App.svelte
        dispatch("add-feedback-to-array", newFeedback);

        // POUR QU'APRES AVOIR SOUMIS LE FORMULAIRE LE TEXTE DISPARAISSE
        text = "";
      }
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate our service ?</h2>

    <form on:submit|preventDefault={handleSubmit}>
      <RatingSelect on:rating-select={handleSelect} />
      <div class="input-group">
        <input
          type="text"
          on:input={handleInput}
          bind:value={text}
          placeholder="Tell us your experience"
        />
        <Button
          type={formBtn.type}
          disabled={formBtn.disabled}
          class={formBtn.style}>Send</Button
        >
      </div>
      <!-- MESSAGE D'AVERTISSEMENT LONGUEUR MINIMALE DE TEXTE ATTENDUE -->
      {#if message}
        <div class="message">
          {message}
        </div>
      {/if}
    </form>
  </header>
</Card>

<style>
  h2 {
    font-size: calc(2 * var(--rythme));
    font-weight: 500;
    line-height: 1.2;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    color: black;
    background-color: #f1f1f1;
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
