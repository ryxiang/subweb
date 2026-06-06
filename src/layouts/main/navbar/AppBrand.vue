<template>
  <div class="brand-wrap">
    <router-link to="/" class="brand-link" aria-label="返回首页">
      <span class="brand-mark" aria-hidden="true">
        <svg viewBox="0 0 64 64">
          <path d="M17 20h27" class="line line-cyan" />
          <path d="m40 11 10 9-10 9" class="line arrow-cyan" />
          <path d="M47 44H20" class="line line-green" />
          <path d="m24 35-10 9 10 9" class="line arrow-green" />
          <path d="M24 31c0-6 4-10 9-10 3 0 6 1 8 3" class="line line-core" />
          <path d="M40 33c0 6-4 10-9 10-3 0-6-1-8-3" class="line line-core" />
        </svg>
      </span>
      <span class="brand-text">{{ siteName }}</span>
    </router-link>
    <button
      class="menu-toggle"
      type="button"
      :aria-expanded="$store.state.style.main.isCollapsed"
      aria-label="打开导航菜单"
      @click="$store.commit('MAIN_LAYOUT_MENU_EXPAND')"
    >
      <svg viewBox="0 0 24 24" aria-hidden="true">
        <path d="M4 7h16M4 12h16M4 17h16" />
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  name: 'AppBrand',
  data() {
    return {
      siteName: '',
    };
  },
  created() {
    this.siteName = window.config.siteName;
  },
};
</script>

<style scoped>
.brand-wrap,
.brand-link {
  display: flex;
  min-width: 0;
  align-items: center;
}

.brand-wrap {
  gap: 10px;
}

.brand-link {
  gap: 11px;
  color: var(--text-primary);
  text-decoration: none;
}

.brand-mark {
  display: grid;
  width: 43px;
  height: 43px;
  flex: 0 0 auto;
  place-items: center;
  overflow: hidden;
  background: linear-gradient(145deg, rgba(15, 23, 42, 0.96), rgba(30, 41, 59, 0.94));
  border: 1px solid rgba(148, 163, 184, 0.24);
  border-radius: 13px;
  box-shadow:
    0 10px 22px rgba(2, 132, 199, 0.16),
    0 5px 12px rgba(101, 163, 13, 0.12);
}

.brand-mark svg {
  width: 34px;
  height: 34px;
  fill: none;
}

.line {
  stroke-width: 5;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.line-cyan {
  stroke: #38bdf8;
}

.arrow-cyan {
  stroke: #67e8f9;
}

.line-green {
  stroke: #34d399;
}

.arrow-green {
  stroke: #bef264;
}

.line-core {
  stroke: #f8fafc;
  stroke-width: 4;
}

.brand-text {
  overflow: hidden;
  font-size: 1rem;
  font-weight: 700;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.menu-toggle {
  display: none;
  width: 42px;
  height: 42px;
  padding: 10px;
  color: var(--text-primary);
  cursor: pointer;
  background: var(--control-bg);
  border: 1px solid var(--control-border);
  border-radius: 999px;
}

.menu-toggle svg {
  width: 100%;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.9;
  stroke-linecap: round;
}

@media (max-width: 720px) {
  .brand-wrap {
    width: 100%;
    justify-content: space-between;
  }

  .brand-mark {
    width: 39px;
    height: 39px;
    border-radius: 12px;
  }

  .brand-mark svg {
    width: 31px;
    height: 31px;
  }

  .brand-text {
    max-width: 210px;
  }

  .menu-toggle {
    display: inline-grid;
    flex: 0 0 auto;
    place-items: center;
  }
}
</style>
