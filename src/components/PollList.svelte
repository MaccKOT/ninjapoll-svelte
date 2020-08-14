<script>
  import PollDetails from './PollDetails.svelte';
  import PollStore from '../store/PollStore';
  // import { onDestroy } from 'svelte'; //хуки нужно импортировать для использования

  // let polls = [];

  //подписка на хранилище данных. Каждый раз при изменении данных в хранилище будет срабатывать callback функция. От события важно отписаться, когда доступ не нужен, иначе будут проблемы с производительностью
  // const unsub = PollStore.subscribe((data) => {
  //   polls = data;
  // });

  //lifecycle hooks

  // onMount(() => {
  //   //time to get data from a db
  //   console.log('component mounted');
  // });

  // onDestroy(() => {
  //   console.log('destroyed');
  //   unsub(); //<-- отписка от события хранилища | unsub from store
  // });
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
</style>

<div class="poll-list">
  <!-- $PollStore - очень простая автоматическая подписка на хранилище. Отписка произойдёт автоматически, следить за компонентом не нужно -->
  {#each $PollStore as poll (poll.id)}
    <!-- on:vote - forwarding event to parent -->
    <PollDetails {poll} on:vote />
  {/each}

</div>
