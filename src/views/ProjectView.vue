<script setup lang="ts">
// Project data - you can move this to a separate file later
const projects = [
  {
    id: 1,
    title: 'Launchpad Coworking Voucher System',
    description: 'Full-stack PHP application with user authentication, and admin dashboard.',
    technologies: ['PHP', 'MySQL', 'JavaScript', 'Bootstrap', 'Tailwind Css'],
    image: '/project1.jpg', // Add your project images to public folder
    liveUrl: 'https://example.com',
    githubUrl: 'https://github.com/yourusername/project1',
    featured: true,
  },
  {
    id: 2,
    title: 'Business Management System',
    description:
      'Custom PHP solution for inventory and customer management with reporting features.',
    technologies: ['PHP', 'MySQL', 'jQuery', 'CSS3'],
    image: '/project2.jpg',
    liveUrl: 'https://example.com',
    githubUrl: 'https://github.com/yourusername/project2',
    featured: true,
  },
  {
    id: 3,
    title: 'WordPress Custom Theme',
    description: 'Responsive WordPress theme with custom post types and advanced custom fields.',
    technologies: ['WordPress', 'PHP', 'JavaScript', 'SASS'],
    image: '/project3.jpg',
    liveUrl: 'https://example.com',
    githubUrl: 'https://github.com/yourusername/project3',
    featured: false,
  },
  {
    id: 4,
    title: 'REST API Service',
    description:
      'RESTful API built with Laravel for mobile app backend with authentication and data management.',
    technologies: ['Laravel', 'PHP', 'MySQL', 'JWT'],
    image: '/project4.jpg',
    liveUrl: 'https://api.example.com',
    githubUrl: 'https://github.com/yourusername/project4',
    featured: false,
  },
]

const featuredProjects = projects.filter((project) => project.featured)
const otherProjects = projects.filter((project) => !project.featured)
</script>

<template>
  <div class="projects-page">
    <!-- Page Header -->
    <section class="page-header">
      <h1>My Projects</h1>
      <p>
        A showcase of my recent web development work, from custom applications to WordPress
        solutions.
      </p>
    </section>

    <!-- All Projects Grid -->
    <section class="projects-section">
      <h2>Featured Projects</h2>
      <div class="projects-grid">
        <div
          v-for="project in featuredProjects"
          :key="project.id"
          class="project-card featured-card"
        >
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
            <div class="project-overlay">
              <div class="project-links">
                <a :href="project.liveUrl" target="_blank" rel="noopener" class="btn-primary">
                  View Live
                </a>
                <a :href="project.githubUrl" target="_blank" rel="noopener" class="btn-secondary">
                  GitHub
                </a>
              </div>
            </div>
          </div>
          <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="project-tech">
              <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>

      <h2>Other Projects</h2>
      <div class="projects-grid">
        <div v-for="project in otherProjects" :key="project.id" class="project-card">
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
            <div class="project-overlay">
              <div class="project-links">
                <a :href="project.liveUrl" target="_blank" rel="noopener" class="btn-primary">
                  View Live
                </a>
                <a :href="project.githubUrl" target="_blank" rel="noopener" class="btn-secondary">
                  GitHub
                </a>
              </div>
            </div>
          </div>
          <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="project-tech">
              <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="cta-section">
      <h2>Interested in Working Together?</h2>
      <p>I'm always open to discussing new projects and opportunities.</p>
      <router-link to="/contact" class="cta-button">Get In Touch</router-link>
    </section>
  </div>
</template>

<style scoped>
.projects-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

/* Page Header */
.page-header {
  text-align: center;
  margin-bottom: 4rem;
  padding: 4rem 2rem;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 15px;
}

.page-header h1 {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #2d3748;
}

.page-header p {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
}

/* Section Headers */
h2 {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 2rem;
  color: #667eea;
}

.projects-section {
  margin-bottom: 4rem;
}

.projects-section h2:not(:first-child) {
  margin-top: 4rem;
}

/* Projects Grid - Uniform for all sections */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-bottom: 2rem;
}

/* Project Cards */
.project-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  height: fit-content;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.featured-card {
  border: 2px solid #962aae;
  position: relative;
}

.featured-card::before {
  content: 'Featured';
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: #962aae;
  color: white;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 600;
  z-index: 2;
}

/* Project Image */
.project-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

/* Project Overlay */
.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-links {
  display: flex;
  gap: 1rem;
}

/* Project Content */
.project-content {
  padding: 1.5rem;
}

.project-content h3 {
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #2d3748;
}

.project-content p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1rem;
}

/* Technology Tags */
.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background: #e2e8f0;
  color: #4a5568;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

/* Buttons */
.btn-primary,
.btn-secondary {
  padding: 0.7rem 1.5rem;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  display: inline-block;
}

.btn-primary {
  background: #962aae;
  color: white;
}

.btn-primary:hover {
  background: #77228a;
}

.btn-secondary {
  background: transparent;
  color: white;
  border: 2px solid white;
}

.btn-secondary:hover {
  background: white;
  color: #333;
}

/* Call to Action Section */
.cta-section {
  text-align: center;
  padding: 3rem 2rem;
  background: #f7fafc;
  border-radius: 12px;
}

.cta-section h2 {
  margin-bottom: 1rem;
}

.cta-section p {
  font-size: 1.1rem;
  color: #666;
  margin-bottom: 2rem;
}

.cta-button {
  background: #962aae;
  color: white;
  padding: 1rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
}

.cta-button:hover {
  background: #77228a;
  transform: translateY(-2px);
}

/* Responsive Design */
@media (max-width: 768px) {
  .projects-page {
    padding: 1rem;
  }

  .page-header h1 {
    font-size: 2rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .project-links {
    flex-direction: column;
  }
}

@media (max-width: 480px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-content {
    padding: 1rem;
  }
}
</style>
