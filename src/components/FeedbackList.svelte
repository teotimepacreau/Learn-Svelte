<script>
    import FeedbackItem from "./FeedbackItem.svelte";
    export let feedback = []

</script>

<div class="feedback-list">
{#each feedback as fb (fb.id)}
    <FeedbackItem item={fb} on:delete-feedback/>
{/each}
</div>

<style>
    .feedback-list {
        margin-top: calc(2*var(--rythme));
    }
</style>