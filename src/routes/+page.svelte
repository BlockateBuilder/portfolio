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
</main>
