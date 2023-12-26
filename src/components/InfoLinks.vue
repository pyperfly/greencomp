<template>
    
    <div class="linCont">
        <div class="linkWrap lightBox">
            <button @click="$emit('openModal', 'impr')" class="fontsmall">Impressum</button>
            <button @click="$emit('openModal', 'dsgvo')" class="fontsmall">Datenschutz</button>
        </div>
    </div>
    
</template>




<script>
    export default{
        name: 'InfoLinks',
        data(){
            return{
                hovering: false
            }
        },

        methods:{
            hovermode(){
                console.log('hovering')
                this.hovering = true
            }


        }
    }
</script>

<style scoped>
    .linCont{
        display: flex;
        justify-content: center;
        z-index: 1;
        padding: calc(3px + 1vh);
    }

    
    .linkWrap {
        display: flex;
        flex-direction: row;
        width: calc(40% + 30px);
    }

     .linkWrap button{
        flex: 1;
        flex-basis: auto;
        margin: 5px 10px;
        padding: 3px 10px;
        border: none;
        border-radius: 0.6em;
        font-family: poppins;
        color:  var(--desertLight);
        background: rgb(33, 54, 44);
        z-index: 2;
    }

     .linkWrap button:hover{
        background: rgb(155, 225, 191);
        color: rgb(33, 54, 44);
    }



    @media(max-width: 750px){
        .linkWrap{
            flex-direction: column;
            width: calc(80% + 10px);
        }


    }

    @media(min-width: 1100px){
        
        .linCont{
        padding: 0;
    }

        .linkWrap{
            flex-direction: column;
            margin: 0;
            padding: 0;
            width: calc(70% + 30px);
        }




    }

   

   
</style>