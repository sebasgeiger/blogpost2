<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
</script>

<div class="container">
    <article>
      <h1>Welcome to NHL Information and Statistics!</h1>
      <p>This blog's purpose is to display information about NHL standings, teams and players. This blog takes real time statistics that shows up to date information about NHL teams and players.</p>
      <p>If you want to know what team is in first place currently or what teams have played the most games so far then this blog is the perfect spot for you.</p>
      <p>This blog is the place for all your National Hockey League information. Whether you are wondering about your favorite team or just curious what teams are in what divisions, this blog has all the information for you.</p>
    </article>
    <aside>
      <figure>
        <img src="/nhl.png" alt="NHL Logo">
      </figure>
    </aside>
  </div>
  
  <style>
    figure {
      margin-top: 7rem;
    }
  </style>