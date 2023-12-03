<template>
   <!--Contenedor General   -->
    <div class="   w-full  p-1 flex flex-col mx-auto  md:w-full md:p-4">

      
      <div class=" w-full flex flex-col md:flex-col md:full"><!--Contenedor 1  -->




       <div class=""><!--Contenedor 1.1  --> 

      <div v-if="isLoading" >Cargando...</div>
      <div v-else>
        
        <div  class="mb-4">
             <!--info 1  -->
          <div v-if="info.periodo" class="text-center bg-pink-950 p-4 rounded-full w-3/4  md:w-full ">
          <p class="text-3xl text-white md:text-4xl">Periodo Escolar:</p>
          <p class="AbrilFont text-white text-xl">{{ info.periodo}}</p>
        </div>
      </div><!--termina div for  -->

</div><!--termina div else  -->
       </div> <!--fin Contenedor 1.1  --> 




       <div class=" space-x-3 w-full flex flex-row md:flex-row md:full md:justify-between"><!--Contenedor 1.2.2  -->

       <div class=""> <!--Contenedor 1.2  --> 
<!--info 2 -->
<div v-if="isLoading" >Cargando...</div>
      <div v-else>
        
        <div  class=" ">


        <div v-if="info.inicio" class=" ">
          <p class=" text-xl md:text-3xl text-center bold text-white ">Inicio de periodo de evaluacion</p>
          <p class=" text-pink-100 rounded-full  bg-pink-950 AbrilFont text-xs italic semi-bold  text-center md:text-lg">{{ formatDate(info.inicio) }}</p>
        </div>

      </div><!--termina div for  -->
       </div> <!--dic else --> 

      </div> <!--fin Contenedor 1.2  --> 



      <div class=""> <!--Contenedor 1.3  --> 
        <div v-if="isLoading" >Cargando...</div>
      <div v-else>
        
        <div  class=" ">
        <!--info 3  -->
        <div v-if="info.fin" class=" ">
          <p class=" text-xl md:text-3xl text-center bold text-white">Fin de periodo de evaluacion</p>
           <p class="text-pink-100 rounded-full  bg-pink-950 AbrilFont text-xs  text-center md:text-lg">{{ formatDate(info.fin) }}</p>
        </div>



      </div><!--termina div v for  -->

</div><!--termina div v else  -->

</div><!--FIN Contenedor 1.3  --> 
</div><!-- fin Contenedor  1.2.2-->


</div><!--Termina contenedor 1-->










<div class=" flex items-center p-2  justify-around "><!--Inicia contenedor 2-->

<div v-if="isLoading" >Cargando...</div>

<div v-else>
        
        <div class="mb-4  w-3/4  ">
        <!--info 4  -->
        <div v-if="info.alTotal" class="rounded-full  ">
         
          <p class=" text-rose-50 AbrilFont text-5xl text-center md:text-8xl">{{ info.alTotal}}</p>
          <p class="text-rose-50 text-center text-sm Questrial md:text-base">Cantidad total de alumnos</p>
        </div>
        <!--info 5  -->
        <div v-if="info.alEvaluados" class="w-40 ">
          
          <p class="text-rose-50 AbrilFont text-5xl text-center md:text-8xl">{{ info.alEvaluados}}</p>
          <p class="text-rose-50 text-xs text-center Questrial md:text-base text-center">Alumnos que resolvieron la evaluacion</p>
        </div>
       
<!--termina infos  -->

       
        </div><!--termina div for  -->

      </div><!--termina div else  -->

      <div v-if ="info.alTotal" class="pt-2 p-8 w-80 h-24  bg-pink-950   hover:bg-amber-600  active:bg-amber-600 focus:outline-none focus:ring focus:bg-amber-600 rounded-full place-content-center md:pt-20 md:w-80 md:h-80">
          
          <p class="text-rose-50 AbrilFont text-5xl text-center md:text-center md:text-8xl">{{ (info.alTotal)-(info.alEvaluados)}}</p>
          <p class="  text-rose-50 text-sm text-center  rounded-full Questrial md:text-base text-center rounded-full">Alumnos por evaluar</p>
        </div>
   
   
    </div><!--termina contenedor 2 -->


  <div class=" w-full flex flex-col  md:full"><!--Contenedor 3 -->

<div class=" space-x-4 w-full flex flex-col items-center md:items-center md:grid grid-cols-2 gap-6 md:full md:justify-between">     <!--Contenedor 1.2.2  -->

       <div class=""> <!--Contenedor 1.2  --> 
<!--info 2 -->
<div v-if="isLoading2" >Cargando...</div>
<div class="flex flex-row ">
        <div class="mb-4 ">


       <details v-if="info2.ISC" class="  dark:open:bg-orange/30 p-4 open:ring-1 open:ring-black/5 dark:open:ring-white/10 open:shadow-lg p-6 rounded-lg" open>
    <summary class=" dark:text-white  select-none text-white AbrilFont font-bold text-xl md:text-3xl text-center  bg-pink-950 w-80  rounded-full  ">ISC
    </summary>
    <div class=" rounded-lg backdrop-blur-sm bg-orange/30 p-4">
<p class="AbrilFont text-xs  text-center md:text-lg">Evaluaciones realizadas {{ info2.ISC.listas }}</p>
 <p class="AbrilFont text-xs  text-center md:text-lg">Por evaluar: {{ info2.ISC.faltantes }}</p>
        </div>
   
     
    </details>
        </div>
</div>

      </div> <!--fin Contenedor 1.2  --> 



       <div class=""> <!--Contenedor 1.3  --> 
