<template>
    <div class='darkBox aboutCont'>
        <p class='blabla'>{{ aboutText }}</p>
    </div>
    
</template>

<script>
export default {
    name : 'CompText',

    data(){
        return{
            aboutText : 'Sie möchten vitale Bepflanzungen, ein harmonisches Nebeneinander und pflegeleichte Eleganz in Ihrem Garten?\
            Mit Pflanzenkenntnis und technischem Geschick lassen sich Gärten durch Schnittmaßnahmen, Bodenverbesserungen und Pflanzungen verwandeln.\
            Ein Gehölz-Rückschnitt kann für mehr grün sorgen und das Gehölz wird im Wachstum gebremst.\
            Spannend ist auch die Zukunft ihrer Bepflanzung, so manch nicht ganz bekannter Strauch kann ihren Garten aufwerten und doch erstaunlich pflegeleicht sein. \
            Manchmal kann man den Standort einer Pflanze verbessern, oder es ist besser Ihr einen neuen zu bieten.\
            Bei meiner Arbeit setze ich moderne Akku-Technik, effizientes Schneidgeräte und bewährte Hilfstechnik ein.',
        }
        
    },

}






</script>

<style>
  

    .blabla{
        font-family: hanken;
       
    }
 
</style>