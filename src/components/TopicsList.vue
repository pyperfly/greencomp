<template>
    <div class='topicsCont'>
        <h3 :class="fadeSwitch(0)" class="topiText"> {{ this.shownTopics[0] }}</h3>
        <h3 :class="fadeSwitch(1)" class="topiText"> {{ this.shownTopics[1] }}</h3>
        <h3 :class="fadeSwitch(2)" class="topiText"> {{ this.shownTopics[2] }}</h3>
       
    </div>
    
</template>

<script>
export default {
    name : 'Topics',

    computed: {
       

    },

    
    methods : {

         fadeSwitch(ic) {
            return{
                fadeOuCl: this.fadeOut && this.interCounter === ic,
                fadeInCl: this.fadeIn && this.interCounter === ic
            }

        },



        setnewName(){
            this.thirdT = this.jarditopics[1]
            console.log('nach timeout',this.thirdT)  
        },

        changeText(){
                this.interCounter++
                if(this.interCounter > 2){
                    this.interCounter = 0
                }
                this.fadeIn = false
                this.fadeOut = true,
            
                setTimeout(() => {
                    let i = this.interCounter
                    let p = Math.floor(Math.random() * 7)
                    let notaus = 0
                
                    while(this.topicIndexArray.includes(p) && notaus < 25){
                        p = Math.floor(Math.random() * 7)
                        notaus++
                    }     

                    this.topicIndexArray[i] = p
                                        
                    this.shownTopics[i] = this.jarditopics[p]

                    this.fadeOut = false
                    this.fadeIn = true

                    }, this.stayTime)
                },



        updateTopics(){
            
            setInterval(this.changeText, 6000)
            }
            
    },

    data(){
        return {
            jarditopics : [],
            shownTopics : [],
            stayTime : Number,
            fadeOut: false,
            fadeIn: false,
            interCounter: Number,
            topicIndexArray: [],
        }
    },

    created() {
        this.jarditopics = [
            'naturnahe und pflegeleichte Pflanzungen',
          'Heckenpflege mit Plan',
          'pflegende Rasen- Wiesenmahd',
          'nachhaltig gesunde Obstbäume',
          'sinnvoller Schnitt für jeden Strauch',
          'effiziente Aukkugeräte',
          'kompetent und günstig'
        ],

        this.topicIndexArray = [1,3,4]
        
        this.shownTopicsDict = {
            first:      'naturnahe und pflegeleichte Pflanzungen',
          second: 'Heckenpflege mit Plan',
          third: 'pflegende Rasen- Wiesenmahd',
       
        }

        this.topicIndexArray.forEach((element,index) => {
            this.shownTopics[index] =  this.jarditopics[element]
        }),


        this.stayTime = 3000 
        this.interCounter = 1
        this.updateTopics() 
        },


    mounted() {
        //this.changeText()
        console.log(this.thirdT)
    },

  
}

//var firstT = document.getElementById("firstT");
//var secondT = document.getElementById("seondT");
//var thirdT = document.getElementById("thirdT");

//let firstText = firstT.innerHTML

//console.log(firstT.innerText)


</script>





<style>

.topicsCont{
    position: relative;
}


.topiText{
    position: absolute;
    font-family: concertOne;
    text-shadow: calc(0.3px + 0.1vw) 1px 0.2em var(--desertUltraLight);
}

.topiText:nth-child(1){
    top: 5%;
    left: 25%;
}


.topiText:nth-child(2){
    top: 40%;
    left: 10%;
}


.topiText:nth-child(3){
    bottom: 15px;
    left: 15%;
}




.fadeOuCl{
 animation: fadeOutAni 3s;
 
}



@keyframes fadeOutAni {
    from{
        opacity: 100%;
    }
    to{
        opacity: 0%;
    }
}


.fadeInCl{
 animation: fadeInAni 3s;
}

@keyframes fadeInAni {
    from{
        opacity: 0%;
    }
    to{
        opacity: 100%;
    }
}


@media(max-width: 750px){

    .topicsCont{
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    position: static;
    min-height: 25vh;
    gap: 2vh;  
    }


    .topiText{
    position: static;
    font-family: concertOne;
    text-shadow: 2px 2px 0.3em var(--desertLight);
    }

   
}




</style>
