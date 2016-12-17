<template>
  <div id="app">
    <div class="views">
      <div class="view view-main">
        <div class="pages navbar-fixed toolbar-fixed">
          

          <!-- All pages, except initial, should have 'cached' class -->
          <!-- data-page=* is pageName -->
          <div class="page" data-page="about">

            <!-- Navbar -->
            <div class="navbar">
              <div class="navbar-inner">
                <div class="center">Awesome App</div>
              </div>
            </div>
            <!-- /Navbar -->

            <!-- Toolbar -->
            <div class="toolbar">
              <div class="toolbar-inner">
                <!-- Toolbar links -->
                <a href="#" class="link" @click="routeToPage('index', $event)">Home</a>
                <a href="#" class="link">Link 2</a>
              </div>
            </div>
            <!-- /Toolbar -->

            <div class="page-content">
              <p>About Page</p>
                  <!-- <img style="width: 10%;" src="./assets/coffee-cup.png" /> -->
            </div>
          </div>
          <!-- /About -->

          <!-- Page, "data-page" contains page name -->
          <div class="page" data-page="index">

            <!-- Top Navbar -->
            <div class="navbar">
              <div class="navbar-inner">
                <div class="center">Awesome App</div>
              </div>
            </div><!-- /Top Navbar -->

            <!-- Toolbar -->
            <div class="toolbar">
              <div class="toolbar-inner">
                <!-- Toolbar links -->
                <a href="#" class="link" @click="routeToPage('about', $event)">About</a>
                <a href="#" class="link">Link 2</a>
              </div>
            </div><!-- /Toolbar -->

            <!-- Scrollable page content -->
            <div class="page-content">
              <div class="content-block-title">Users</div>
              
              <div class="list-block media-list">
                <ul>

                  <li>
                    <a href="#" class="item-link item-content">
                      <div class="item-media"><img src="http://placehold.it/80x80" width="80"></div>
                      <div class="item-inner">
                        <div class="item-title-row">
                          <div class="item-title">Danny Brown</div>
                          <div class="item-after">40 oz &nbsp;<i class="fa fa-coffee" aria-hidden="true"></i></div>
                        </div>
                        <!--<div class="item-subtitle">C# .NET Developer</div>-->
                        <div class="item-text">
                          <ul style="list-style-type: square; padding-left: 20px;">
                            <li>asd</li>
                            <li>asd</li>
                          </ul>
                        </div>
                      </div>
                    </a>
                  </li>

                </ul><!-- /list -->
              </div><!-- /list-block -->

            </div><!-- /page-content -->

          </div><!-- /page:index -->


        </div><!-- /pages -->
      </div><!-- /view -->
    </div><!-- /views -->
  </div><!-- /app -->
</template>

<script>
// Framework7
import Framework7 from 'Framework7'

export default {
  name: 'app',
  components: {},
  data: function(){
    return {
      myApp: undefined,
      mainView: undefined
    }
  },
  mounted: function()
  {
    /* Init Framework7 */
    this.myApp = new window.Framework7({
        root: '#app',               // Vue is not a fan of mounting to body
        material: true,             // Android
        materialPageLoadDelay: 50,  // Performance increase
        domCache: true              // https://framework7.io/docs/pages-inline.html
    });

    /* Init Main View */
    this.mainView = this.myApp.addView('.view-main', {});

  }, // mounted
  methods: {
    routeToPage: function (pageName, evt) 
    {
      evt.preventDefault();
      this.mainView.router.load({pageName: pageName});
    }
  }
}
</script>

<style>
</style>
