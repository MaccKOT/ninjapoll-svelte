<script>
  export let message = 'default value'; //импорт значения из props со значением по дефолту
  let showModal = true;
  export let isPromo = false;
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
    box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.15);
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
      <p>{message}</p>
    </div>
  </div>
{/if}
