<template>
    <div class='darkBox aboutCont'>
        <p class='story'>{{ aboutText }}</p>
    </div>
    
</template>

<script>
export default {
    name : 'CompText',

    data(){
        return{
            aboutText : 'Sie möchten vitale Bepflanzungen, ein harmonisches Nebeneinander und pflegeleichte Eleganz in Ihrem Garten?\
             Durch Schnittmaßnahmen, Bodenverbesserungen und Pflanzungen lassen sich mit Pflanzenkenntnis und technischem Geschick Gärten umgestalten.\
            Ein Gehölz-Rückschnitt kann für mehr grün sorgen und das Gehölz wird im Wachstum gebremst. \
            Besonders Interessant kann auch eine Veränderung in ihrer Bepflanzung sein, so manch nicht ganz bekannter Strauch kann ihren Garten aufwerten und doch erstaunlich pflegeleicht sein.\
             Manchmal kann man den Standort einer Pflanze verbessern, oder es ist besser Ihr einen neuen zu bieten.\
             Bei meiner Arbeit setze ich moderne Akku-Technik, effizientes Schneidgeräte und bewährte Hilfstechnik ein.',
        }
        
    },

}






</script>

<style>
  

    .story{
        font-family: hanken;
       
    }
 
</style>