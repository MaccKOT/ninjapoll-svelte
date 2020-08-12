<script>
  import Modal from './Modal.svelte';

  let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 },
  ];

  let login = false;

  const handleClick = (id) => {
    //delete person from people array
    //оставим в массиве элементы, id которых не равен тому, что надо удалять
    //важно переназначить переменную, а не просто применить на ней метод filter! Только переназначение активирует реактивную связь
    people = people.filter((person) => person.id != id);
  };
</script>

<style>
  main {
    text-align: center;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>

  <!-- условный вывод -->
  {#if login === true}
    <button style="background-color: #ccc" on:click={() => (login = false)}>
      Log Out
    </button>
  {:else if login !== true}
    <!-- вставка компонента -->
    <Modal message="Hey, i am is prop value" isPromo={true} />
    <button on:click={() => (login = true)}>Log In</button>
  {/if}

  <!-- нужен id в скобках для манипуляции элемента в дальнейшем -->
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p>
          <strong>master ninja</strong>
        </p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt</p>
      <!-- мы не можем использовать handleClick(person.id), потому что это сразу исполнит функцию, поэтому надо вызовать через arrow-функцию -->
      <button on:click={() => handleClick(person.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>
