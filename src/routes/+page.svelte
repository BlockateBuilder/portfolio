<script>
  import '../app.css';
  import { onMount } from 'svelte';

  const links = [
    { name: 'GitHub', href: 'https://github.com/blockatebuilder' },
    { name: 'Discord', href: 'discord://-/users/814908440496701460' },
    { name: 'Projects', href: '/projects' }
  ];

  onMount(() => {
    const canvas = document.getElementById('ant-canvas');
    const ctx = canvas.getContext('2d');

    const cellSize = 4;
    const cols = Math.floor(window.innerWidth / cellSize);
    const rows = Math.floor(window.innerHeight / cellSize);
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;

    const grid = new Array(cols * rows).fill(0);

    const ants = [
      { x: cols / 2, y: rows / 2, dir: 0 },
      { x: cols / 2 + 10, y: rows / 2, dir: 0 },
      { x: cols / 2 - 10, y: rows / 2, dir: 0 }
    ];

    let prevCenter = getCenter(ants);

    function stepAnt(ant) {
      const x = Math.floor(ant.x);
      const y = Math.floor(ant.y);
      const index = y * cols + x;
      const current = grid[index];

      // Turn based on current cell color
      const turnRight = current === 0;
      ant.dir = (ant.dir + (turnRight ? 1 : 3)) % 4;

      // Flip color: white <-> black
      grid[index] = current === 0 ? 1 : 0;

      // Move forward
      switch (ant.dir) {
        case 0: ant.y = (ant.y - 1 + rows) % rows; break;
        case 1: ant.x = (ant.x + 1) % cols; break;
        case 2: ant.y = (ant.y + 1) % rows; break;
        case 3: ant.x = (ant.x - 1 + cols) % cols; break;
      }
    }

    function getCenter(ants) {
      const cx = ants.reduce((sum, a) => sum + a.x, 0) / ants.length;
      const cy = ants.reduce((sum, a) => sum + a.y, 0) / ants.length;
      return {
        x: cx * cellSize,
        y: cy * cellSize
      };
    }

    function animate() {
      for (let i = 0; i < 10; i++) {
        ants.forEach(stepAnt);
        const newCenter = getCenter(ants);

        ctx.strokeStyle = 'rgba(0, 0, 0, 0.4)';
        ctx.lineWidth = 1;
        ctx.beginPath();
        ctx.moveTo(prevCenter.x, prevCenter.y);
        ctx.lineTo(newCenter.x, newCenter.y);
        ctx.stroke();

        prevCenter = newCenter;
      }

      requestAnimationFrame(animate);
    }

    // Start with white canvas
    ctx.fillStyle = '#ffffff';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    animate();
  });
</script>


<style>
  body {
    margin: 0;
    overflow: hidden;
    background: #f8f8f8;
  }

  canvas#ant-canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
    background: white;
  }

  main {
    max-width: 700px;
    margin: auto;
    padding: 4rem 1rem;
    font-family: system-ui, sans-serif;
    color: #333;
    position: relative;
    z-index: 1;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 0.5rem;
  }

  p {
    font-size: 1.25rem;
    color: #555;
    margin-bottom: 1.5rem;
  }

  a {
    text-decoration: none;
    color: #0070f3;
    transition: color 0.2s ease;
  }

  a:hover {
    color: #0051a3;
  }

  ul {
    list-style: none;
    padding: 0;
    margin-top: 2rem;
  }

  li {
    margin: 0.75rem 0;
  }

  .about-link {
    display: inline-block;
    margin-top: 1rem;
    font-weight: 500;
  }
</style>

<canvas id="ant-canvas"></canvas>

<main>
  <h1>snas</h1>
  <p>Experienced Roblox Scripter & Developer specializing in game mechanics, systems, and custom tools.</p>
  <a class="about-link" href="/about">Learn more about me →</a>

  <ul>
    {#each links as link}
      <li>
        <a href={link.href} target="_blank" rel="noopener noreferrer">
          {link.name}
        </a>
      </li>
    {/each}
  </ul>
</main>
