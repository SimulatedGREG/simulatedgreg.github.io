<template>
  <div>
    <div class="columns">
      <div class="column is-3 first">
        <strong>CONTACT</strong>
      </div>
      <div class="column">
        <ul>
          <li><a class="button is-outlined" href="mailto:simulatedgreg@gmail.com" target="_blank">Email</a></li>
          <li><a class="button is-outlined" href="https://github.com/SimulatedGREG" target="_blank">GitHub</a></li>
          <li><a class="button is-outlined" href="https://twitter.com/SimulatedGREG" target="_blank">Twitter</a></li>
        </ul>
      </div>
    </div>

    <div class="columns">
      <div class="column is-3">
        <strong>OVERVIEW</strong>
      </div>
      <div class="column">
        <div class="experience-item alt">
          <p>Web development professional with over two years of experience in both front and back end. Highly skilled in JavaScript technologies such as Vue.js and Loopback. Always wanting to make applications efficient and workflow organized as possible. Open to trying new platforms &amp; frameworks.</p>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-3">
        <strong>EXPERIENCE</strong>
      </div>
      <div class="column">
        <div class="experience-item" v-for="exp in experience">
          <strong>{{ exp.title }},</strong> <a :href="exp.link" target="_blank">{{ exp.company }}</a>
          <br>
          <span v-if="exp.time.end">{{ exp.time.begin }} &ndash; {{ exp.time.end }}</span>
          <span v-else>{{ exp.time.begin }}</span>
          <p>{{ exp.description }}</p>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-3">
        <strong>PROJECTS</strong>
      </div>
      <div class="column">
        <div class="experience-item">
          <strong>electron-vue,</strong> <a href="https://github.com/SimulatedGREG/electron-vue" target="_blank">GitHub</a>
          <p>An Electron &amp; Vue.js quick start boilerplate with vue-cli support. Slowly growing more and more popular everyday with {{ stars }} stargazers on GitHub.</p>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-3">
        <strong>EDUCATION</strong>
      </div>
      <div class="column">
        <div class="experience-item">
          <strong>Lone Star College System</strong>
          <br><span>2014 &ndash; 2016</span>
          <p>AAS: Visual Communications (Web Design)</p>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-3">
        <strong>SKILLS</strong>
      </div>
      <div class="column">
        <div class="experience-item">
          <strong>Proficient</strong>
          <p>
            JavaScript (ES6/7), Vue.js, Loopback, Electron
            <br>Git, CommonJS, Webpack, ESLint
          </p>
        </div>
        <div class="experience-item">
          <strong>Familiar</strong>
          <p>React, Node.js, SASS/Scss, MongoDB, PostgreSQL, MySQL, Firebase, Angular, nginx, gulp.js, socket.io, Photoshop, Illustrator</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        experience: [
          {
            title: 'Full Stack Developer',
            company: 'The Pokéthon Team',
            time: {
              begin: 'Jan 2016',
              end: 'Present'
            },
            description: 'A charity gaming marathon where a group of friends play through various Pokémon games in a marathon style to raise money for charity. Am in charge of creating and maintaining website, backend API, system dashboard, stream overlays, and system monitoring.',
            link: 'https://pokethon.net'
          },
          {
            title: 'Web Developer',
            company: 'LocateMyNewHome.com LLC',
            time: {
              begin: 'Oct 2015',
              end: 'Jan 2016'
            },
            description: 'Constructed website for a growing real estate company. Website is made simple for realtors and only requires them to enter a listing MLS number. Back end uses this number to web scrap respective listing information and updates every night.',
            link: 'http://www.locatemynewhome.com'
          },
          {
            title: 'Web Designer',
            company: 'Target Realty, Inc.',
            time: {
              begin: 'April 2014'
            },
            description: 'Created website to increase real estate office’s website potential of getting online leads and has succeeded significantly.',
            link: 'http://targetrealtyinc.com'
          }
        ],
        stars: 'nearly 400'
      }
    },
    created () {
      this.$http.get('https://api.github.com/repos/simulatedgreg/electron-vue')
        .then(({ data }) => {
          this.stars = data.stargazers_count
        })
    }
  }
</script>

<style lang="scss">
  .experience-item {
    margin-bottom: 20px;

    span { color: rgba(#4a4a4a, .75); }

    p {
      color: rgba(#4a4a4a, .75);
      margin-top: 6px;
      transition: color 100ms ease-in-out;
    }

    &:hover p { color: #4a4a4a; }

    &.alt {
      margin-bottom: 0;

      p { margin-top: 0; }
    }
  }

  .first { padding-top: 15px !important; }

  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }

  li {
    display: inline-block;
  }

  .is-3 strong { color: #e74c3c !important; }

  .button {
    background: transparent !important;
    transition: all 200ms ease-in-out;

    &:hover {
      border-color: rgba(#e74c3c, .75) !important;
      color: #e74c3c !important;
    }
  }

  a:not(.button) {
    color: #e74c3c !important;
  }
</style>
