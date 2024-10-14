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
            aboutText : 'Für Gärten die durch grüne Formvielfalt, Harmonie und Vitalität begeistern.\
                Seit vielen Jahren arbeite ich mit Gehölzen und Bäumen sowie Stauden und Gräsern in Pflanzungen unterschiedlichster ausprägung.\
            Für zeitlich passende und schonende Schnittmaßnahmen sollte das artspezifische Wachstum und die Biologie der Pflanzen berücksichtigt werden.\
            Schöne und pflegeleichte Pflanzungen können durch die fundierte Berücksichtigung von Nutzung, Ökologie, Boden und Biologie realisiert werden.\
                        Die Ausstattung reicht hier von Scheeren bis zu großen Motorsägen und von Bodentestern zu Klettergerät.',
        }
        
    },

}






</script>

<style>
  

    .story{
        font-family: hanken;
       
    }
 
</style>
