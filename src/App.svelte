<script>
	import { onMount } from 'svelte'
	
	onMount(() => {
	  if (
		localStorage.theme === 'dark' ||
		(!('theme' in localStorage) &&
		  window.matchMedia('(prefers-color-scheme: dark)').matches)
	  ) {
		document.documentElement.classList.add('dark')
	  } else {
		document.documentElement.classList.remove('dark')
	  }
	})
	
	function toggleDarkMode() {
	  if (document.documentElement.classList.toggle('dark')) {
		localStorage.setItem('theme', 'dark')
	  } else {
		localStorage.removeItem('theme')
	  }
	}
	</script>

<div class="flex flex-col min-h-screen">
  <header class="p-5 bg-indigo-200 dark:bg-indigo-900">
    <nav class="flex flex-wrap justify-between items-center">
	  <h2 class="text-green-900 dark:text-green-300">Dark Mode Demo</h2>
	    <button on:click={toggleDarkMode} class="px-4 py-1 border-2 rounded-md border-green-700 dark:border-green-300
		 text-green-700 dark:text-green-300 hover:bg-indigo-300 dark:hover:bg-indigo-700">Click me!</button>
	</nav>
  </header>
  <main class="p-5 flex-grow flex justify-center items-center flex-col 
  bg-indigo-100 dark:bg-indigo-800 text-green-900 dark:text-green-300">
    <div>
      <h1 class="text-2xl">Who turned out the lights?</h1>
    </div>
  </main>
  <footer class="flex justify-center p-5 bg-indigo-200 dark:bg-indigo-900 text-green-900 dark:text-green-300">Svelte and Tailwind</footer>
</div>

<style global lang="postcss">
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>