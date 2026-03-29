<template>
  <div class="project-card">
    <div class="project-header">
      <div class="tech-badge" :class="technology">
        {{ technologyDisplayName }}
      </div>
    </div>

    <h3 class="project-title">{{ title }}</h3>
    <p class="project-description">{{ description }}</p>

    <div class="project-links">
      <a
        :href="siteLink"
        target="_blank"
        rel="noopener noreferrer"
        class="project-link"
        :class="{ disabled: siteLink === '#' }"
      >
        <span>Visitar Site</span>
      </a>

      <a
        :href="githubLink"
        target="_blank"
        rel="noopener noreferrer"
        class="project-link"
        :class="{ disabled: githubLink === '#' }"
      >
        <span>GitHub</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProjectCard',
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    technology: {
      type: String,
      required: true,
      validator: (value) => ['vue', 'javascript'].includes(value),
    },
    siteLink: {
      type: String,
      default: '#',
    },
    githubLink: {
      type: String,
      default: '#',
    },
  },
  data() {
    return {
      visitSiteIcon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
        <polyline points="15 3 21 3 21 9"></polyline>
        <line x1="10" y1="14" x2="21" y2="3"></line>
      </svg>`,
      githubIcon: `<svg viewBox="0 0 24 24" fill="currentColor">
        <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
      </svg>`,
    }
  },
  computed: {
    technologyDisplayName() {
      const names = {
        vue: 'Vue.js',
        javascript: 'JavaScript',
      }
      return names[this.technology] || this.technology
    },
  },
}
</script>

<style scoped>
.project-card {
  background: #335766;
  color: whitesmoke;
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 2rem;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.project-card:hover {
  border-color: var(--accent-cyan);
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 217, 255, 0.2);
}

.project-header {
  display: flex;
  justify-content: flex-start;
}

.tech-badge {
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.tech-badge.vue {
  background: rgba(65, 184, 131, 0.15);
  color: #42b883;
  border: 1px solid #42b883;
}

.tech-badge.javascript {
  background: rgba(247, 223, 30, 0.15);
  color: #f7df1e;
  border: 1px solid #f7df1e;
}

.project-title {
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
}

.project-description {
  color: var(--text-secondary);
  line-height: 1.6;
  flex-grow: 1;
  margin: 0;
}

.project-links {
  display: flex;
  gap: 1rem;
  margin-top: 0.5rem;
}

.project-link {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  background: var(--bg-section);
  border: 1px solid var(--border-color);
  border-radius: 8px;
  color: var(--text-primary);
  font-weight: 500;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.project-link svg {
  width: 18px;
  height: 18px;
}

.project-link:not(.disabled):hover {
  transform: translateY(-2px);
}

.project-link.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

@media (max-width: 768px) {
  .project-card {
    padding: 1.5rem;
  }

  .project-title {
    font-size: 1.2rem;
  }

  .project-links {
    flex-direction: column;
  }
}
</style>
