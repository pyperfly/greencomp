<template>
    <div class='introCont'>
        <h1>Grünpflege</h1><h1 class='namePart'>Schank</h1>
    </div>
    
</template>

<script>
export default {
    name : 'SiteIntro',

}
</script>

<style>


     .introCont{
        display: flex;
        flex-direction: row;
        align-items: end;
        gap: 1vw;
        font-family: rubik;
        font-weight: 600;
        background: radial-gradient(closest-side, rgba(250,250,250,0.5), rgba(250,250,250,0.2), transparent);
        
    }

    .namePart{
        font-weight: 300;
    }


    @media(max-width: 1350px){
            .introCont{
                flex-direction: column;
                align-items: center;
        }

        }

</style>
