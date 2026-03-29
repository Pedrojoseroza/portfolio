<script setup>
import { ref, reactive } from 'vue'
import emailjs from '@emailjs/browser'
import ProjectCard from './components/ProjectCard.vue'
// Estado da Categoria de Projetos
const currentCategory = ref('vue')

// Objeto de dados para o formulário (Composition API)
const contactForm = reactive({
  name: '',
  subject: '',
  message: '',
})

const clearForm = () => {
  contactForm.name = ''
  contactForm.subject = ''
  contactForm.message = ''
}

const handleEmailSend = () => {
  const serviceID = 'service_sk0dw5j' // Substituir pelo seu ID
  const templateID = 'template_fw1b32n' // Substituir pelo seu ID
  const publicKey = '7_rYE9tZnGPfK1EyL' // Substituir pela sua Key

  const templateParams = {
    from_name: contactForm.name,
    subject: contactForm.subject,
    message: contactForm.message,
    to_email: 'pedrojs.ol.daroza@gmail.com',
  }

  emailjs.send(serviceID, templateID, templateParams, publicKey).then(
    () => {
      alert('E-mail enviado com sucesso!')
      clearForm()
    },
    (error) => {
      alert('Falha ao enviar e-mail: ' + error.text)
    },
  )
}
</script>

