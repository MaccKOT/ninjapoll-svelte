<script>
  // export let message = 'default value'; //импорт значения из props со значением по дефолту
  export let showModal = false;
  export let isPromo = false;

  //Event Modifiers
  // stopPropagation - stop the event bubbling or capturing any further
  // capture - fires the handler during the capture phase not bubbling
  // once - makes sure the event can only fire once (removes handler)
  // preventDefault - prevent the default action (run e.preventDefault())
  // self - only fires the event if the clicked element is the target
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
    border: 2px solid rgba(57, 207, 27, 0.685);
    color: rgba(0, 0, 0, 0.75);
    /* box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.25); */
  }

  .promo .modal {
    background-color: crimson;
    color: white;
    font-weight: bold;
  }
</style>

{#if showModal}
  <!-- on:click это event emmit, который перехватит родительский компонент Modal -->
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <!-- class:promo={isPromo} - условное применение класса promo -->
      <!-- slot ищет переданный child и вставляет его -->
      <slot name="title" />
      <slot />
    </div>
  </div>
{/if}
