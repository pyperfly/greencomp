<template>
     <div>
            <h1>
                Datenschutzerklärung
            </h1>
            <p class="parafield">{{ this.dsgvoCont.intro }}</p>

            <h3>
                Verantwortlich
            </h3>

            <div class="parafield">
                <p>{{ this.imprInfo.Name }}</p>
                <p>{{ this.imprInfo.Strasse }}</p>
                <p>{{ this.imprInfo.Ort }}</p>

            </div>
            
            <h3>
                Ionos
            </h3>


            <p class="parafield">{{ this.dsgvoCont.ionos }}</p>

            <h2>
                Ihre Rechte
            </h2>



            <p class="parafield">{{ this.dsgvoCont.rightsIntro }}</p>

            <div v-for="(item, key) in this.dsgvoCont.rights" :key=key>
                <h3>{{key}}</h3>
                <p class="parafield">{{ item }}</p>
            </div>
                

        </div>

</template>

<script>

export default {
    name : 'DSGVO',
    props: {
        imprInfo: Object
    },


    data(){
        return{
            dsgvoCont: {
                'intro' :  'Hiermit soll Information hinsichichtlich der Erhebung und Verwendung personenbezogener Daten gegeben werden.\
                        Wir behalten uns vor diese anzupassen, um immer den aktuellen Anforderungen zu entsprechen. \
                         Die Nutzung dieser Webseite ist ohne Angabe personenbezogener Daten möglich',


                'rightsIntro' : 'Als betroffene Person haben Sie das Recht, uns gegenüber Ihre Betroffenenrechte geltend zu machen. Dabei haben Sie insbesondere die folgenden Rechte: Sie haben das Recht, Auskunft darüber zu verlangen, ob und gegebenenfalls in welchen Umfang wir personenbezogene Daten zu Ihrer Person verarbeiten oder nicht. \
                                Sie haben das Recht von uns die Berichtigung Ihrer Daten zu verlangen. Sie haben das Recht von uns die Löschung Ihrer personenbezogenen Daten zu verlangen. \
                                Sie haben das Recht die Verarbeitung Ihrer personenbezogenen Daten einschränken zu lassen. ',

                'ionos' : 'Gehostet wird diese Webseite durch 1&1 IONOS SE, Elgendorfer Str. 57, 56410 Montabaur, Deutschland. Weitere Infos können Sie der Datenschutzerklärung von IONOS entnehmen: https://www.ionos.de/terms-gtc/terms-privacy.',

                'rights' : {
                    'Datenübertragbarkeit': 'Sie haben das Recht die Sie betreffenden personenbezogenen Daten, die Sie uns bereitgestellt haben, in einem strukturierten, gängigen und maschinenlesbaren Format zu erhalten, und diese Daten einem anderen Verantwortlichen zu übermitteln.',
                    'Widerspruchsrecht' : 'Sie haben das Recht, gegen jede Verarbeitung Widerspruch einzulegen. Sofern durch uns personenbezogene Daten über Sie zum Zweck der Direktwerbung verarbeitet werden, können Sie gegen diese Verarbeitung Widerspruch einlegen.',
                    'Widerrufsrecht' : 'Sofern Sie uns eine gesonderte Einwilligung in die Datenverarbeitung erteilt haben, können Sie diese Einwilligung jederzeit widerrufen. Durch einen solchen Widerruf wird die Rechtmäßigkeit der Verarbeitung, die bis zum Widerruf aufgrund der Einwilligung erfolgt ist, nicht berührt.'
                    }
            
                }


            }

         }

    }


</script>

<style scoped>


.parafield{
    margin: 5px 0 25px 0;
}

</style>