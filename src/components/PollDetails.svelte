<script>
  import Card from '../shared/Card.svelte';
  export let poll;
  import PollStore from '../store/PollStore';

  //reactive value
  $: totalVotes = poll.votesA + poll.votesB;
  $: percentA = Math.floor((100 / totalVotes) * poll.votesA);
  $: percentB = 100 - percentA;

  //handling votes
  const handleVote = (option, id) => {
    PollStore.update((currentPolls) => {
      let copiedPolls = [...currentPolls];
      let upvotedPoll = copiedPolls.find((poll) => poll.id == id);
      if (option === 'a') {
        upvotedPoll.votesA++;
      }
      if (option === 'b') {
        upvotedPoll.votesB++;
      }

      return copiedPolls;
    });
  };
</script>

<style>
  h3 {
    margin: 0 auto;
    color: #555;
  }
  p {
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }
  .answer {
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
    user-select: none;
  }
  .answer:hover {
    opacity: 0.6;
  }
  span {
    display: inline-block;
    padding: 10px 20px;
  }

  .percent {
    height: 100%;
    position: absolute;
    box-sizing: border-box;
  }
  .percent-a {
    border-left: 4px solid #d91b42;
    background-color: rgba(217, 27, 66, 0.2);
  }
  .percent-b {
    border-left: 4px solid #45c496;
    background-color: rgba(69, 196, 150, 0.2);
  }
</style>

<Card>
  <div class="poll">
    <h3>{poll.question}</h3>
    <p>Total votes: {totalVotes}</p>
    <div class="answer" on:click={() => handleVote('a', poll.id)}>
      <!-- dynamic value -->
      <div class="percent percent-a" style="width: {percentA}%" />
      <span>{poll.answerA} ({poll.votesA})</span>
    </div>
    <div class="answer" on:click={() => handleVote('b', poll.id)}>
      <div class="percent percent-b" style="width: {percentB}%" />
      <span>{poll.answerB} ({poll.votesB})</span>
    </div>
  </div>
</Card>
