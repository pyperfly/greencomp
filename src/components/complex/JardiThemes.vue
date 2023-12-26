<template>
    <div class="themesCont"> 

        <div class="themesNav"> 
            <div class="buttonCont">
                <MagButton
                v-for="item in themes" 
                :key="item.id"
                @switchTheme = switchTheme(item.id)
                :title="item.title" 
                :selMode="item.selected"
             />
            </div>
        </div>

        <div class="themeTitle"> 
            <h3> {{ selTheme.title }}</h3>
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
            
        <div class="gback-a gbacks"></div>
        <div class="gback-b gbacks"></div>
         <div class="gback-c gbacks"></div>

    </div>


</template>

<script>

    import MagButton from '@/components/complex/MagneticButton.vue'
    import themesCont from '@/assets/themes.json'
    import pflImage from '@/assets/imgs/pflanzungCut.jpg'
    import heckenImg from '@/assets/imgs/hecken.jpg'
    import bodenImg from '@/assets/imgs/boden.jpg'

    export default{
        name: "JardiThemes",
        components: {
            MagButton

        },

        data(){
            return{
                imgs: [pflImage, heckenImg, bodenImg],
                themes: themesCont,
                selTheme: {},
                hovering: false,
                switchWidth: '65%',
                
            }
            
            
        },


        methods : {
            switchTheme(id){

                for (const [key, value] of Object.entries(this.themes)) {
                    console.log(' --  -- ',key, value)
                    if (value.id === id){
                        this.selTheme = value
                        console.log("huhu switch theme", key)
                        this.selTheme.selected = true
                            if (value.wideImage === true){
                            this.switchWidth = '85%'
                                }
                            else{
                                this.switchWidth = '60%'
                                }
                        }
                    
                    else{
                        value.selected = false
                    }
                    


                console.log("huhu switch theme", id)
                }
         

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

@import '@/assets/themes.css';

.hoverclass{
        font-size: 0.9rem;
        background: white;
        
    }

</style>