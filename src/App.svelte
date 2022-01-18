<script>
	import { Router, Route, Link } from "svelte-navigator";
	import Game from "./Game/Game.svelte";
	import Sobre from "./Sobre/Sobre.svelte";
</script>

<Router>
	<header>
		<h1>Campo Minado</h1>
		<nav>
			<Link class="link" to="/">Home</Link>
			<Link class="link" to="game">Jogar</Link>
			<Link class="link" to="sobre">Sobre</Link>
		</nav>
	</header>
	<main>
		<Route path="/">
			<h3>Home</h3>
			<p>Home sweet home...</p>
		</Route>

		<Route path="game">
			<Game/>
		</Route>

		<Route path="sobre">
			<Sobre/>
		</Route>

	</main>
</Router>

<link rel="stylesheet" href="global.css">