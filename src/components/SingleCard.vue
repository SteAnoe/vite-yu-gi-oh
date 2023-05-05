<script>
export default{
  name: "SingleCard",
  props: ['infoCard'],
}
</script>

<template>
  
    <div class="text-center mb-3">
        <img :src="infoCard.card_images[0].image_url" alt="">
        <h5>{{ infoCard.name }}</h5>
        <div>{{ infoCard.archetype }}</div>
    </div>
  
</template>

<style lang="scss" scoped>
div.mb-3{
    background-color: #D48F38;
    width: calc(100%/5 - 30px);
    padding: 0;
    h5{
        padding-top: 15px;
    }
    div{
        padding-bottom: 5px;
    }
}
  img{
    width: 100%;
    
  }
</style>
