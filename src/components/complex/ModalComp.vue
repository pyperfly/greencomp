<template>
    <Transition>
    <div class="wrapModal" v-show="modalActive">
        <div class="backLayer" @click="closeModal"></div>
        <div class="contentBox">
            <button class="killModal" @click="closeModal">&times;</button>
            <div class="contentField">
                <DSGVO v-if="modalSel === 'dsgvo'" :imprInfo="imprInfo"/>
                <IMPR v-else-if="modalSel === 'impr'" :imprInfo="imprInfo"/>
            </div>
        </div>
    </div>

    </Transition>
        
</template>

<script>

import DSGVO from '@/components/complex/dsgvoCont.vue'

import IMPR from '@/components/complex/imprCont.vue'


export default {
    name : 'Modal',

    props: {
        modalActive: Boolean,
        imprInfo: Object,
        modalSel: Text
    },

    components: {
            DSGVO,
            IMPR
        },

    methods: {
        closeModal(){
            console.log('hello mod close :)'),
            this.$emit("closeModal")
        },

    

    },


}
</script>


<style scoped>

    .wrapModal{
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        z-index: 100;
        display: grid;
        grid-template-columns: repeat( 16, 1fr );
        grid-template-rows: repeat( 16, minmax(10px, auto) );
       
    }

     .backLayer{
        grid-column: 1/17;
        grid-row: 1/17;
        background: rgba(30, 30, 30, 0.7);
        
    }

    .contentBox{

        grid-column: 2/16;
        grid-row: 2/15;
        display: grid;
        grid-template-columns: repeat( 32, minmax(3px, auto) );
        grid-template-rows: repeat( 32, minmax(3px, auto) );
        background: rgb(230, 230, 230);
        border-radius: 10px;
    }

    .killModal{
        grid-column: 26/31;
        grid-row: 1/4;
        padding: 5px;
        max-width: 6vw;
        max-height: 6vw;
        display: flex;
        justify-content: center;
        align-items: center;
        color: rgb(240, 100, 100);
        background: rgba(30,30,30,0.3);
        font-family: concertOne;
        border: none;
        font-size: 3em;
        border-radius: 8px;
    }

    .killModal:hover{
        border: 1px solid red;
        background: rgba(30,30,30,0.7);
    }


    .v-enter-active, .v-leave-active {
    transition: opacity 0.4s ease;
    }

    .v-enter-from,.v-leave-to {
    opacity: 0;
    }

    .contentField{
        grid-column: 2/31;
        grid-row: 4/32;
        overflow-y: scroll;
        max-width: 95%;
        text-wrap: balance;
    }

    @media(max-width: 800px){
        .contentBox{
            grid-column: 2/16;
            grid-row: 4/15;
            }

        .killModal{
            grid-column: 26/31;
            grid-row: 1/5;
            padding: 5px;
            max-width: 18vw;
            max-height: 18vw;
        }

        .contentField{
        grid-column: 2/31;
        grid-row: 6/32;
    }



    }

</style>