<!--info 2 -->
<div v-if="isLoading2" >Cargando...</div>
<div class="flex flex-row ">
        <div class="mb-4 ">


          <details v-if="info2.IEM" class="  dark:open:bg-orange/30 p-4 open:ring-1 open:ring-black/5 dark:open:ring-white/10 open:shadow-lg p-6 rounded-lg" open>
    <summary class=" dark:text-white  select-none text-white AbrilFont font-bold text-xl md:text-3xl text-center  bg-pink-950 w-80  rounded-full  ">IEM
    </summary>
    <div class=" rounded-lg backdrop-blur-sm bg-orange/30 p-4">
<p class="AbrilFont text-xs  text-center md:text-lg">Evaluaciones realizadas {{ info2.IEM.listas }}</p>
 <p class="AbrilFont text-xs  text-center md:text-lg">Por evaluar: {{ info2.IEM.faltantes }}</p>
        </div>
   
     
    </details>
        </div>
</div>

      </div> <!--fin Contenedor 1.3  --> 




       <div class=""> <!--Contenedor 1.4  --> 
<!--info 2 -->
<div v-if="isLoading2" >Cargando...</div>
<div class="flex flex-row ">
        <div class="mb-4 ">


          <details v-if="info2.IER" class="  dark:open:bg-orange/30 p-4 open:ring-1 open:ring-black/5 dark:open:ring-white/10 open:shadow-lg p-6 rounded-lg" open>
    <summary class=" dark:text-white  select-none text-white AbrilFont font-bold text-xl md:text-3xl text-center  bg-pink-950 w-80  rounded-full  ">IER
    </summary>
    <div class=" rounded-lg backdrop-blur-sm bg-orange/30 p-4">
<p class="AbrilFont text-xs  text-center md:text-lg">Evaluaciones realizadas {{ info2.IER.listas }}</p>
 <p class="AbrilFont text-xs  text-center md:text-lg">Por evaluar: {{ info2.IER.faltantes }}</p>
        </div>
   
     
    </details>
        </div>
</div>

      </div> <!--fin Contenedor 1.4  --> 

       <div class=""> <!--Contenedor 1.5  --> 
<!--info 2 -->
<div v-if="isLoading2" >Cargando...</div>
<div class="flex flex-row ">
        <div class="mb-4 ">


          <details v-if="info2.IE" class="  dark:open:bg-orange/30 p-4 open:ring-1 open:ring-black/5 dark:open:ring-white/10 open:shadow-lg p-6 rounded-lg" open>
    <summary class=" dark:text-white  select-none text-white AbrilFont font-bold text-xl md:text-3xl text-center  bg-pink-950 w-80  rounded-full  ">IE
    </summary>
    <div class=" rounded-lg backdrop-blur-sm bg-orange/30 p-4">
<p class="AbrilFont text-xs  text-center md:text-lg">Evaluaciones realizadas {{ info2.IE.listas }}</p>
 <p class="AbrilFont text-xs  text-center md:text-lg">Por evaluar: {{ info2.IE.faltantes }}</p>
        </div>
   
     
    </details>
        </div>
</div>
      </div> <!--fin Contenedor 1.5  --> 



       <div class=""> <!--Contenedor 1.6  --> 
<!--info 2 -->
<div v-if="isLoading2" >Cargando...</div>
<div class="flex flex-row ">
        <div class="mb-4 ">


          <details v-if="info2.II" class="  dark:open:bg-orange/30 p-4 open:ring-1 open:ring-black/5 dark:open:ring-white/10 open:shadow-lg p-6 rounded-lg" open>
    <summary class=" dark:text-white  select-none text-white AbrilFont font-bold text-xl md:text-3xl text-center  bg-pink-950 w-80  rounded-full  ">II
    </summary>
    <div class=" rounded-lg backdrop-blur-sm bg-orange/30 p-4">
<p class="AbrilFont text-xs  text-center md:text-lg">Evaluaciones realizadas {{ info2.II.listas }}</p>
 <p class="AbrilFont text-xs  text-center md:text-lg">Por evaluar: {{ info2.II.faltantes }}</p>
        </div>
   
     
    </details>
        </div>
</div>

      </div> <!--fin Contenedor 1.6   --> 




       







</div><!-- fin Contenedor  1.2.2-->


</div><!--Termina contenedor 3-->


    </div>
  </template>
<script setup>
import {onMounted, ref} from 'vue'




const info = ref ("");
const isLoading = ref ("");
const info2 = ref ("");
const isLoading2 = ref ("");

//en el frontend



async function fetchData() {
try {
    
const response = await fetch('https:/sitmotul.com.mx/api/statusEval');
const data = await response.json();

data.inicio = formatDate(data.inicio);
    data.fin = formatDate(data.fin);


info.value=data;
isLoading.value = false;
console.log (data);
}catch (error) {
 console.error('Error al obtener datos:', error);
  }
}

function formatDate(dateString) {
  const date = new Date(dateString);
  return `${date.getFullYear()}-${padZero(date.getMonth() + 1)}-${date.getDate()}`;
}

function padZero(value) {
  return value < 10 ? `0${value}` : value;
}




async function fetchData2() {
try {
    
const response = await fetch('https://sitmotul.com.mx/api/statusEvalIng');
const data = await response.json();

data.inicio = formatDate(data.inicio);
    data.fin = formatDate(data.fin);


info2.value=data;
isLoading2.value = false;
console.log (data);
}catch (error) {
 console.error('Error al obtener datos:', error);
  }
}
onMounted(() => {
  fetchData();
fetchData2();
})



</script>