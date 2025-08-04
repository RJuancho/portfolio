<script setup lang="ts">
import TheWelcome from '../components/sections/TheWelcome.vue'
import { useRouter } from 'vue-router'

const router = useRouter()

// Page-level data and logic
const contactEmail = 'rjvillaluz@example.com'
const yearsExperience = 2

// Page-level actions
const downloadResume = () => {
  window.open('/resume.pdf', '_blank')
}

const viewProjects = () => {
  router.push('/projects')
}

// Portfolio data
const stats = [
  { value: `${yearsExperience}+`, label: 'Years Experience' },
  { value: '50+', label: 'Projects Completed' },
  { value: '100%', label: 'Client Satisfaction' },
]

const specialties = [
  'Web Applications',
  'API Development',
  'E-commerce Solutions',
  'WordPress Development',
]

const test = ['API Development', 'E-commerce Solutions', 'WordPress Development']

const featuredProjects = [
  {
    title: 'E-commerce Platform',
    description: 'Full-stack Laravel application with payment integration',
  },
  {
    title: 'Business Management System',
    description: 'Custom PHP solution for inventory and customer management',
  },
]

// Split tech stack into separate categories - all with icons
const backendTech = [
  { name: 'PHP', icon: '/icons/php.svg' },
  { name: 'Java', icon: '/icons/java.svg' },
  { name: 'MySQL', icon: '/icons/mysql.svg' },
  { name: 'PostgreSQL', icon: '/icons/postgresql.svg' },
  { name: 'Node.js', icon: '/icons/nodejs.svg' },
  { name: 'MongoDB', icon: '/icons/mongodb.svg' },
]

const frontendTech = [
  { name: 'JavaScript', icon: '/icons/javascript.svg' },
  { name: 'Vue.js', icon: '/icons/vue.svg' },
  { name: 'React', icon: '/icons/react.svg' },
  { name: 'Tailwind CSS', icon: '/icons/tailwindcss.svg' },
]
const toolsTech = [
  { name: 'Git', icon: '/icons/git.svg' },
  { name: 'VS Code', icon: '/icons/vscode.png' },
  { name: 'Composer', icon: '/icons/composer.svg' },
  { name: 'Postman', icon: '/icons/postman.svg' },
]

const contactLinks = [
  { type: 'email', url: `mailto:${contactEmail}`, label: '📧 Email Me' },
  { type: 'linkedin', url: 'https://linkedin.com/in/yourprofile', label: '💼 LinkedIn' },
  { type: 'github', url: 'https://github.com/yourusername', label: '🔗 GitHub' },
]
</script>

<template>
  <main>
    <TheWelcome
      :years-experience="yearsExperience"
      :stats="stats"
      :specialties="specialties"
      :featured-projects="featuredProjects"
      :backend-tech="backendTech"
      :frontend-tech="frontendTech"
      :tools-tech="toolsTech"
      :contact-links="contactLinks"
      :test="test"
      @download-resume="downloadResume"
      @view-projects="viewProjects"
    />
  </main>
</template>
