<script>
  import PollDetails from './PollDetails.svelte';
  import PollStore from '../store/PollStore';
  import { fade, slide, scale } from 'svelte/transition';
  import { flip } from 'svelte/animate';
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
    <!-- мы можем использовать анимацию и переходы только на html-элементе, а не компоненте. |local - действие только на конкретном компоненте -->
    <div in:fade out:scale|local>
      <PollDetails {poll} animate:flip={{ duration: 500 }} />
    </div>
  {/each}
</div>
