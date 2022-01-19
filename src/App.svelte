<script>
	import { Router, Route, Link } from "svelte-navigator";
	import Game from "./Game/Game.svelte";
	import Sobre from "./Sobre/Sobre.svelte";
</script>

<Router>
	<header>
		<h1><Link class="link-home" to="/">Campo Minado</Link></h1>
		<!-- <nav>
			<Link class="link" to="/">Home</Link>
			<Link class="link" to="game">Jogar</Link>
			<Link class="link" to="sobre">Sobre</Link>
		</nav> -->
	</header>
	<main>
		<Route path="/">
			<Link class="link" to="game"><span style="display: block; text-align: center;">Jogar </span></Link>
			<Link class="link" to="sobre"><span style="display: block; text-align: center;">Sobre</span></Link>
			<!-- <img src="assets/bomb.png" alt="bomb"> -->
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
<style>
	:global(.link) {
		transform-style: preserve-3d;
		text-decoration: none;
		text-transform: uppercase;
		font-size: 20px;
		display: block;
		border-radius: 5px;
		font-weight: bold;
		color: #fff;
		margin-top: 5%;
		margin-right: 45%;
		margin-left: 40%;
		padding: 10px;
		border: 2px solid #5fe36a;
	}
	:global(.link-home) {
		transform-style: preserve-3d;
		text-decoration: none;
		text-transform: uppercase;
		font-size: 50px;

		border-radius: 5px;
		font-weight: bold;
		color: #fff;

		margin: 0px 15px;
		padding: 10px 35px;

	}

</style>