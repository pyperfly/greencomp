<template>
    <div class="container" @mousemove="moveBtn" @mouseenter="moveAni" @mouseleave="moveEnd" ref="btnCont">
        <button @click="$emit('switchTheme')" class="mButton fontmd" :class="{selectedTheme: selMode}" ref="mBtn">{{ title }}</button>
    </div>

</template>

<script>

export default{
    name: "MagButton",
    props: {
        title: String,
        selMode: Boolean,
    },    

      data(){
            return{
                activeColor: 'var(--desertDark)',
               
            }
            
            
            
        },


    methods : {

        switchColor(){
            console.log('switch to ', this.title, this.selMode)
            if(this.selMode == true){
                this.activeColor = 'var(--desertLight)'
            }
            else{
                this.activeColor = 'black'
            }

        },


        moveBtn(event){
            console.log('mbutton hober')
            const brect = this.$refs.btnCont.getBoundingClientRect()
            const x = event.pageX  
            const y = event.pageY 
            const bcx = brect.left + window.scrollX + brect.width / 2
            const bcy = brect.top + window.scrollY + brect.height / 2
            const dx = x - bcx 
            const dy = y - bcy
            //console.log(brect.top,'y event ', y, 'folgt ein delta ', dy) 

            const mBtn = this.$refs.mBtn

            const magfac = 4

            mBtn.style.transform = `translate(${dx/magfac}px,${dy/magfac}px)`

        },

        moveAni(){
            const mBtn = this.$refs.mBtn
            mBtn.style.transition = `all 0.5s ease`
            setTimeout(()=>{
                mBtn.style.transition = ''
            }, 500)

        },

        moveEnd(){
            const mBtn = this.$refs.mBtn

            mBtn.style.transform = `translate(0px,0px)`

        }
    },


    


}


</script>

<style>


    .container{
        display: flex;
        max-width: 300px;
        align-items: center;
        justify-content: center;
        flex: 1 0 0;

    }

       
    .mButton{
        display: inline-flex;
        justify-content: center; /* center the content horizontally */
        width: 100%;
        height: auto;
        max-height: 55px;
        padding-top: calc(2vh -1px);
        padding-bottom: 0.3vh;
        background: var(--desertLight);
        border-radius: 0.4em;
        border: none;
        box-shadow: 0 0 1em 0 var(--desertMedium);
        font-family: concertOne;
    }

     .mButton:hover{
        font-weight: 700;
        box-shadow: 0 0 2em 0 green;
    }

    .selectedTheme{
        color: var(--desertLight);
        background: linear-gradient(to top, var(--desertLight),rgba(14, 118, 54, 0.6) 15%, rgba(14, 118, 54, 0.6) 35%, var(--desertLight));

    }

    @media(min-width: 1000px){
        .mButton{
        height: calc(95% - 4vh + 5px);
        max-height: 65px;
        }

    }

</style>
