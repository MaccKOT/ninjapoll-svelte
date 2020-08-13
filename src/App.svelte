<script>
  import Header from './components/Header.svelte';
  import Footer from './components/Footer.svelte';
  import Tabs from './shared/Tabs.svelte';

  //tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';

  const tabChange = (e) => {
    activeItem = e.detail;
  };
</script>

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>

<Header />
<main>
  <Tabs {items} {activeItem} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <p>Poll list component</p>
  {:else if activeItem === 'Add New Poll'}
    <p>New Poll component</p>
  {/if}
</main>
<Footer />
