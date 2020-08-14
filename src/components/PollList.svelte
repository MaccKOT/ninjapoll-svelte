<script>
  import PollDetails from './PollDetails.svelte';
  import PollStore from '../store/PollStore';

  let polls = [];

  //подписка на хранилище данных. Каждый раз при изменении данных в хранилище будет срабатывать callback функции
  PollStore.subscribe((data) => {
    polls = data;
  });
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
</style>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <!-- on:vote - forwarding event to parent -->
    <PollDetails {poll} on:vote />
  {/each}

</div>
