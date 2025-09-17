<template>
  <footer class="ds-footer">
    <div class="footer-content">
      <img src="../assets/souls.png" alt="Dark Souls Logo" class="ds-logo" />
      <div class="footer-text">
        <h2>Dark Souls Fan Page</h2>
        <p>
          “La oscuridad solo es el principio. Prepárate para morir.”<br>
          © 2025 - Todos los derechos reservados. Esta página es un tributo a la saga Dark Souls.
        </p>
      </div>
      <div class="footer-links">
        <a href="https://www.bandainamcoent.com/games/dark-souls" target="_blank">Sitio oficial</a>
        <a href="https://darksouls.fandom.com/es/wiki/Dark_Souls_Wiki" target="_blank">Wiki Dark Souls</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "pieDePagina"
};
</script>

<style scoped>
.ds-footer {
  background: #181818;
  color: #f5c16c;
  padding: 32px 0 16px 0;
  text-align: center;
  font-family: 'Cinzel', serif;
  border-top: 2px solid #a67c52;
}
.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ds-logo {
  width: 80px;
  margin-bottom: 16px;
  border-radius: 8px;
  box-shadow: 0 0 12px #000;
}
.footer-text h2 {
  margin: 0;
  font-size: 1.5rem;
  letter-spacing: 2px;
}
.footer-text p {
  margin: 8px 0 0 0;
  font-size: 1rem;
  font-style: italic;
}
.footer-links {
  margin-top: 16px;
}
.footer-links a {
  color: #f5c16c;
  margin: 0 12px;
  text-decoration: none;
  transition: color 0.2s;
}
.footer-links a:hover {
  color: #fff;
  text-shadow: 0 0 8px #f5c16c;
}
</style>