<!-- in /src/routes/+layout.svelte -->
<script>
	import '../global.css';
  </script>
  
  <nav>
	<a href="/">Home</a>
	<a href="/posts">Posts</a>
	<a href="/favs">Favs</a>
	<a href="/resources">Resources</a>
	<a href="/donate">Donate</a>
	<a href="/about">About</a>
  </nav>
  
  <main>
	<slot />
  </main>
  
  <footer>
	<a href="/">&copy;2023 Sebastian Geiger</a>
  </footer>
  
  <style>
    nav, footer {
      display: flex;
      justify-content: space-evenly;
      padding: .5em;
      background-color:silver;
      color: black;
    }
    nav {
    font-weight: 900;
    text-transform: uppercase;
  }
    main {
      grid-row: 2;
    }
    footer {
    grid-row: 3;
    position: sticky;
    bottom: 0;
  }
  </style>
