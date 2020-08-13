<script>
  export let polls = [];
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: (2, 1fr);
    gap: 20px;
  }
</style>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div class="">{poll.question}</div>
  {/each}

</div>
