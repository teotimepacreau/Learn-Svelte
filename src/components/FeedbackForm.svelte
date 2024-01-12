<script>
    import Button from "./Button.svelte";
    import Card from "./Card.svelte";

    const formBtn = {
        style: 'primary',
        type: 'submit',
        disabled: true
    }


    // MINIMUM 40 CHARACTERES DANS LE INPUT AVANT D'AUTORISER LA SOUMISSION DU FORM
    let text = ''
    let min = 10
    let message

    const handleInput = () => {
        if(text.trim().length <=min){
            message = `
            Text must be at least ${min} characters
            `
        }else{
            message = null
            formBtn.disabled = false
        }
    }
</script>

<Card>
    <header>
        <h2>How would you rate our service ?</h2>
    </header>
<form>
    <!-- RATING SELECT -->
    <div class="input-group">
        <input type="text" on:input={handleInput} bind:value = {text} placeholder="Tell us your experience">
        <Button type={formBtn.type} disabled={formBtn.disabled}
        class={formBtn.style} >Send</Button>
    </div>
</form>
</Card>

<style>
     header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
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

  .message{
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>