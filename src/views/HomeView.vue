<template>
   <div class="home wallpaper">
    <SiteIntro />
    <CompText />
    <InfoComp 
    :imprInfo="imprInfo"
    />
    <InfoLinks 
     @openModal = "openModalWin"
    />
    <Topics />
   <div v-if="mobileMode" class="themesBtnCont">
    <RouterLink to="/themes" class="themesBtn fontmd">Gartenthemen... &#9654;</RouterLink> 
   </div>
    <JardiThemes v-if="!mobileMode"/>   
    <div class="flowers"></div>
    <Modal 
    :modalActive="this.modalActive"
    :imprInfo="imprInfo"
    :modalSel="modalInfo"
    @closeModal = "closeModalWin"
    />
  </div>
</template>

<script>
// @ is an alias to /src
//import siteIntro from '@/components/Intro.vue'
import SiteIntro from '@/components/Intro.vue'
import CompText from '@/components/CompText.vue'
import Topics from '@/components/TopicsList.vue'
import InfoComp from '@/components/InfoComp.vue'
import JardiThemes from '@/components/complex/JardiThemes.vue'
import InfoLinks from '@/components/InfoLinks.vue'
import Modal from '@/components/complex/ModalComp.vue'
import imprInfo from '@/assets/imprInfo.json'


export default {
  name: 'HomeView',
  components: {
    SiteIntro,
    CompText,
    Topics,
    InfoComp,
    JardiThemes,
    InfoLinks,
    Modal
  },

data(){
        return{
            modalActive: false,
            mobileMode: false,
            modalInfo: 0,
            imprInfo : imprInfo
        }

    },

  methods : {
      openModalWin(info){
        this.modalActive = true
        this.modalInfo = info
      },
      closeModalWin(){
        this.modalActive = false
      },
      checkMobileMode(e){
        e.matches ? this.mobileMode=true : this.mobileMode=false
      }
  },

  created() {
    const mqLarge = window.matchMedia( '(max-width: 750px)' )
    this.checkMobileMode(mqLarge)
    mqLarge.addEventListener('change', this.checkMobileMode)
  }
}

</script>



<style>



.themesBtn{
    min-height: 10vh;
    padding: 5px;
    color:  var(--desertLight);
    background-color: rgba(23, 63 , 58, 100);
    border-radius: 0.3em;
    border: none;
    text-decoration: none;
}
 
</style>
