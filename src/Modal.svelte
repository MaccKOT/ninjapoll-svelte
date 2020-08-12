<script>
  let showModal = true;
  let isPromo = true;
</script>

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background-color: rgba(0, 0, 0, 0.8);
    color: white;
  }

  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background-color: white;
    color: rgba(0, 0, 0, 0.75);
  }

  .promo .modal {
    background-color: crimson;
    color: white;
    font-weight: bold;
  }
</style>

{#if showModal}
  <div class="backdrop" class:promo={isPromo}>
    <div class="modal">
      <!-- class:promo={isPromo} - условное применение класса promo -->
      <p>Sign up for offers!</p>
    </div>
  </div>
{/if}
