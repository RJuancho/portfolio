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

const test = ['Wild Rift', 'API Development', 'E-commerce Solutions', 'WordPress Development']

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

const techStack = {
  backend: ['PHP', 'Laravel', 'MySQL', 'PostgreSQL'],
  frontend: ['JavaScript', 'Vue.js', 'Bootstrap', 'Tailwind CSS'],
  tools: ['Git', 'Composer', 'Docker', 'REST APIs'],
}

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
      :tech-stack="techStack"
      :contact-links="contactLinks"
      :test="test"
      @download-resume="downloadResume"
      @view-projects="viewProjects"
    />
  </main>
</template>
