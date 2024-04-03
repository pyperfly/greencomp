<template>
  <RouterView />
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',

  data(){
        return{
            modalActive: false,
            modalInfo: 0,
            mobileMode: false,

            imprInfo : {
                'Name': 'Stephan Schank',
                'Strasse': 'Blumenstr. 15-A',
                'Ort': '79194 Gundelfingen',
                'Tel': '0151 5150 2251',
                'email': 'pythonfr@mailbox.org'
                }
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
        e.matches ? this.mobileMode=true : this.redirectHome()
      },

      redirectHome(){
                this.$router.push({ path: '/' })
            }
            ,
  },

  created() {
    const mqLarge = window.matchMedia( '(max-width: 750px)' )
    this.checkMobileMode(mqLarge)
    mqLarge.addEventListener('change', this.checkMobileMode)
  }
}


</script>



<style>

@import './assets/fonts.css';
@import './assets/mLayout.css';
@import './assets/fontGlobal.css';



*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}


:root{

--marineTheme : rgba(120, 189, 233,1);
--desertUltraLight : rgba(245, 210, 163,1);
--desertLight : rgba(240, 199, 133,1);
--desertMedium : rgba(190, 160, 100,1);
--desertDark : rgba(90, 60, 40,1);
--forest: rgba(23, 113 , 98, 100);
--darkForest: rgba(13, 73, 63, 100);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}



.wallpaper{
  background-color:rgba(10, 10, 10, 1);
  background:
       linear-gradient(to bottom, rgba(100, 100, 100, 0.4), rgba(100, 100, 100, 0.4)),
    linear-gradient(to bottom, rgb(67, 191, 225), rgba(166, 223, 117, 0.6) 10% 12%, transparent),
    linear-gradient(to bottom, rgba(17, 114, 100, 0.6) 50%, transparent),
    linear-gradient(to top, rgba(137, 166, 103, 0.6) 50%, transparent),
    repeating-linear-gradient(to top, rgba(11, 107, 107, 0.3), rgba(25, 126, 27, 0.3) 30px, rgba(25, 126, 27, 0.3),  rgba(255, 255, 255,0.3) 40px),
    repeating-linear-gradient(rgb(113, 162, 113) 3%, rgba(151, 132, 44, 0.6) 9%, rgba(151, 132, 44, 0.6) 9%, green 3% 16%);
 z-index: -2;   
}

.flowers{
  background-image:
     radial-gradient(rgba(246, 116, 94, 0.7) 3%, rgba(243, 195, 112, 0.911) 5%, rgba(246, 116, 94, 0.2) 8%, transparent 3%),
      radial-gradient(rgba(172, 229, 235, 0.7) 2%, rgba(69, 43, 182, 0.8) 5%, rgba(246, 116, 94, 0.2) 7%, transparent 3%),
   radial-gradient(rgba(211, 237, 240, 0.7) 3%, rgba(231, 226, 181, 0.4) 4% 5%, transparent 3%);
  background-position: 20px 10px, 140px 130px;
  background-size: 600px 600px;
  opacity: 0.8;
  z-index: -1;

}

.lightBox{
  color: var(--desertDark);
  min-height: 40px;
  width: 90%;
  margin: 6px;
  padding: 5px;
  border-radius: 10px;
  background: linear-gradient( to right bottom, rgba(235, 235, 255, 0.6),  rgba(255, 255, 255, 0.2));
  backdrop-filter: blur(2rem);
 }



.darkBox{
  color: var(--desertLight);
  min-height: 40px;
  margin: 8px;
  padding: 10px;
  padding-top: calc(10px + 2vh);
  border-radius: 10px;
  background: linear-gradient( to right bottom, rgba(11, 61, 43, 0.9),  rgba(11,  61, 43, 0.6));
  backdrop-filter: blur(2rem);
 }



 @media(max-width: 750px){
  .darkBox{
    padding-top: 4px;
  }

}



</style>
