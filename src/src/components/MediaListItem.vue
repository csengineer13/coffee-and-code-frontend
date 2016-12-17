<template>
    <a href="#" class="item-link item-content">
      <div class="item-media"><img v-bind:src="mediaImage" width="80"></div>
      <div class="item-inner">
        <div class="item-title-row">
          <div class="item-title">Danny Brown</div>
          <div class="item-after">40 oz &nbsp;<i class="fa fa-coffee" aria-hidden="true"></i></div>
        </div>
        <!--<div class="item-subtitle">C# .NET Developer</div>-->
        <div class="item-text">
          <ul style="list-style-type: square; padding-left: 20px;">
            <li>Future Stat</li>
            <li>Future Stat</li>
          </ul>
        </div>
      </div>
    </a>
</template>

<script>
export default {
  name: 'media-list-item',
  props: ['media-image'],
  data: function(){
  	return {

  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
