<template>
  <div>
    <header 
      class="fixed py-5 px-5 w-full flex bg-white z-10" 
      :class="{ hidden: !showNavbar }"
    >
      <div 
        class="bg-cover bg-center w-16 h-16 rounded-full mr-3 cursor-pointer" 
        style="background-image: url(https://i.ibb.co/pdxLgVg/Dr-Strangelove.png); min-width: 4rem"
        @click="$router.push('/')"
      ></div>
      <div class="cursor-pointer" @click="showSide = true">
        <p class="text-lg mt-1">shusuke ioku</p>
        <p class="text-xs leading-tight" style="width: 13rem; min-width: 13rem">crisis signaling, deterrence, alliance</p>
        <p class="text-xs leading-tight" style="width: 13rem; min-width: 13rem">formal theory, survey experiment</p>
      </div>
      <input 
        class="appearance-none block w-full px-3 mt-1 mx-auto focus:outline-none" 
        type="text"
        v-model="search"
        placeholder="keywords."
        @keypress.enter="$router.push('/search/' + search)"
      >
    </header>  
    <div 
      v-if="showSide"
      class="cover fixed top-0 bottom-0 left-0 right-0 z-20" 
      style="background: rgba(255,255,255,.9)"
      @click="showSide = false"
    ></div>
    <div 
      class="side fixed top-0 right-0 bottom-0 bg-white p-5 z-30"
      :class="{shown: showSide}"
    >
      <div class="flex mb-5">
        <div 
          class="bg-cover bg-center w-16 h-16 rounded-full mr-3 cursor-pointer" 
          style="background-image: url(https://i.ibb.co/pdxLgVg/Dr-Strangelove.png); min-width: 4rem"
          @click="showSide = true"
        ></div>
        <div>
          <p class="text-lg mt-1">shusuke ioku</p>
          <p class="text-xs leading-tight" style="width: 13rem; min-width: 13rem">crisis signaling, deterrence, alliance</p>
          <p class="text-xs leading-tight" style="width: 13rem; min-width: 13rem">formal theory, survey experiment</p>
        </div>
      </div>
      <div class="list">
        <div>
          <p><span>Academic Position</span></p>
        </div>
        <ul>
          <li>Graduate Student, GSPS, Waseda Univ.</li>
          <li>Junior Visiting Fellow, Japan Institute of International Affairs</li>
        </ul>
        <div>
          <p><span>Paper</span></p></div>
        <ul>
          <li>"Threats and Assurances with Military Actions," In Progress</li>
          <li>"Tuning Audience Costs," In Progress</li>
        </ul>
        <div>
          <p><span>Presentation</span></p>
        </div>
        <ul>
          <li>"Threats and Assurances with Military Actions," 2020 Annual Conf., Japan Assoc. of Int'l Relations</li>
          <li>"Threats and Assurances with Military Actions," Mar. 2021, Game Theory Workshop</li>
        </ul>
        <div>
          <p><span>Scholarship & Award</span></p>
        </div>
        <ul>
          <li>Scolarship Fellow, US-Japan Partnership Program, Research Institute of Peace and Security</li>
          <li>Secretary-General Award, Diplomacy Essey Contest, Japan Liberal Democratic Party</li>
        </ul>
        <div>
          <p><span>Training</span></p>
        </div>
        <ul>
          <li>"Causal Inference for Social Sciences," 2020, ICPSR Summer Program</li>
          <li>"Multilevel Models II: Advanced Topics," 2020, ICPSR Summer Program</li>
          <li>"Text Analysis for Social Sciences," 2019, Essex Summer School</li>
          <li>"Maximum Likelihood," 2018, Essex Summer School</li>
        </ul>
        <div>
          <p><span>Skill</span></p>
        </div>
        <ul>
          <li>R, Python, HTML, CSS, JavaScript</li>
        </ul>
        <div>
          <p><span>Non-Academic Position</span></p>
        </div>
        <ul>
          <li>Freelance Web Developer</li>
          <li>Junior Research Fellow, National Defense Academy of Japan</li>
          <li>Research Assistant, Asia-Pacific Initiative</li>
          <li>Research Assistant, Center for Strategic & International Studies</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style lang="stylus" scoped>
header
  transform translate3d(0, 0, 0)
  transition 0.1s all ease-out
  box-shadow 0 3px 3px rgba(0, 0, 0, .05)
.hidden
  transform translate3d(0, -100%, 0)
input
  width 100%
  background #eee
  border-radius .5rem
::-webkit-input-placeholder
  color black
:-ms-placeholder
  color black
.side
  width 400px
  margin-right -400px
  transition .1s all ease-in-out
  box-shadow -3px 0 3px rgba(0,0,0,.05)
  overflow-y scroll
  @media (max-width 768px) {
    width 80%
    margin-right -80%
  }
  .list
    div
      margin 1rem 0 .25rem
      p
        position relative
        span
          width fit-content
          background white
          padding-right .2rem
      p:before
        content ''
        display block
        width 100%
        background black
        height 1px
        position absolute
        top .7rem
        left 0
        z-index -1
    ul
      margin-left .75rem
      li
        font-size .75rem
        position relative
.shown
  margin-right 0
</style>

<script>
export default {
  data() {
    return {
      search: '',
      showNavbar: true,
      lastScrollPosition: 0,
      showSide: false
    }
  },
  mounted () {
    window.addEventListener('scroll', this.onScroll)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    onScroll () {
      const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop
      if (currentScrollPosition < 0) {
        return
      }
      if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 60) {
        return
      }
      this.showNavbar = currentScrollPosition < this.lastScrollPosition
      this.lastScrollPosition = currentScrollPosition
    }
  }
}
</script>