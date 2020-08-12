<script>
  let showModal = true;
</script>

<style>
  .backdrop {
    color: white;
    background-color: rgba(0, 0, 0, 0.35);
  }
</style>

{#if showModal}
  <div class="backdrop">
    <div class="modal">
      <p>Sign up for offers!</p>
    </div>
  </div>
{/if}
