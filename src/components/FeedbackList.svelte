<script>
  import FeedbackItem from "./FeedbackItem.svelte";
  import { fade, scale } from "svelte/transition";
  export let feedback = [];
</script>

<div class="feedback-list">
  {#each feedback as fb (fb.id)}
    <div in:scale out:fade="{{duration: 500}}">
      <FeedbackItem item={fb} on:delete-feedback />
    </div>
  {/each}
</div>

<style>
  .feedback-list {
    margin-top: calc(2 * var(--rythme));
  }
</style>
