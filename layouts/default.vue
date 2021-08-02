<template>
  <div class="wrapper">
  	<AnimatedCity />
    <Header />
    <nuxt />
    <ColorModePicker />
  </div>
</template>

<style>

/* purgecss ignore */
.video-container {
  position: relative;
  padding-bottom: 56.25%; /*16:9*/
  padding-top: 30px; 
  height: 0; 
  overflow: hidden;
  margin: 2rem 0px;
  position: sticky;
  top: 65px;
}
/* purgecss ignore */
.video-container iframe,
.video-container object,
.video-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

</style>