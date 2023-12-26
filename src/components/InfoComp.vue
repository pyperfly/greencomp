<template>
    <div class='infoCont lightBox'>
        <div class="impText fontmd">
            <p>{{ this.imprInfo.Name }}</p>
            <p>{{ this.imprInfo.Tel }}</p>
            <p>{{ this.imprInfo.email }}</p>

        </div>        
    </div>
</template>


<script>

export default{

    name: 'InfoComp',
    props: {
        imprInfo: Object
    },

}
</script>


<style>
     .infoCont{
        display: flex;
        justify-content: center;
        align-items: center;
        margin: auto;
        padding: calc(2px + 1vh);
        padding-bottom: calc(2px + 4vh);
        color: black;
     }

     .infoCont p{
        padding-top: calc(0.8px + 0.6vh);
     }

     .impText{
        letter-spacing: 0.1em;
        font-weight: 200;
        font-family: poppins;
     }

     .impText > p{
        padding-top: calc(3px + 2vh);
     }

     @media(max-height:750px){
        .infoCont{
            margin: 5px auto;
            padding: calc(3px + 0.5vh);
            color: black;
        }

     }


</style>
