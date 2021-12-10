<template>
  <div class="dishcard">
    
    <div class="image">
    <slot name="image"></slot>
    </div>

    <div class="description">
    <slot name="description" class="description"></slot>
    </div>
    
    
  </div>
</template>
<script>

</script>
<style scoped>
.dishcard{
    text-align: center;
    display: flex;
    background-color: rgb(221, 216, 216);
    margin: 1rem;
}
.description{
  display: flex;
  flex-direction: column;
  width: 300px;
  margin: 1rem;
}
</style>
