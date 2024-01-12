<script>
    import Card from "./Card.svelte";
    export let item

    // EVENEMENT DELETE : clic sur le bouton close entraîne SUPPRESSION DE L'AVIS
    //on a pas accès à l'array d'item donc il faut envoyer l'évènemen t à App.svelte

    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher()

    const handleDelete = (itemId)=>{
        dispatch('delete-feedback',itemId)
    }
</script>

<Card>  
    <div class="num-display">{item.rating}</div>
    <button class="close" on:click={()=> handleDelete(item.id)}>X</button>
    <p class="text-display">{item.text}</p>
</Card>

<style>
    button {
        border: none;
        background-color: unset;
    }
    .num-display{
        position: absolute;
        text-align: center;
        top: -0.5rem;
        left: -0.5rem;
        width: 2rem;
        height: 2rem;
        display: grid;
        place-items: center;
        border-radius: 50%;
        background-color: bisque;
    }

    .close {
        position: absolute;
        right: 0;
        top: 0;
        font-size: 0.8rem;
        font-weight: 600;
        background-color: darkgrey;
        color: #f1f1f1;
        border-radius: 10%;
        display: grid;
        place-items: center;
        width: 1.4rem;
        height: 1.4rem;
        cursor: pointer;
    }
</style>