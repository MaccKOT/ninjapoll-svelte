<script>
  import PollDetails from './PollDetails.svelte';
  export let polls = [];
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
</style>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <!-- on:vote - forwarding event to parent -->
    <PollDetails {poll} on:vote />
  {/each}

</div>
