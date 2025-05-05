<script>
  import { onMount } from 'svelte';

  onMount(() => {
    const canvas = document.createElement('canvas');
    canvas.id = 'life-canvas';
    document.body.appendChild(canvas);

    const ctx = canvas.getContext('2d');
    const cellSize = 6;
    const cols = Math.floor(window.innerWidth / cellSize);
    const rows = Math.floor(window.innerHeight / cellSize);
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;

    let grid = Array.from({ length: rows }, () =>
      Array.from({ length: cols }, () => (Math.random() > 0.8 ? 1 : 0))
    );

    function drawGrid() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
      for (let y = 0; y < rows; y++) {
        for (let x = 0; x < cols; x++) {
          if (grid[y][x] === 1) {
            ctx.fillRect(x * cellSize, y * cellSize, cellSize, cellSize);
          }
        }
      }
    }

    function nextGeneration() {
      const newGrid = grid.map(arr => [...arr]);
      for (let y = 0; y < rows; y++) {
        for (let x = 0; x < cols; x++) {
          const neighbors = [
            [-1, -1], [-1, 0], [-1, 1],
            [0, -1],           [0, 1],
            [1, -1], [1, 0], [1, 1]
          ].reduce((acc, [dy, dx]) => {
            const ny = y + dy;
            const nx = x + dx;
            if (ny >= 0 && ny < rows && nx >= 0 && nx < cols) {
              return acc + grid[ny][nx];
            }
            return acc;
          }, 0);

          if (grid[y][x] === 1) {
            newGrid[y][x] = neighbors === 2 || neighbors === 3 ? 1 : 0;
          } else {
            newGrid[y][x] = neighbors === 3 ? 1 : 0;
          }
        }
      }
      grid = newGrid;
    }

    function animate() {
      drawGrid();
      nextGeneration();
      requestAnimationFrame(animate);
    }

    animate();
  });
</script>

<style>
  #life-canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -2;
    width: 100%;
    height: 100%;
    background: white;
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

<main>
  <h1>snas</h1>
  <p>
    Hey, I'm snas, also known as ._snas on 
    <a href='discord://-/users/814908440496701460'>Discord</a> or as BlockateBuilder01 on 
    <a href='https://www.roblox.com/users/5494278467/profile' target="_blank">Roblox</a>.
  </p>

  <ul>
    
  </ul>
  <img src="https://static.wikia.nocookie.net/noooooooooooo/images/4/41/06A40DEE-E17E-4747-A0DF-B5C73743EB2D.png/revision/latest?cb=20201112015220" alt='sans'>
</main>
