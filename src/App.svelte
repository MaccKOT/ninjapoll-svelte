<script>
  let firstName = "Jimi";
  let lastName = "Hendrix";
  let beltColor = "black";

  const handleClick = () => {
    beltColor = "orange";
  };

  const handleInput = e => {
    beltColor = e.target.value;
  };

  //Создание реактивной переменной иил реактивного выражения
  $: fullName = firstName + " " + lastName;
  $: {
    //срабатывает каждый раз при изменении переменной
    console.log(beltColor);
    console.log(fullName);
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>

  <p>{fullName} - {beltColor} belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <!-- прямое связывание параметров -->
  <input type="text" bind:value={beltColor} />
</main>
