<script>
  const links = [
    { name: 'GitHub', href: 'https://github.com/blockatebuilder' },
    { name: 'Projects', href: '/projects' },
    { name: 'Discord', href: 'discord://-/users/814908440496701460'}
  ];
</script>

<style>
  main {
    max-width: 700px;
    margin: auto;
    padding: 4rem 1rem;
    font-family: system-ui, sans-serif;
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

  .wave-background {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to bottom, #fff 0%, #e0e0e0 100%);
    z-index: -1;
  }

  .wave {
    position: absolute;
    bottom: 0;
    width: 200%;
    height: 20%;
    background: rgba(255, 255, 255, 0.5);
    border-radius: 100%;
    animation: wave-animation 10s linear infinite;
  }
  @keyframes wave-animation {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(-50%);
    }
  }

  .wave:nth-child(1) {
    animation-duration: 10s;
    animation-delay: 0s;
    opacity: 0.3;
  }

  .wave:nth-child(2) {
    animation-duration: 15s;
    animation-delay: 2s;
    opacity: 0.2;
  }

  .wave:nth-child(3) {
    animation-duration: 20s;
    animation-delay: 5s;
    opacity: 0.1;
  }

</style>

<main>
  <h1>snas</h1>
  <p>Roblox Scripter & Developer with multiple years of experience</p>
  <a href="/about">About</a>
  <ul>
    {#each links as link}
      <li><a href={link.href} target="_blank" rel="noopener noreferrer">{link.name}</a></li>
    {/each}
  </ul>

  <div class="wave-background">
    <div class="wave"></div>
    <div class="wave"></div>
    <div class="wave"></div>
  </div>
</main>
