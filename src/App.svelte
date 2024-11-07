<script>
import Modal from "./Modal.svelte";
import AddPersonForm from "./AddPersonForm.svelte";

let showModal = true;

let people = [
	{ name: "yoshi", beltColour: "black", age: 25, id: 1 },
	{ name: "mario", beltColour: "orange", age: 45, id: 2 },
	{ name: "luigi", beltColour: "brown", age: 35, id: 3 },
];

let login = false;

const handleClick = (id) => {
	//delete person from people array
	//оставим в массиве элементы, id которых не равен тому, что надо удалять
	//важно переназначить переменную, а не просто применить на ней метод filter! Только переназначение активирует реактивную связь
	people = people.filter((person) => person.id != id);
};

const toggleModal = () => {
	showModal = !showModal;
};

//данные кастомного события приходят автоматически через переменную evt
const addPerson = (evt) => {
	showModal = false;
	// console.log(evt.detail);
	const person = evt.detail;
	people = [person, ...people]; //нельзя использовать push, для реактивной связи нужно обновить переменную
};
</script>

<style>
  main {
    text-align: center;
    max-width: 240px;
    margin: 0 auto;
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }

  .cards-items {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: #fff;
    margin: 2rem;
    padding: 0.5rem;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<!-- вставка компонента -->
<Modal isPromo={false} {showModal} on:click={toggleModal}>
  <!-- использование слота для передачи сложных данных внутрь компонента -->
  <AddPersonForm on:addPerson={addPerson} />

  <!-- именованный слот -->
  <div slot="title">
    <h3>Add a New Person</h3>
  </div>
</Modal>

<main>

  <button on:click={toggleModal}>Open Modal</button>

  <!-- нужен id в скобках для манипуляции элемента в дальнейшем -->
  <div class="cards">
    {#each people as person (person.id)}
      <div class="cards-items">
        <h4 style="text-decoration: underline">{person.name}</h4>
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
  </div>
</main>
