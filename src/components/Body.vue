
<template>
	<main class="ds-main">
		<section class="ds-banner">
			<img class="ds-banner-img" src="https://assets-prd.ignimgs.com/2022/02/23/darksouls-1645649648572.jpg" alt="Dark Souls Banner" />
			<div class="ds-banner-text">
				<h1>Dark Souls Saga</h1>
				<p>"Prepárate para morir"</p>
			</div>
		</section>
		<section class="ds-games">
			<h2>Juegos de la saga</h2>
			<div class="ds-cards">
				<div v-for="game in games" :key="game.title" class="ds-card" @mouseenter="hoverGame(game)" @mouseleave="unhoverGame(game)">
					<img :src="game.img" :alt="game.title" class="ds-card-img" />
					<h3>{{ game.title }}</h3>
					<transition name="fade">
						<p v-if="game.showDesc" class="ds-desc">{{ game.desc }}</p>
					</transition>
					<button class="ds-btn" @click="showDetails(game)">Ver detalles</button>
				</div>
			</div>
		</section>
		<transition name="modal">
			<div v-if="selectedGame" class="ds-modal" @click.self="selectedGame = null">
				<div class="ds-modal-content">
					<h2>{{ selectedGame.title }}</h2>
					<img :src="selectedGame.img" :alt="selectedGame.title" />
					<p>{{ selectedGame.details }}</p>
					<button class="ds-btn" @click="selectedGame = null">Cerrar</button>
				</div>
			</div>
		</transition>
	</main>
</template>

<script>
export default {
	name: 'BodyDarkSouls',
	data() {
		return {
			games: [
				{
					title: 'Dark Souls',
					img: 'https://upload.wikimedia.org/wikipedia/en/8/8d/Dark_Souls_Cover_Art.jpg',
					desc: 'El inicio de la leyenda. Un mundo oscuro, desafiante y lleno de secretos.',
					details: 'Dark Souls (2011) revolucionó los juegos de acción-RPG con su dificultad, diseño de niveles y atmósfera opresiva. Explora Lordran, enfréntate a jefes épicos y descubre una narrativa ambiental única.',
					showDesc: false,
				},
				{
					title: 'Dark Souls II',
					img: 'https://assets-prd.ignimgs.com/2022/01/05/dark-souls-2-scholar-button-1641371397910.jpg?crop=1%3A1%2Csmart&format=jpg&auto=webp&quality=80',
					desc: 'Una secuela desafiante con nuevas mecánicas y escenarios.',
					details: 'Dark Souls II (2014) expande el universo con nuevas áreas, enemigos y una historia diferente. Mantiene la dificultad y añade mayor personalización de personajes.',
					showDesc: false,
				},
				{
					title: 'Dark Souls III',
					img: 'https://www.play-zine.com/wp-content/uploads/2016/04/dark-souls-3-1.jpg',
					desc: 'El cierre épico de la saga, rápido y visualmente impresionante.',
					details: 'Dark Souls III (2016) culmina la saga con combates más ágiles, gráficos mejorados y una conclusión memorable. Un homenaje a los fans y a la dificultad clásica.',
					showDesc: false,
				},
			],
			selectedGame: null,
		};
	},
	methods: {
		hoverGame(game) {
			game.showDesc = true;
		},
		unhoverGame(game) {
			game.showDesc = false;
		},
		showDetails(game) {
			this.selectedGame = game;
		},
	},
};
</script>

<style scoped>
.ds-main {
	font-family: 'Segoe UI', 'Arial', sans-serif;
	background: linear-gradient(180deg, #232526 0%, #1a1a1a 100%);
	min-height: 100vh;
	color: #f5f5f5;
	padding-bottom: 2rem;
}
.ds-banner {
	position: relative;
	width: 100%;
	height: 320px;
	overflow: hidden;
	margin-bottom: 2rem;
}
.ds-banner-img {
	width: 100%;
	height: 100%;
	object-fit: cover;
	filter: brightness(0.5) grayscale(0.2);
}
.ds-banner-text {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	text-align: center;
}
.ds-banner-text h1 {
	font-size: 3rem;
	letter-spacing: 2px;
	color: #ffd700;
	text-shadow: 0 2px 16px #000;
}
.ds-banner-text p {
	font-size: 1.5rem;
	color: #fff;
	margin-top: 0.5rem;
	text-shadow: 0 2px 8px #000;
}
.ds-games {
	max-width: 1100px;
	margin: 0 auto;
	padding: 1rem;
}
.ds-games h2 {
	text-align: center;
	color: #ffd700;
	margin-bottom: 2rem;
	font-size: 2rem;
}
.ds-cards {
	display: flex;
	flex-wrap: wrap;
	gap: 2rem;
	justify-content: center;
}
.ds-card {
	background: #232526;
	border-radius: 16px;
	box-shadow: 0 4px 24px #000a;
	padding: 1.5rem 1rem 1rem 1rem;
	width: 260px;
	text-align: center;
	transition: transform 0.2s, box-shadow 0.2s;
	cursor: pointer;
	position: relative;
}
.ds-card:hover {
	transform: scale(1.06) translateY(-8px);
	box-shadow: 0 8px 32px #ffd70055;
	border: 1.5px solid #ffd700;
}
.ds-card-img {
	width: 100%;
	height: 180px;
	object-fit: cover;
	border-radius: 10px;
	margin-bottom: 1rem;
	box-shadow: 0 2px 12px #0008;
}
.ds-card h3 {
	color: #ffd700;
	margin-bottom: 0.5rem;
}
.ds-desc {
	color: #fff;
	font-size: 1rem;
	margin-bottom: 0.5rem;
	min-height: 48px;
	transition: opacity 0.2s;
}
.ds-btn {
	background: #ffd700;
	color: #232526;
	border: none;
	border-radius: 8px;
	padding: 0.5rem 1.2rem;
	font-size: 1rem;
	font-weight: bold;
	cursor: pointer;
	margin-top: 0.5rem;
	transition: background 0.2s, color 0.2s, box-shadow 0.2s;
	box-shadow: 0 2px 8px #ffd70044;
}
.ds-btn:hover {
	background: #232526;
	color: #ffd700;
	box-shadow: 0 4px 16px #ffd70099;
}
.fade-enter-active, .fade-leave-active {
	transition: opacity 0.2s;
}
.fade-enter, .fade-leave-to {
	opacity: 0;
}
.ds-modal {
	position: fixed;
	top: 0; left: 0; right: 0; bottom: 0;
	background: rgba(20,20,20,0.85);
	display: flex;
	align-items: center;
	justify-content: center;
	z-index: 1000;
}
.ds-modal-content {
	background: #232526;
	border-radius: 16px;
	padding: 2rem;
	max-width: 400px;
	text-align: center;
	box-shadow: 0 8px 32px #000a;
	color: #fff;
}
.ds-modal-content img {
	width: 80%;
	border-radius: 10px;
	margin-bottom: 1rem;
	box-shadow: 0 2px 12px #0008;
}
.modal-enter-active, .modal-leave-active {
	transition: opacity 0.2s;
}
.modal-enter, .modal-leave-to {
	opacity: 0;
}
</style>
