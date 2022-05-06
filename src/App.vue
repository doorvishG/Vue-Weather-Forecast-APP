<template>
  <weatherComp/>
</template>

<script>
import weatherComp from './components/WeatherComp.vue'

export default {
  name: 'App',
  components: {
    weatherComp
  }
}
</script>

<style lang="scss">

 @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;1,200;1,300;1,400;1,500;1,600;1,700&display=swap');

 $font: 'Nunito', sans-serif;

 *{
   padding: 0;
   margin: 0;
   box-sizing: border-box;
 }
 
 body{
   background-color: #094D92;
 }

 .card{
   background-color: #2CA58D;
   margin: 0 auto;
   margin-top: 4em;
   width: 35vw;
   height: 22vh;
   border-top-right-radius: 20px;
   border-top-left-radius: 20px;

   h1{
     font-family: $font;
     font-weight: 700;
     color: #fff;
     text-align: center;
     padding-top: 0.8em;
   }

   input{
     background: #2CA58D;
     border: 1px solid #fff;
     padding: 0.5em;
     border-radius: 5px;
     width: 15vw;
     margin-top: 1.1em;
     margin-left: 28%;
     transition: 0.3s ease-in-out;

    &:focus{
      border: 2px solid #fff;
      outline: none;
    }
   }
   
    input[type=text]{
      color: #fff;
      font-family: $font;
      font-size: 1rem;
    }

   ::placeholder{
     font-family: $font;
     color:#fff;
     font-size: 1rem;
   }
 }

 @media (max-width:468px) {
   .card{
     input[type=text]{
     font-size: 0.7rem;
   }
   ::placeholder{
     font-size: 0.7rem;
   }
   }
   
 }

 .result{
   background-color: #1C1018;
   border-bottom-left-radius: 20px;
   border-bottom-right-radius: 20px;
   margin: 0 auto;
   width: 35vw;
   height: 35vh;
   display: flex;
   justify-content: center;

   .location{
     margin-top: 3em;
     margin-left: -4.5em;
        
     h2{
       font-family: $font;
       font-weight: 600;
       color: #fff;
     }

     h1{
       font-family: $font;
       font-weight: 200;
       color: #fff;
     }

     p{
       font-family: $font;
       font-weight: 400;
       color: #fff;
       line-height: 2;
     }
   }

   .image{
     margin-top: 3em;
     padding-left:2em;
      img{
        width: 80px;
        height: 66px;
        
      }
   }
 }
</style>