<template>
  <div class="portfolio-wrapper">
    <component is="style">
      @import
      url('https://fonts.googleapis.com/css2?family=Allura&family=Inter:wght@400;600;700&display=swap');
    </component>

    <header class="header">
      <h1 class="logo">
        <a href="#" class="logo-p">P</a>
        <a href="#" class="logo-name">Pedro.Js</a>
      </h1>
      <nav class="nav-menu">
        <ul>
          <li>
            <a href="#home">home</a>
          </li>
          <li>
            <a href="#about">about</a>
          </li>
          <li>
            <a href="#projects">projects</a>
          </li>
          <li>
            <a href="#contacts">contacts</a>
          </li>
        </ul>
      </nav>
    </header>

    <section id="home" class="hero">
      <div class="hero-content">
        <h1 class="glitch-text">
          <span v-for="(char, i) in '<hello-World>'" :key="i" class="hover-char">{{ char }}</span>
        </h1>
        <p class="hero-subtitle">dev em constante evolução</p>
        <h1 class="glitch-text footer-tag">
          <span v-for="(char, i) in '</hello-world>'" :key="i" class="hover-char">{{ char }}</span>
        </h1>
      </div>
    </section>

    <section class="intro section-container">
      <div class="intro-grid">
        <div class="intro-text">
          <h2>Seja bem-vindo ao meu portfólio pessoal!</h2>
          <p>
            Me chamo Pedro José, estou estudando programação para me tornar um desenvolvedor de
            software e estou atualmente cursando o técnico em informática para a internet, oferecido
            no IFC, campus Araquari.
          </p>
          <div class="social-links">
            <ul>
              <li>
                <a href="#" target="_blank"><img src="@/assets/linkedin-seeklogo.svg" alt=""></a>
              </li>
              <li>
                <a href="#" target="_blank"><img src="@/assets/github-seeklogo.svg" alt=""></a>
              </li>
              <li>
                <a href="#" target="_blank"><img src="@/assets/instagram-glyph-seeklogo.svg" alt=""></a>
              </li>
            </ul>
          </div>
        </div>
        <div class="profile-container">
          <div class="white-circle">
            <img src="@/assets/foto_de_perfil.jpg" alt="Foto de Perfil" class="profile-img" />
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="about section-container">
      <div class="about-grid">
        <div class="bio">
          <h2>Sobre Mim:</h2>
          <p>
            Tenho 16 anos, nasci e moro em Joinville, Santa Catarina. Estou cursando o segundo ano
            do ensino médio integrado ao curso técnico de informática para a internet. Curso inglês
            na Wizard, além de espanhol na própria instituição. Costumo ter afinidade em resolver
            problemas com lógica, especialmente focado em resoluções matemáticas.
          </p>
        </div>
        <div class="skills">
          <h2>Tecnologias</h2>
          <div class="tech-icons">
            <img src="@/assets/js-vector.svg" alt="JavaScript" title="JavaScript" />
            <img src="@/assets/vue-vector.svg" alt="Vue.js" title="Vue.js" />
            <img src="@/assets/html-vector.svg" alt="HTML5" title="HTML5" />
            <img src="@/assets/css-vector.svg" alt="CSS3" title="CSS3" />
          </div>
        </div>
      </div>
    </section>

    <section id="projects" class="projects section-container">
      <h2>Projetos:</h2>
      <div class="tabs">
        <button @click="currentCategory = 'vue'" :class="{ active: currentCategory === 'vue' }">
          Vue.js
        </button>
        <button @click="currentCategory = 'js'" :class="{ active: currentCategory === 'js' }">
          JavaScript
        </button>
      </div>

      <div class="projects-grid">
        <template v-if="currentCategory === 'vue'">
          <ProjectCard
            title="Gerador de paletas de cores personalizáveis"
            githubLink="https://github.com/Pedrojoseroza/gerador_de_paletas_de_cores_vue.git"
            siteLink="https://gerador-de-paletas-de-cores-vue.vercel.app/"
          />
        </template>
        <template v-if="currentCategory==='vue'">
          <ProjectCard title="To-do List" siteLink="https://listadeafazeres-peach.vercel.app/" githubLink="https://github.com/Pedrojoseroza/lista_de_afazeres.git">
          </ProjectCard>
        </template>
                <template v-if="currentCategory==='vue'">
          <ProjectCard title="Portfólio" siteLink="https://portfolio-self-kappa-96.vercel.app/" githubLink="https://github.com/Pedrojoseroza/portfolio.git">
          </ProjectCard>
        </template>
        <template v-else>
          <ProjectCard title="Converter texto para binário e vice-versa" siteLink="https://pedrojoseroza.github.io/codigo_binario/" githubLink="https://github.com/Pedrojoseroza/codigo_binario.git" />
        </template>
        <template v-if="currentCategory !== 'vue'">
            <ProjectCard title="Piano online" siteLink="https://pedrojoseroza.github.io/piano_projeto/" githubLink="https://github.com/Pedrojoseroza/piano_projeto.git" />
        </template>
        <template v-if="currentCategory !== 'vue'">
            <ProjectCard title="Fitly: Feito em colaboração" siteLink="https://fitlyapp.com.br/" githubLink="https://github.com/FitlyApp/FitlyApp.git" />
        </template>
      </div>
    </section>

    <section id="contacts" class="contacts section-container">
      <div class="contact-layout">
        <div class="form-wrapper">
          <h2>Contatos:</h2>
          <p>Escreva-me para começarmos uma conversa!</p>
          <form @submit.prevent="handleEmailSend">
            <div class="field">
              <label>Nome:</label>
              <input v-model="contactForm.name" type="text" required />
            </div>
            <div class="field">
              <label>Assunto:</label>
              <input v-model="contactForm.subject" type="text" required />
            </div>
            <div class="field">
              <label>Mensagem:</label>
              <textarea v-model="contactForm.message" rows="5" required></textarea>
            </div>
            <div class="form-btns">
              <button type="button" @click="clearForm" class="btn-clear">Limpar</button>
              <button type="submit" class="btn-send">Enviar</button>
            </div>
          </form>
        </div>

        <div class="contact-info">
          <p><strong>Email:</strong> pedrojs.ol.daroza@gmail.com</p>
          <p>
            <strong>Número:</strong>
            <a href="https://wa.me/5547984669538" target="_blank"> +55 47 98466-9538</a>
          </p>
          <p>
            <strong>Instagram:</strong>
            <a href="https://instagram.com/pedroka_17" target="_blank"> @pedroka_17</a>
          </p>
        </div>
      </div>
    </section>
    <footer class="footer">
      <div class="footer-container">
        <div class="footer-logo"><span class="allura-logo">P</span> Pedro José</div>
        <nav class="footer-nav">
          <a href="#home">home</a>
          <a href="#about">about</a>
          <a href="#contacts">contacts</a>
          <a href="#projects">projects</a>
        </nav>
        <p class="copyright">© 2026 Pedro José. Todos os direitos reservados.</p>
      </div>
    </footer>
  </div>
</template>

<style>
/* Reset e Estilos Globais */
* {
  margin: 0;
  padding: 0;
}
body {
  background-color: #66afcd;
  color: #000;
  font-family: 'Inter', sans-serif;
  scroll-behavior: smooth;
}

