
<template>
	<header class="header">
		<div class="logo">
			<img src="@/assets/logo.png" alt="Logo" />
			<span>SoulsPage</span>
		</div>
		<nav class="menu">
			<ul>
				<li v-for="item in menuItems" :key="item.title" @mouseenter="showSubmenu(item)" @mouseleave="hideSubmenu(item)">
					<a href="#" :class="{ active: item.active }">
						<i :class="item.icon"></i> {{ item.title }}
					</a>
					<transition name="fade">
						<ul v-if="item.submenu && item.showSubmenu" class="submenu">
							<li v-for="sub in item.submenu" :key="sub.title">
								<a href="#">{{ sub.title }}</a>
							</li>
						</ul>
					</transition>
				</li>
			</ul>
		</nav>
	</header>
</template>

<script>
export default {
	name: 'encabezadoPagina',
	data() {
		return {
			menuItems: [
				{
					title: 'Inicio',
					icon: 'fas fa-home',
					active: true,
				},
				{
					title: 'Juegos',
					icon: 'fas fa-gamepad',
					submenu: [
						{ title: 'Acción' },
						{ title: 'Aventura' },
						{ title: 'RPG' },
						{ title: 'Estrategia' },
					],
					showSubmenu: false,
				},
				{
					title: 'Noticias',
					icon: 'fas fa-newspaper',
				},
				{
					title: 'Foro',
					icon: 'fas fa-comments',
				},
				{
					title: 'Contacto',
					icon: 'fas fa-envelope',
				},
			],
		};
	},
	methods: {
		showSubmenu(item) {
			if (item.submenu) item.showSubmenu = true;
		},
		hideSubmenu(item) {
			if (item.submenu) item.showSubmenu = false;
		},
	},
};
</script>

<style scoped>
.header {
	background: linear-gradient(90deg, #1a1a2e 0%, #16213e 100%);
	color: #fff;
	padding: 1rem 2rem;
	display: flex;
	align-items: center;
	justify-content: space-between;
	box-shadow: 0 2px 8px rgba(0,0,0,0.4);
	position: relative;
	z-index: 10;
}
.logo {
	display: flex;
	align-items: center;
	font-size: 1.5rem;
	font-weight: bold;
	gap: 0.5rem;
}
.logo img {
	width: 40px;
	height: 40px;
	border-radius: 50%;
	box-shadow: 0 0 8px #0f3460;
}
.menu ul {
	list-style: none;
	display: flex;
	gap: 2rem;
	margin: 0;
	padding: 0;
}
.menu > ul > li {
	position: relative;
	transition: transform 0.2s;
}
.menu > ul > li:hover {
	transform: scale(1.08) rotate(-2deg);
	z-index: 20;
}
.menu a {
	color: #fff;
	text-decoration: none;
	font-size: 1.1rem;
	padding: 0.5rem 1rem;
	border-radius: 8px;
	transition: background 0.2s, color 0.2s, box-shadow 0.2s;
	display: flex;
	align-items: center;
	gap: 0.5rem;
}
.menu a.active,
.menu a:hover {
	background: #0f3460;
	color: #ffd700;
	box-shadow: 0 2px 8px #0f3460aa;
}
.submenu {
	position: absolute;
	top: 110%;
	left: 0;
	background: #16213e;
	border-radius: 8px;
	box-shadow: 0 4px 16px #0f3460cc;
	min-width: 160px;
	padding: 0.5rem 0;
	animation: submenu-pop 0.2s;
}
.submenu li {
	padding: 0;
}
.submenu a {
	display: block;
	padding: 0.5rem 1.5rem;
	color: #fff;
	border-radius: 0;
	font-size: 1rem;
	transition: background 0.2s, color 0.2s;
}
.submenu a:hover {
	background: #0f3460;
	color: #ffd700;
}
@keyframes submenu-pop {
	0% { opacity: 0; transform: translateY(-10px); }
	100% { opacity: 1; transform: translateY(0); }
}
.fade-enter-active, .fade-leave-active {
	transition: opacity 0.2s;
}
.fade-enter, .fade-leave-to {
	opacity: 0;
}
</style>
