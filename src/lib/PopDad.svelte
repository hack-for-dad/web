<script>
    import { onMount } from 'svelte';
  
    let counter = 0;
  
    function handleClick() {
      counter++;
    }
  
    onMount(() => {
      document.addEventListener('keydown', handleClick);
    });
  
    function handleReset() {
      counter = 0;
    }
  </script>
  
  <main>
    <h1>Popcat-like Game</h1>
    <button on:click={handleClick} class="nine-button">๙</button>
    <p>Counter: {counter}</p>
  </main>
  
  <style>
    main {
      text-align: center;
      padding: 20px;
    }
  
    h1 {
      font-size: 24px;
      margin-bottom: 10px;
    }
  
    button {
      padding: 10px 20px;
      font-size: 18px;
      margin-bottom: 10px;
    }
  
    p {
      font-size: 24px;
      margin-bottom: 10px;
    }
    
    .nine-button {
        background-color: rgb(241, 241, 0);
        padding-left: 2.5rem;
        padding-right: 2.5rem;
        border-radius: 1rem;
        font-size: 5rem;
        border: 0px solid black;
    }

    .nine-button:active {
        background-color: rgb(204, 204, 0);
        padding-left: 2.5rem;
        padding-right: 2.5rem;
        border-radius: 1rem;
    }
  </style>
  