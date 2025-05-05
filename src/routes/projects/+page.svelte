<script>
  import { onMount } from 'svelte';

  const links = [
    { name: 'GitHub', href: 'https://github.com/blockatebuilder' },
    { name: 'Discord', href: 'discord://-/users/814908440496701460' },
    { name: 'Projects', href: '/projects' }
  ];

  onMount(() => {
    const canvas = document.getElementById('langton-bg');
    const ctx = canvas.getContext('2d');

    const cellSize = 4;
    const cols = Math.floor(window.innerWidth / cellSize);
    const rows = Math.floor(window.innerHeight / cellSize);
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;

    const grid = new Array(cols * rows).fill(0);

    const ants = [
      { x: cols / 2, y: rows / 2, dir: 0, color: 'red' },
      { x: cols / 2 + 10, y: rows / 2, dir: 0, color: 'green' },
      { x: cols / 2 - 10, y: rows / 2, dir: 0, color: 'blue' }
    ];

    function stepAnt(ant) {
      const x = Math.floor(ant.x);
      const y = Math.floor(ant.y);
      const index = y * cols + x;
      const current = grid[index];

      // Turn based on current cell color (white = 0)
      const turnRight = current === 0;
      ant.dir = (ant.dir + (turnRight ? 1 : 3)) % 4;

      // Flip color: white <-> black
      grid[index] = current === 0 ? 1 : 0;

      // Draw trail in ant's color
      ctx.fillStyle = ant.color;
      ctx.fillRect(x * cellSize, y * cellSize, cellSize, cellSize);

      // Move forward
      switch (ant.dir) {
        case 0: ant.y = (ant.y - 1 + rows) % rows; break;
        case 1: ant.x = (ant.x + 1) % cols; break;
        case 2: ant.y = (ant.y + 1) % rows; break;
        case 3: ant.x = (ant.x - 1 + cols) % cols; break;
      }
    }

    function animate() {
      for (let i = 0; i < 50; i++) {
        ants.forEach(stepAnt);
      }
      requestAnimationFrame(animate);
    }

    // Start with a white background
    ctx.fillStyle = '#ffffff';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    animate();
  });
</script>


<style>
  #langton-bg {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
    width: 100vw;
    height: 100vh;
  }

  main {
    max-width: 700px;
    margin: auto;
    padding: 4rem 1rem;
    position: relative;
    z-index: 1;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 0.5rem;
  }

  p {
    font-size: 1.2rem;
    color: #555;
  }

  ul {
    list-style: none;
    padding: 0;
    margin-top: 2rem;
  }

  li {
    margin: 0.5rem 0;
  }

  a {
    text-decoration: none;
    color: #0070f3;
  }
</style>

<canvas id="langton-bg"></canvas>

<main>
  <h1>Projects</h1>
  <p>
    Some projects are in this
    <a href="https://github.com/BlockateBuilder/Roblox-Projects" target="_blank">github repository</a>, some are also in video form
    <a href="https://www.youtube.com/@RblxPf-n3t" target="_blank">here</a>.<br>
    The rest are listed here:
  </p>
  <div class="space"></div>
  <a href="https://create.roblox.com/store/asset/116112656702972" target="_blank">RemoteAnalyser</a>
  <p>
    RemoteAnalyserTool (RAT) is a Roblox model which can be required by anyone in-game to show remoteEvents being fired on every client.
  </p>
  <img src="/RemoteAnalyser.png" alt='RemoteAnalyser'>
</main>
