<template>
  <div class="nav-menu" :class="{ open: $store.state.style.main.isCollapsed }">
    <div class="mobile-menu-head">
      <span>导航</span>
      <button type="button" aria-label="关闭导航菜单" @click="$store.commit('MAIN_LAYOUT_MENU_EXPAND')">
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <path d="m6 6 12 12M18 6 6 18" />
        </svg>
      </button>
    </div>
    <ul>
      <li v-for="item in navBarItem" :key="`${item.title}-${item.link}`">
        <a :href="item.link" :target="item.target" :rel="item.target === '_blank' ? 'noopener noreferrer' : null">
          {{ item.title }}
        </a>
      </li>
    </ul>
  </div>
  <div
    v-if="$store.state.style.main.isCollapsed"
    class="menu-overlay"
    aria-hidden="true"
    @click="collapsedMenu"
  ></div>
</template>

<script>
export default {
  name: 'NavMenu',
  data() {
    return {
      navBarItem: [],
    };
  },
  created() {
    this.navBarItem = window.config.menuItem || [];
  },
  methods: {
    collapsedMenu() {
      this.$store.commit('MAIN_LAYOUT_MENU_EXPAND');
    },
  },
};
</script>

<style scoped>
.nav-menu ul {
  display: flex;
  align-items: center;
  gap: 6px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.nav-menu a {
  display: inline-flex;
  min-height: 40px;
  align-items: center;
  padding: 9px 13px;
  color: var(--text-secondary);
  font-size: 0.88rem;
  font-weight: 700;
  text-decoration: none;
  border-radius: 999px;
  transition:
    color 0.2s ease,
    background 0.2s ease,
    transform 0.2s ease;
}

.nav-menu a:hover {
  color: var(--text-primary);
  background: var(--control-hover);
  transform: translateY(-1px);
}

.mobile-menu-head,
.menu-overlay {
  display: none;
}

@media (max-width: 720px) {
  .nav-menu {
    position: fixed;
    top: 0;
    right: max(0px, calc(100% - 100vw));
    z-index: 120;
    display: none;
    width: min(320px, calc(100vw - 42px));
    height: 100vh;
    height: 100svh;
    padding: 18px;
    background: var(--surface-strong);
    border-left: 1px solid var(--surface-border);
    box-shadow: -24px 0 60px rgba(15, 23, 42, 0.24);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
  }

  .nav-menu.open {
    display: block;
  }

  .mobile-menu-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 4px 2px 16px;
    color: var(--text-primary);
    font-weight: 700;
    border-bottom: 1px solid var(--inner-border);
  }

  .mobile-menu-head button {
    display: grid;
    width: 40px;
    height: 40px;
    padding: 9px;
    color: var(--text-primary);
    cursor: pointer;
    background: var(--control-bg);
    border: 1px solid var(--control-border);
    border-radius: 999px;
    place-items: center;
  }

  .mobile-menu-head svg {
    width: 100%;
    fill: none;
    stroke: currentColor;
    stroke-width: 1.9;
    stroke-linecap: round;
  }

  .nav-menu ul {
    align-items: stretch;
    flex-direction: column;
    gap: 7px;
    padding-top: 16px;
  }

  .nav-menu a {
    width: 100%;
    min-height: 46px;
    padding-inline: 15px;
    background: var(--surface-soft);
    border: 1px solid var(--inner-border);
  }

  .menu-overlay {
    position: fixed;
    inset: 0;
    z-index: 110;
    display: block;
    padding: 0;
    cursor: default;
    background: rgba(2, 6, 23, 0.46);
    border: 0;
  }

}
</style>
