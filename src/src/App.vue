<template>
  <div id="app" class="views">
    

    <!-- Your main view, should have "view-main" class -->
    <div class="view view-main">
      <!-- Pages container, because we use fixed navbar and toolbar, it has additional appropriate classes-->
      <div class="pages navbar-fixed toolbar-fixed">
        <!-- Page, "data-page" contains page name -->
        <div data-page="index" class="page">

          <!-- Top Navbar. In Material theme it should be inside of the page-->
          <div class="navbar">
            <div class="navbar-inner">
              <div class="center">Awesome App</div>
            </div>
          </div>

          <!-- Toolbar. In Material theme it should be inside of the page-->
          <div class="toolbar">
            <div class="toolbar-inner">
              <!-- Toolbar links -->
              <a href="#" class="link">Link 1</a>
              <a href="#" class="link">Link 2</a>
            </div>
          </div>

          <!-- Scrollable page content -->
          <div class="page-content">
            <p>Page content goes here</p>
            <!-- Link to another page -->
            <a href="about.html">About app</a>
          </div>
        </div>
      </div>
    </div>

    <!-- -->

  </div>
</template>

<script>
// Framework7
import Framework7 from 'Framework7'

export default {
  name: 'app',
  components: {},
  mounted: function(){
    window.myApp = new window.Framework7({
        root: '#app',
        material: true,             // Android
        materialPageLoadDelay: 50,  // Performance increase
        domCache: true              // https://framework7.io/docs/pages-inline.html
    });

    /* Initialize views */
    var mainView = myApp.addView('.view-main', {
      dynamicNavbar: true
    });
    //var anotherView = myApp.addView('.another-view');

  } // mounted
}
</script>

<style>
</style>
