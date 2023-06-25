<script>
    import { onMount } from 'svelte';
    let counter = 0;
  
    function handleClick(e) {
      counter++;
      e.target.style.width = e.target.width * 1.01 + 'px';
        e.target.style.height = e.target.height * 1.01 + 'px';
    }
  
    onMount(() => {
      document.addEventListener('keydown', handleClick);
    });

  </script>
  
  <main>
    <h1>Popcat-like Game</h1>
    <img on:click={handleClick} src="/o.jpg" alt="">
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
    img {
      border-radius: 25px;
    }
  </style>
  