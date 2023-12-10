<script setup>
 import {ref,onMounted,nextTick } from 'vue';
 import {items} from "../assets/carousel.js";
 const newImg = ref("src/img/img1.jpg");
 onMounted(()=>{
    new Flickity('#carousel');
 });
 function add(){
	items.value.push(newImg.value);
	new Flickity('#carousel').destroy(); 
	nextTick(()=>{
	  new Flickity('#carousel');
	});
 }
</script>
<template>
	<div class="row">
		<div class="col-1">
	       <button @click="add()" :class="(items.length > 10) ? 'disabled':''" class="btn btn-primary">Add</button>
	    </div>
	</div>
	<br>
	<div class="row">
		<div class="col-12" id="carousel">
		    <div :style="`background-image:url('${item}')`" class="ImgDiv" v-for="(item,i) in items" :key="i">
		    {{ i+1 }}
		   </div>
	 	</div>
	</div>
</template>
<style scoped>

div.col-12 {
    text-align: center;
}
.ImgDiv {
  	width:100%;
    height: 400px;
    margin: auto;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    color: #1dff26;
    font-weight: bold;
    font-size: 99px;
}

div#carousel {
    width: 800px;
    margin: auto;
}
</style>