/* Estilo Allura para o Logo */
.logo-p {
  font-family: 'Allura', cursive;
  background-color: #66afcd;
  font-size: 2.5rem;
  margin-right: 20px;
  padding: 10px 25px;
  border-radius: 100%;
}
.logo-name {
  color: #fff;
  font-weight: 700;
  font-size: 1.8rem;
  font-family: 'Allura', cursive;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 5%;
  background: #50352a;
  position: sticky;
  top: 0;
  z-index: 1000;
}
.nav-menu ul {
  display: flex;
  align-items: center;
}
.nav-menu ul li {
  list-style-type: none;
}
.nav-menu ul li a {
  color: #fff;
  text-decoration: none;
  margin-left: 2rem;
  text-transform: lowercase;
  font-weight: 600;
}

.nav-menu ul li a:hover {
  color: #2df982;
}

/* Banner Escuro com Efeito de Hover */
.hero {
  height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  background: #000;
}

.glitch-text {
  font-size: 3.5rem;
  letter-spacing: 2px;
}
.hero-subtitle {
  font-size: 1.5rem;
  margin: 1rem 0;
  color: #888;
}
.hero-subtitle:hover {
  transition: font-weight, 3s;
  font-weight: bold;
  color: #2df982;
}

.hover-char {
  color: #fff;
  display: inline-block;
  transition:
    transform 0.3s,
    color 0.3s;
  cursor: default;
}

.hover-char:hover {
  transform: translateY(-10px) scale(1.2);
  color: #ff846e; /* Cor temática do Vue */
}

/* Layout Seções */
.section-container {
  padding: 5rem 10%;
}

.intro-grid,
.about-grid,
.contact-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}
 h2 {
  font-size: 1.5rem;
  margin: 0 0 5px 0;
}
p {
  font-size: 1.2rem;
}
.social-links ul {
  display:flex;
  gap: 20px;
  margin: 10px 0;
}
.social-links ul li {
  margin: 20px 0;
  list-style-type: none;
}
.social-links ul li a img {
  width: 5vw;
}
/* Círculo da Foto */

.white-circle img {
  border-radius: 50%;
  width: 400px;
  height: 400px;
  background-position: cover;
}
.profile-img {
  width: 100%;
  height: auto;
}

/* Tecnologia Icons */

.tech-icons {
  display: grid;
  grid-template-columns: repeat(2, 2fr);
  gap: 2rem;
  margin-top: 1.5rem;
}
.tech-icons img {
  width: 80px;
  height: 80px;
}
/* Projetos */
.tabs {
  margin: 2rem 0;
  display: flex;
  gap: 1rem;
}
.tabs button {
  background: none;
  border: 1px solid #fff;
  color: #fff;
  padding: 0.5rem 1.5rem;
  cursor: pointer;
  border-radius: 4px;
}
.tabs button.active {
  background: #fff;
  color: #000;
}

.projects-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

/* Formulário */
.field {
  margin-bottom: 1.5rem;
  display: flex;
  flex-direction: column;
}
.field label {
  margin-bottom: 0.5rem;
  font-weight: 600;
}
.field input,
.field textarea {
  background: #111;
  border: 1px solid #333;
  color: #fff;
  padding: 12px;
  border-radius: 4px;
}
.contact-info p{
  margin: 20px 0;
}
.contact-info a:hover {
  color:blue;
  text-decoration: underline;
}
.form-btns {
  display: flex;
  gap: 1rem;
}
.btn-send {
  background: #fff;
  border: none;
  padding: 10px 30px;
  cursor: pointer;
  font-weight: 700;
}
.btn-clear {
  background: none;
  border: 1px solid #fff;
  color: #fff;
  padding: 10px 30px;
  cursor: pointer;
}
.footer {
  background-color: #50352a;
  border-top: 1px solid #222;
  padding: 40px 8%;
  margin-top: 50px;
  color: #fff;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}
.footer .allura-logo {
  background-color: #66afcd;
  font-size: 2rem;
  margin-right: 20px;
  padding: 5px 15px;
  border-radius: 100%;
  font-family: "Allura", cursive;
}
.footer-nav {
  display: flex;
  gap: 30px;
}

.footer-nav a {
  color: #888;
  text-decoration: none;
  font-size: 0.9rem;
  text-transform: lowercase;
  transition: color 0.3s;
}

.footer-nav a:hover {
  color: #fff;
}

.copyright {
  color: #444;
  font-size: 0.8rem;
  margin-top: 10px;
}
</style>
