<template>
  <div class="about">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <div class="hero-text">
          <h1>About Me</h1>
          <p class="hero-subtitle">
            Passionate developer creating innovative solutions and bringing ideas to life through
            code.
          </p>
        </div>
        <div class="hero-image">
          <img src="/images/profile.jpeg" alt="Ralph Juancho Villaluz" />
        </div>
      </div>
    </section>

    <!-- Main Content -->
    <section class="content">
      <div class="container">
        <!-- Introduction -->
        <div class="intro">
          <h2>Hi, I'm Ralph Juancho</h2>
          <p>
            I'm a passionate full-stack developer with a love for creating clean, efficient, and
            user-friendly applications. With experience in modern web technologies, I enjoy turning
            complex problems into simple, beautiful solutions.
          </p>
          <p>
            When I'm not coding, you can find me exploring new technologies, contributing to
            open-source projects, or sharing knowledge with the developer community.
          </p>
        </div>

        <!-- Skills Section -->
        <div class="skills">
          <h3>Technical Skills</h3>
          <div class="skills-grid">
            <div class="skill-category">
              <h4>Frontend</h4>
              <div class="skill-tags">
                <span class="skill-tag">Vue.js</span>
                <span class="skill-tag">React</span>
                <span class="skill-tag">TypeScript</span>
                <span class="skill-tag">JavaScript</span>
                <span class="skill-tag">HTML5</span>
                <span class="skill-tag">CSS3</span>
              </div>
            </div>
            <div class="skill-category">
              <h4>Backend</h4>
              <div class="skill-tags">
                <span class="skill-tag">Node.js</span>
                <span class="skill-tag">Python</span>
                <span class="skill-tag">Express</span>
                <span class="skill-tag">PostgreSQL</span>
                <span class="skill-tag">MongoDB</span>
              </div>
            </div>
            <div class="skill-category">
              <h4>Tools & Others</h4>
              <div class="skill-tags">
                <span class="skill-tag">Git</span>
                <span class="skill-tag">Docker</span>
                <span class="skill-tag">AWS</span>
                <span class="skill-tag">Figma</span>
                <span class="skill-tag">Vercel</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Experience Timeline -->
        <div class="experience">
          <h3>Experience</h3>
          <div class="timeline">
            <div class="timeline-item">
              <div class="timeline-date">2023 - Present</div>
              <div class="timeline-content">
                <h4>Senior Frontend Developer</h4>
                <p class="company">Tech Company Inc.</p>
                <p>
                  Leading frontend development for web applications, mentoring junior developers,
                  and implementing modern development practices.
                </p>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-date">2021 - 2023</div>
              <div class="timeline-content">
                <h4>Full Stack Developer</h4>
                <p class="company">Startup Solutions</p>
                <p>
                  Developed end-to-end web applications using modern frameworks, collaborated with
                  design teams, and optimized application performance.
                </p>
              </div>
            </div>
            <div class="timeline-item">
              <div class="timeline-date">2020 - 2021</div>
              <div class="timeline-content">
                <h4>Junior Developer</h4>
                <p class="company">Web Agency</p>
                <p>
                  Built responsive websites and web applications, learned best practices, and
                  contributed to various client projects.
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- Education -->
        <div class="education">
          <h3>Education</h3>
          <div class="education-item">
            <h4>Bachelor of Science in Computer Science</h4>
            <p class="university">University Name</p>
            <p class="graduation-year">Graduated: 2020</p>
          </div>
        </div>

        <!-- Personal Interests -->
        <div class="interests">
          <h3>When I'm Not Coding</h3>
          <div class="interests-grid">
            <div class="interest-item">
              <h4>🎸 Music</h4>
              <p>Playing guitar and discovering new artists</p>
            </div>
            <div class="interest-item">
              <h4>📚 Learning</h4>
              <p>Always exploring new technologies and frameworks</p>
            </div>
            <div class="interest-item">
              <h4>🏃‍♂️ Fitness</h4>
              <p>Running and staying active</p>
            </div>
            <div class="interest-item">
              <h4>✈️ Travel</h4>
              <p>Exploring new places and cultures</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.about {
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 6rem 0 4rem;
  margin-top: -1rem;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 4rem;
  align-items: center;
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.hero-subtitle {
  font-size: 1.25rem;
  opacity: 0.9;
  line-height: 1.6;
}

.hero-image img {
  width: 100%;
  height: 400px;
  object-fit: cover;
  border-radius: 12px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
}

/* Content Section */
.content {
  padding: 4rem 0;
}

.intro {
  margin-bottom: 4rem;
}

.intro h2 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  color: var(--color-text);
}

.intro p {
  font-size: 1.125rem;
  line-height: 1.7;
  color: var(--color-text);
  margin-bottom: 1rem;
}

/* Skills Section */
.skills {
  margin-bottom: 4rem;
}

.skills h3 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--color-text);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.skill-category h4 {
  font-size: 1.25rem;
  margin-bottom: 1rem;
  color: var(--color-text);
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.skill-tag {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 500;
}

/* Experience Timeline */
.experience {
  margin-bottom: 4rem;
}

.experience h3 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--color-text);
}

.timeline {
  position: relative;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.timeline-item {
  position: relative;
  margin-bottom: 2rem;
  padding-left: 2rem;
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: -6px;
  top: 0;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.timeline-date {
  font-weight: 600;
  color: #667eea;
  margin-bottom: 0.5rem;
}

.timeline-content h4 {
  font-size: 1.25rem;
  margin-bottom: 0.25rem;
  color: var(--color-text);
}

.company {
  font-weight: 600;
  color: #764ba2;
  margin-bottom: 0.5rem;
}

.timeline-content p:last-child {
  color: var(--color-text);
  line-height: 1.6;
}

/* Education */
.education {
  margin-bottom: 4rem;
}

.education h3 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--color-text);
}

.education-item h4 {
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
  color: var(--color-text);
}

.university {
  font-weight: 600;
  color: #667eea;
  margin-bottom: 0.25rem;
}

.graduation-year {
  color: var(--color-text);
}

/* Interests */
.interests h3 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--color-text);
}

.interests-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.interest-item {
  background: var(--color-background-soft);
  padding: 1.5rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
}

.interest-item h4 {
  font-size: 1.125rem;
  margin-bottom: 0.5rem;
  color: var(--color-text);
}

.interest-item p {
  color: var(--color-text);
  line-height: 1.5;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero {
    padding: 4rem 0 3rem;
  }

  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .hero h1 {
    font-size: 2.5rem;
  }

  .hero-image {
    order: -1;
  }

  .hero-image img {
    height: 300px;
  }

  .container {
    padding: 0 1rem;
  }

  .content {
    padding: 3rem 0;
  }

  .intro h2 {
    font-size: 2rem;
  }

  .skills h3,
  .experience h3,
  .education h3,
  .interests h3 {
    font-size: 1.5rem;
  }

  .skills-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .interests-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: 3rem 0 2rem;
  }

  .hero h1 {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1.125rem;
  }

  .timeline {
    padding-left: 1.5rem;
  }

  .timeline-item {
    padding-left: 1.5rem;
  }
}
</style>
