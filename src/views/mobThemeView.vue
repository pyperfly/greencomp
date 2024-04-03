<template>
  <div class="mobThemes wallpaper">

   <RouterLink to="/" class="homeBtn mobButtons">
    <p class="uniSign">&#11207;</p>
    <h3>Zurück</h3></RouterLink> 
   
   <div class="MobThemeNav mobButtons" @click="openThemeModal">
    <h3>Anderes Thema...</h3>
    <p :style="{ transform: arrowRotate}">&#9654;</p>
   </div>
   
   <div class="themeSection">
        <div class="themeTitle"> 
                <h2> {{ selTheme.title }}</h2>
        </div>
            
        <div class="themeText darkBox"> 
                <p> {{ selTheme.text }}</p>
        </div>

        <div class="imageCont">
                <div class="themeImage" :style="{ width: switchWidth}">
                    <img :src="getImgUrl(selTheme.img)" />
                    <div class="overlayDiv"></div>
                </div>          
    </div>
    
    <InfoLinks 
     @openModal = "openModal"
     :imprInfo="imprInfo"
    />

   </div>

   <Transition>
    <div v-show="themeModalActive" class="themeSelOverlay" @click="closeThemeModal">
        <p class="closeMe">&times;</p>

        <div class="navCont">
            <button v-for="item in themes" :key="item.id" @click="switchTheme(item.id)"><h2>{{item.title}}</h2></button>

        </div>    
        
   </div>
   
   </Transition>

  

   <Modal 
    :modalActive="this.modalActive"
    :imprInfo="imprInfo"
    :modalSel="this.modalInfo"
    @closeModal = "closeModal"
    />
    
      
  </div>
</template>


<script>

    import themesCont from '@/assets/themes.json'
    import pflImage from '@/assets/imgs/pflanzungCut.jpg'
    import heckenImg from '@/assets/imgs/hecken.jpg'
    import bodenImg from '@/assets/imgs/boden.jpg'

    import InfoLinks from '@/components/InfoLinks.vue'
    import Modal from '@/components/complex/ModalComp.vue'

    import imprInfo from '@/assets/imprInfo.json'

    export default{

        components: {
            InfoLinks,
            Modal,
        },


        data(){
            return{
                imgs: [pflImage, heckenImg, bodenImg],
                themes: themesCont,
                imprInfo: imprInfo,
                selTheme: {},
                arrowRotate: "rotate(0)",
                themeModalActive: false,
                modalActive: false,
                modalInfo: 0,
                
            }
            
            
        },

        methods : {
            switchTheme(id){

                for (const [key, value] of Object.entries(this.themes)) {
                    console.log(key)
                    if (value.id === id){
                        this.selTheme = value
                        this.selTheme.selected = true
                        }
                    
                    else{
                        value.selected = false
                    }
                    


                
                }
         

            },

            

            openModal(info){
                this.modalActive = true
                this.modalInfo = info
            },

            closeModal(){
                this.modalActive = false
            },


            openThemeModal(){
                this.themeModalActive = true
            },

            closeThemeModal(){
                this.themeModalActive = false
            },


             getImgUrl: function (img) { 
                return require('@/assets/imgs/' + img);
            }


            
        },

        created() {
            this.selTheme = this.themes.hecken
         }


    }



</script>


<style>
.mobThemes{
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(24, minmax(4vh, auto));
  gap:2px;
}

.mobButtons{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 3px;
  margin: 3px;
  max-height: 10vh;
  border-radius: 5px;

}

.mobButtons:hover{
    font-weight: 700;
    border: 1px solid gold;

}

.homeBtn{
    position: fixed;
    right: 3px;
    color: var(--darkForest);
    background-color: rgba(183, 83 , 88, 0.9);
    border-radius: 0.3em;
    border: none;
    text-decoration: none;
    z-index: 100;
}

.uniSign{
    font-size: 25px;
}


.MobThemeNav{
  grid-column: 2/8;
  grid-row: 3/5;
  padding:8px;
  background-color: var(--darkForest);
  color: var(--desertLight);
  cursor: pointer;
}


.themeSection{
    grid-column: 1/13;
    grid-row: 6/20;
    display: flex;
   flex-direction: column;
   align-items: center;
   gap:10px;
}

.themeSelOverlay{
    position: relative;
    grid-column: 1/13;
    grid-row: 2/20;
    background: rgba(43, 83 , 88, 0.5);
    z-index: 10;
}

.closeMe{
    position: absolute;
    right: 5px;
    top: 5px;
    font-family: concertOne;
    font-size: 3em;
    cursor: pointer;
}

.closeMe:hover{
    color: rgba(243, 83 , 88, 0.8);

}

.navCont{
    display: flex;
    flex-direction: column;
    gap: 5px;
    min-height: 38vh;
    padding: 15vh 10vw; 
}

.navCont button{
    padding: 1px 1px; 
    background: var(--desertLight);
    border-radius: 0.6em;
    border: none;
    box-shadow: 0 0 1em 0 var(--desertMedium);
    font-family: concertOne;
    cursor: pointer;
}

.navCont button:hover{
    font-weight: 700;
    box-shadow: 0 0 2em 0 green;
    }

.v-enter-active, .v-leave-active {
    transition: opacity 0.4s ease;
    }

    .v-enter-from,.v-leave-to {
    opacity: 0;
    }



</style>
