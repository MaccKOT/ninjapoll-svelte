<script>
  let name;
  let beltColour;
  let age;
  // let fighting = false;
  // let sneaking = false;
  // let running = false;
  let skills = [];

  const handleSubmit = () => {
    console.log(name, beltColour, age, skills);
  };
</script>

<style>

</style>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <!-- <input type="text" placeholder="belt colour" bind:value={beltColour} /> -->
  <!-- в отличии от ванильного js, если установлен тип number, то он и будет integer, а не строкой -->
  <input type="number" placeholder="age" bind:value={age} />
  <label>
    Belt colour:
    <select bind:value={beltColour}>
      <option value="black">black</option>
      <option value="tomato">tomato</option>
      <option value="orange">orange</option>
      <option value="pink">pink</option>
    </select>
  </label>
  <label for="skills">
    Skills:
    <br />
    <!-- 
    <input type="checkbox" bind:checked={fighting} />
    Fighting
    <br />
    <input type="checkbox" bind:checked={sneaking} />
    Sneaking
    <br />
    <input type="checkbox" bind:checked={running} />
    Running
    <br /> -->
  </label>
  <!-- bind group группировка свойств в массив. Чтобы различать свойства, нужно value -->
  <form id="skills">
    <input type="checkbox" bind:group={skills} value="fighting" />
    Fighting
    <br />
    <input type="checkbox" bind:group={skills} value="sneaking" />
    Sneaking
    <br />
    <input type="checkbox" bind:group={skills} value="running" />
    Running
  </form>
  <button type="submit">Add Person</button>
</form>
