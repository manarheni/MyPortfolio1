<template>
  <div class="main-content">
    <Intro :data="data" />
    <div :class="data.lang === 'ar' ? 'exp-container reverse' : 'exp-container'">
      <Education :data="data" />
      <Experience :data="data" />
    </div>
    <div class="skills-container">
      <Skills :data="data" />
    </div>
    <div class="portfolio-container">
      <Portfolio :data="data" />
    </div>
    <div class="contact-container">
      <Contact :data="data" />
    </div>
  </div>
</template>

<script>
import Intro from './mainContent/Intro.vue';
import Education from './mainContent/Education.vue';
import Experience from './mainContent/Experience.vue';
import Skills from './mainContent/Skills.vue';
import Portfolio from './mainContent/Portfolio.vue';
import Contact from './mainContent/Contact.vue';

export default {
  name: 'Main',
  components: {
      Intro,
      Education,
      Experience,
      Skills,
      Portfolio,
      Contact
  },
  props: ['data'],
  
}
</script>


<style scoped>
  .rtl {
        direction: rtl;
  }

  .reverse {
      flex-direction: row-reverse;
  } 

  .main-content {
      padding: 0;
  }

  .exp-container {
    padding: 3% 10%;
    background-color: #1f203a;
    display: flex;
    overflow: hidden;
  }

  .skills-container {
    padding: 3% 10%;
    background-color: #f7f7f7;
    overflow: hidden;
  }

  .portfolio-container {
    padding: 3% 10%;
    background-color: #1f203a;
    display: flex;
    overflow: hidden;
  }

  @media(max-width: 767px) {
      .exp-container {
          padding: 40px 20px;
          flex-direction: column;
      }
  }
</style>
