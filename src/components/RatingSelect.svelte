<script>
    // let numbersOfRating = [0,1,2,3,4,5,6,7,8,9,10]

    let numbersOfRating = new Array(11)

    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher()

    const onChange = (e)=>{
        let select = e.target.value
        dispatch('rating-select', select)
    }
</script>

<ul class="rating">
    {#each numbersOfRating as number, i}
    <li>
        <input type="radio" value={i} name="rating" id="num{i}" on:change={onChange}>
        <label for="num{i}">{i}</label>
    </li> 
    {/each}
</ul>

<style>
    .rating{
        display: flex;
        justify-content: space-between;
        margin-top: var(--rythme);
    }
</style>