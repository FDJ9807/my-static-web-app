<template>
  <div class="min-h-screen bg-slate-950 text-slate-100">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-slate-950/80 backdrop-blur-sm border-b border-slate-800 z-50">
      <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
        <a href="#" class="text-xl font-bold text-emerald-400">{ 'DevPortfolio' }</a>
        <div class="flex gap-6">
          <a href="#about" class="text-slate-300 hover:text-emerald-400 transition-colors">Sobre mí</a>
          <a href="#skills" class="text-slate-300 hover:text-emerald-400 transition-colors">Skills</a>
          <a href="#projects" class="text-slate-300 hover:text-emerald-400 transition-colors">Proyectos</a>
          <a href="#contact" class="text-slate-300 hover:text-emerald-400 transition-colors">Contacto</a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="pt-32 pb-20 px-6">
      <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-12 items-center">
        <div>
          <h1 class="text-5xl md:text-6xl font-bold mb-4 text-balance">
            Hola, soy
            <span class="text-emerald-400">{{ developerName }}</span>
          </h1>
          <p class="text-xl text-slate-400 mb-6 leading-relaxed">
            {{ title }}
          </p>
          <p class="text-slate-300 mb-8 leading-relaxed">
            {{ description }}
          </p>
          <div class="flex gap-4">
            <a 
              href="#projects" 
              class="px-6 py-3 bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-semibold rounded-lg transition-colors"
            >
              Ver Proyectos
            </a>
            <a 
              href="#contact" 
              class="px-6 py-3 border border-slate-700 hover:border-emerald-500 text-slate-100 font-semibold rounded-lg transition-colors"
            >
              Contactar
            </a>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="relative w-64 h-64 rounded-full bg-gradient-to-br from-emerald-500 to-cyan-500 p-1">
            <div class="w-full h-full rounded-full bg-slate-900 flex items-center justify-center">
              <User :size="120" class="text-slate-600" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-20 px-6 bg-slate-900/50">
      <div class="max-w-7xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-12 text-emerald-400">Sobre mí</h2>
        <div class="grid md:grid-cols-2 gap-12">
          <div>
            <p class="text-slate-300 mb-6 leading-relaxed">
              Soy un desarrollador apasionado por crear soluciones innovadoras y eficientes. 
              Me especializo en desarrollo web moderno utilizando las últimas tecnologías.
            </p>
            <p class="text-slate-300 leading-relaxed">
              Con experiencia en proyectos de diferentes escalas, desde startups hasta grandes corporaciones, 
              siempre busco entregar código de calidad que genere impacto real.
            </p>
          </div>
          <div class="space-y-4">
            <div class="flex items-center gap-3">
              <Mail class="text-emerald-400" :size="20" />
              <span class="text-slate-300">developer@email.com</span>
            </div>
            <div class="flex items-center gap-3">
              <MapPin class="text-emerald-400" :size="20" />
              <span class="text-slate-300">Ciudad, País</span>
            </div>
            <div class="flex items-center gap-3">
              <Briefcase class="text-emerald-400" :size="20" />
              <span class="text-slate-300">Full Stack Developer</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20 px-6">
      <div class="max-w-7xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-12 text-emerald-400">Skills & Tecnologías</h2>
        <div class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
          <div 
            v-for="skill in skills" 
            :key="skill.name"
            class="p-6 bg-slate-900 border border-slate-800 rounded-lg hover:border-emerald-500 transition-all hover:shadow-lg hover:shadow-emerald-500/10"
          >
            <component :is="skill.icon" class="text-emerald-400 mb-3" :size="32" />
            <h3 class="text-lg font-semibold mb-2">{{ skill.name }}</h3>
            <p class="text-sm text-slate-400">{{ skill.level }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-20 px-6 bg-slate-900/50">
      <div class="max-w-7xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-12 text-emerald-400">Proyectos Destacados</h2>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="project in projects" 
            :key="project.id"
            class="bg-slate-900 border border-slate-800 rounded-lg overflow-hidden hover:border-emerald-500 transition-all hover:shadow-lg hover:shadow-emerald-500/10 group"
          >
            <div class="h-48 bg-slate-800 flex items-center justify-center">
              <Folder class="text-slate-600 group-hover:text-emerald-400 transition-colors" :size="64" />
            </div>
            <div class="p-6">
              <h3 class="text-xl font-semibold mb-2 group-hover:text-emerald-400 transition-colors">
                {{ project.title }}
              </h3>
              <p class="text-slate-400 mb-4 text-sm leading-relaxed">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span 
                  v-for="tech in project.technologies" 
                  :key="tech"
                  class="px-3 py-1 bg-slate-800 text-emerald-400 text-xs rounded-full"
                >
                  {{ tech }}
                </span>
              </div>
              <div class="flex gap-3">
                <a href="#" class="text-slate-400 hover:text-emerald-400 transition-colors">
                  <Github :size="20" />
                </a>
                <a href="#" class="text-slate-400 hover:text-emerald-400 transition-colors">
                  <ExternalLink :size="20" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 px-6">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-emerald-400">Trabajemos Juntos</h2>
        <p class="text-slate-300 mb-12 text-lg leading-relaxed">
          ¿Tienes un proyecto en mente? Me encantaría escuchar tus ideas y colaborar contigo.
        </p>
        <div class="flex flex-wrap justify-center gap-6 mb-12">
          <a 
            href="https://github.com" 
            target="_blank"
            class="flex items-center gap-2 px-6 py-3 bg-slate-900 border border-slate-700 hover:border-emerald-500 rounded-lg transition-colors"
          >
            <Github :size="20" />
            <span>GitHub</span>
          </a>
          <a 
            href="https://linkedin.com" 
            target="_blank"
            class="flex items-center gap-2 px-6 py-3 bg-slate-900 border border-slate-700 hover:border-emerald-500 rounded-lg transition-colors"
          >
            <Linkedin :size="20" />
            <span>LinkedIn</span>
          </a>
          <a 
            href="mailto:developer@email.com"
            class="flex items-center gap-2 px-6 py-3 bg-slate-900 border border-slate-700 hover:border-emerald-500 rounded-lg transition-colors"
          >
            <Mail :size="20" />
            <span>Email</span>
          </a>
        </div>
        <a 
          href="mailto:developer@email.com" 
          class="inline-block px-8 py-4 bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-semibold rounded-lg transition-colors text-lg"
        >
          Enviar Mensaje
        </a>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 px-6 border-t border-slate-800">
      <div class="max-w-7xl mx-auto text-center text-slate-400">
        <p>© {{ currentYear }} {{ developerName }}. Todos los derechos reservados.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { User, Mail, MapPin, Briefcase, Github, Linkedin, ExternalLink, Code, Database, Folder } from 'lucide-vue-next'

const developerName = ref('Juan Pérez')
const title = ref('Desarrollador Full Stack')
const description = ref('Construyo aplicaciones web modernas y escalables que resuelven problemas reales.')

const currentYear = computed(() => new Date().getFullYear())

const skills = ref([
  { name: 'Vue.js', level: 'Avanzado', icon: Code },
  { name: 'React', level: 'Avanzado', icon: Code },
  { name: 'Node.js', level: 'Intermedio', icon: Code },
  { name: 'TypeScript', level: 'Avanzado', icon: Code },
  { name: 'Python', level: 'Intermedio', icon: Code },
  { name: 'PostgreSQL', level: 'Intermedio', icon: Database },
  { name: 'MongoDB', level: 'Intermedio', icon: Database },
  { name: 'Docker', level: 'Básico', icon: Code },
])

const projects = ref([
  {
    id: 1,
    title: 'E-commerce Platform',
    description: 'Plataforma completa de comercio electrónico con carrito de compras, pagos y gestión de inventario.',
    technologies: ['Vue.js', 'Node.js', 'MongoDB'],
  },
  {
    id: 2,
    title: 'Task Management App',
    description: 'Aplicación de gestión de tareas con colaboración en tiempo real y notificaciones.',
    technologies: ['React', 'Firebase', 'Tailwind'],
  },
  {
    id: 3,
    title: 'Weather Dashboard',
    description: 'Dashboard interactivo que muestra datos meteorológicos con visualizaciones y mapas.',
    technologies: ['Vue.js', 'API REST', 'Charts.js'],
  },
  {
    id: 4,
    title: 'Blog Platform',
    description: 'Sistema de blog con editor markdown, comentarios y sistema de autenticación.',
    technologies: ['Next.js', 'PostgreSQL', 'Prisma'],
  },
  {
    id: 5,
    title: 'Portfolio Generator',
    description: 'Herramienta para generar portafolios personalizados con plantillas y temas.',
    technologies: ['Vue.js', 'Tailwind', 'Vite'],
  },
  {
    id: 6,
    title: 'Chat Application',
    description: 'Aplicación de mensajería en tiempo real con salas de chat y mensajes privados.',
    technologies: ['Socket.io', 'Express', 'Vue.js'],
  },
])
</script>