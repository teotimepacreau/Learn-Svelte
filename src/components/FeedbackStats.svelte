<script>
    export let count
    export let average
</script>

<div class="feedback-stats">
    <span>{count} Reviews</span>
    <span>Ratings average : {average}</span>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>