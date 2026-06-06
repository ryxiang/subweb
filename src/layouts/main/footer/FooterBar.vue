<template>
  <footer class="site-footer">
    <span>Subconverter Web</span>
    <span class="footer-dot" aria-hidden="true"></span>
    <a href="https://github.com/Aethersailor/subweb" target="_blank" rel="noopener noreferrer">Aethersailor/subweb</a>
  </footer>
</template>

<script>
export default {
  name: 'FooterBar',
};
</script>

<style scoped>
.site-footer {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 26px 18px 30px;
  color: var(--text-muted);
  font-size: 0.84rem;
}

.site-footer a {
  color: var(--text-secondary);
  font-weight: 700;
  text-decoration: none;
}

.site-footer a:hover {
  color: var(--accent-blue);
}

.footer-dot {
  width: 5px;
  height: 5px;
  background: var(--accent-gradient);
  border-radius: 999px;
}

@media (max-width: 440px) {
  .site-footer {
    flex-wrap: wrap;
  }
}
</style>
