<script setup lang="ts">
import HeroSection from './HeroSection.vue'
import StatsSection from './StatsSection.vue'

// Updated props to handle tech objects with icons
defineProps<{
  yearsExperience: number
  stats: Array<{ value: string; label: string }>
  specialties: string[]
  test: string[]
  featuredProjects: Array<{ title: string; description: string }>
  backendTech: Array<{ name: string; icon: string }>
  frontendTech: Array<{ name: string; icon: string }>
  toolsTech: Array<{ name: string; icon: string }>
  contactLinks: Array<{ type: string; url: string; label: string }>
}>()

// Events - emit to parent
const emit = defineEmits<{
  downloadResume: []
  viewProjects: []
}>()
</script>

<template>
  <div class="portfolio-landing">
    <!-- Hero Section -->
    <HeroSection
      title="Ralph Juancho Villaluz"
      subtitle="Full-Stack Developer & Technology Enthusiast"
      :description="`Building end-to-end web solutions with ${yearsExperience} year of experience across multiple technologies. Passionate about creating scalable applications from frontend to backend.`"
      :years-experience="yearsExperience"
      @view-projects="emit('viewProjects')"
      @download-resume="emit('downloadResume')"
    />

    <!-- Stats Section -->
    <StatsSection :stats="stats" />

    <!-- Content Grid -->
    <div class="content-grid">
      <!-- What I Do Card -->
      <div class="content-card what-i-do">
        <div class="card-header">
          <div class="card-icon">💻</div>
          <h3>What I Do</h3>
        </div>
        <div class="card-body">
          <p>
            Developing complete web solutions from database design to user interfaces, leveraging
            modern technologies for optimal performance.
          </p>
          <div class="specialties-grid">
            <div
              class="specialty-item"
              v-for="specialty in specialties.slice(0, 4)"
              :key="specialty"
            >
              {{ specialty }}
            </div>
          </div>
        </div>
      </div>

      <!-- Featured Projects Card -->
      <div class="content-card featured-projects">
        <div class="card-header">
          <div class="card-icon">🚀</div>
          <h3>Featured Work</h3>
        </div>
        <div class="card-body">
          <div class="projects-grid">
            <div
              v-for="project in featuredProjects.slice(0, 2)"
              :key="project.title"
              class="project-item"
            >
              <h4>{{ project.title }}</h4>
              <p>{{ project.description }}</p>
            </div>
          </div>
          <router-link to="/projects" class="view-all-btn">View All Projects</router-link>
        </div>
      </div>

      <!-- Backend Technologies Card -->
      <div class="content-card backend-tech">
        <div class="card-header">
          <div class="card-icon">⚙️</div>
          <h3>Backend & Databases</h3>
        </div>
        <div class="card-body">
          <p>Server-side technologies, APIs, and database management systems I work with.</p>
          <div class="tech-grid">
            <div v-for="tech in backendTech.slice(0, 6)" :key="tech.name" class="tech-tag">
              <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
              <span>{{ tech.name }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Frontend Technologies Card -->
      <div class="content-card frontend-tech">
        <div class="card-header">
          <div class="card-icon">🎨</div>
          <h3>Frontend & UI</h3>
        </div>
        <div class="card-body">
          <p>
            Modern frontend frameworks, libraries, and styling technologies for creating engaging
            user experiences.
          </p>
          <div class="tech-grid">
            <div v-for="tech in frontendTech.slice(0, 6)" :key="tech.name" class="tech-tag">
              <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
              <span>{{ tech.name }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Tools & Workflow Card -->
      <div class="content-card tools-tech">
        <div class="card-header">
          <div class="card-icon">🛠️</div>
          <h3>DevOps & Tools</h3>
        </div>
        <div class="card-body">
          <p>
            Development tools, version control, deployment platforms, and workflow optimization
            technologies.
          </p>
          <div class="tech-grid">
            <div v-for="tech in toolsTech.slice(0, 6)" :key="tech.name" class="tech-tag">
              <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
              <span>{{ tech.name }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Contact Card -->
      <div class="content-card contact-card">
        <div class="card-header">
          <div class="card-icon">📧</div>
          <h3>Let's Build Together</h3>
        </div>
        <div class="card-body">
          <p>
            Ready to bring your full-stack project to life? Let's discuss your vision and create
            something amazing!
          </p>
          <div class="contact-grid">
            <a
              v-for="link in contactLinks"
              :key="link.type"
              :href="link.url"
              :class="`contact-btn ${link.type}`"
              target="_blank"
              rel="noopener"
            >
              {{ link.label }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.portfolio-landing {
  max-width: 1200px;
  margin: 0 auto;
}

/* Content Grid */
.content-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin: 3rem 0;
  padding: 0 1rem;
}

/* Content Cards */
.content-card {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  border: 1px solid #e2e8f0;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.content-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
}

/* Card Header */
.card-header {
  padding: 2rem 2rem 1rem;
  border-bottom: 1px solid #f1f5f9;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.card-icon {
  font-size: 2rem;
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  font-size: 1.5rem;
}

.card-header h3 {
  font-size: 1.4rem;
  font-weight: 600;
  color: #2d3748;
  margin: 0;
}

/* Card Body */
.card-body {
  padding: 1rem 2rem 2rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.card-body p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

/* Specialties Grid */
.specialties-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 0.75rem;
}

.specialty-item {
  background: #f8fafc;
  padding: 0.75rem;
  border-radius: 8px;
  text-align: center;
  font-size: 0.85rem;
  font-weight: 500;
  color: #4a5568;
  border: 2px solid transparent;
  transition: all 0.3s ease;
}

.specialty-item:hover {
  border-color: #667eea;
  background: #eef2ff;
  color: #667eea;
}

/* Projects Grid */
.projects-grid {
  display: grid;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.project-item {
  padding: 1rem;
  background: #f8fafc;
  border-radius: 8px;
  border-left: 4px solid #667eea;
}

.project-item h4 {
  color: #2d3748;
  margin-bottom: 0.5rem;
  font-weight: 600;
  font-size: 0.95rem;
}

.project-item p {
  color: #666;
  font-size: 0.85rem;
  margin: 0;
  line-height: 1.4;
}

/* Tech Categories */
.tech-categories {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.tech-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.tech-label {
  font-weight: 600;
  color: #4a5568;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

/* Tech Grid for individual tech cards */
.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  gap: 0.8rem;
  justify-content: center;
  align-items: center;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.8rem 1rem;
  border-radius: 12px;
  font-size: 0.85rem;
  font-weight: 500;
  transition: all 0.3s ease;
  text-align: center;
  width: 100%;
  height: 65px;
  display: flex;
  flex-direction: row; /* Changed from column to row */
  align-items: center;
  justify-content: center; /* Center the content horizontally */
  gap: 0.5rem; /* Space between icon and text */
  min-height: 50px; /* Reduced height since we're going horizontal */
}

.tech-icon {
  width: 20px; /* Slightly smaller for side-by-side layout */
  height: 20px;
  filter: brightness(0) invert(1); /* Makes SVG icons white */
  transition: transform 0.3s ease;
  flex-shrink: 0; /* Prevents icon from shrinking */
}

.tech-tag:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
}

.tech-tag:hover .tech-icon {
  transform: scale(1.1);
}

/* Specific styling for different tech cards */
.backend-tech .tech-tag {
  background: linear-gradient(135deg, #48bb78 0%, #38a169 100%);
}

.frontend-tech .tech-tag {
  background: linear-gradient(135deg, #ed8936 0%, #dd6b20 100%);
}

.tools-tech .tech-tag {
  background: linear-gradient(135deg, #805ad5 0%, #6b46c1 100%);
}

/* Contact Grid */
.contact-grid {
  display: grid;
  gap: 0.75rem;
}

.contact-btn {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  font-size: 0.9rem;
}

.contact-icon {
  font-size: 1.2rem;
}

.contact-btn.email {
  background: #fee2e2;
  color: #dc2626;
}

.contact-btn.linkedin {
  background: #dbeafe;
  color: #2563eb;
}

.contact-btn.github {
  background: #f3f4f6;
  color: #374151;
}

.contact-btn:hover {
  transform: translateX(5px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

/* View All Button */
.view-all-btn {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  text-align: center;
  transition: all 0.3s ease;
  margin-top: auto;
}

.view-all-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
}

/* Timeline Styles */
.timeline-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-dot {
  width: 12px;
  height: 12px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 50%;
  margin-top: 0.3rem;
  flex-shrink: 0;
}

.timeline-content h4 {
  color: #2d3748;
  margin-bottom: 0.3rem;
  font-weight: 600;
  font-size: 0.95rem;
}

.timeline-content p {
  color: #666;
  font-size: 0.85rem;
  margin: 0;
  line-height: 1.4;
}

/* Service Grid Styles */
.service-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 1rem;
}

.service-item {
  text-align: center;
  padding: 1rem;
  background: #f8fafc;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.service-item:hover {
  background: #eef2ff;
  transform: translateY(-2px);
}

.service-icon {
  font-size: 1.5rem;
  display: block;
  margin-bottom: 0.5rem;
}

.service-item h4 {
  color: #2d3748;
  margin-bottom: 0.5rem;
  font-weight: 600;
  font-size: 0.9rem;
}

.service-item p {
  color: #666;
  font-size: 0.8rem;
  margin: 0;
  line-height: 1.3;
}

/* Responsive Design */
@media (max-width: 768px) {
  .content-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin: 2rem 0;
  }

  .card-header {
    padding: 1.5rem 1.5rem 1rem;
  }

  .card-body {
    padding: 1rem 1.5rem 1.5rem;
  }

  .specialties-grid {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  }

  .service-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .tech-grid {
    grid-template-columns: repeat(
      auto-fit,
      minmax(120px, 1fr)
    ); /* Increased min width for side-by-side */
  }

  .tech-tag {
    padding: 0.6rem 0.8rem;
    min-height: 45px;
    font-size: 0.8rem;
  }

  .tech-icon {
    width: 18px;
    height: 18px;
  }
}

@media (max-width: 480px) {
  .card-header {
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
  }

  .specialties-grid {
    grid-template-columns: 1fr 1fr;
  }

  .tech-tags {
    justify-content: center;
  }

  .service-grid {
    grid-template-columns: 1fr;
  }

  .timeline-item {
    gap: 0.75rem;
  }

  .tech-grid {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  }

  .tech-tag {
    padding: 0.5rem 0.6rem;
    gap: 0.3rem;
    font-size: 0.75rem;
  }

  .tech-icon {
    width: 16px;
    height: 16px;
  }
}
</style>
