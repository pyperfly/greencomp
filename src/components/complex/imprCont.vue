<template>
    <div>
           <h3>
               Verantwortlich
           </h3>

           <p>{{ this.imprInfo.Name }}</p>
           <p>{{ this.imprInfo.Strasse }}</p>
           <p>{{ this.imprInfo.Ort }}</p>


    </div>

</template>

<script>

export default {
   name : 'IMPR',
   props: {
       imprInfo: Object
   },

   }


</script>

<style></style>