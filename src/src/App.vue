<template>
  <div id="app">

    <div class="login-screen">
      <div class="view">
        <div class="page">
          <div class="page-content login-screen-content">

            <div class="login-screen-title">Enter Pin</div>
            
            <form>
              <div class="content-block">
                <div class="pin-container">
                  <div class="pin-placeholder empty">&#8226;</div>
                  <div class="pin-placeholder empty">&#8226;</div>
                  <div class="pin-placeholder empty"></div>
                  <div class="pin-placeholder empty"></div>
                </div>
              </div>


              <div class="list-block">
                <div class="list-block-label">
                  <p>Some text with login information.</p>
                  <p><a href="#" class="close-login-screen">Close Login Screen</a></p>
                </div>
              </div>

              <div class="content-block">
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue">1</a>
                  <a href="#" class="button button-fill color-blue">2</a>
                  <a href="#" class="button button-fill color-blue">3</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue">4</a>
                  <a href="#" class="button button-fill color-blue">5</a>
                  <a href="#" class="button button-fill color-blue">6</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue">7</a>
                  <a href="#" class="button button-fill color-blue">8</a>
                  <a href="#" class="button button-fill color-blue">9</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-red">Clear</a>
                  <a href="#" class="button button-fill color-blue">0</a>
                  <a href="#" class="button button-fill color-green" @click="signIn">Submit</a>
                </p>
              </div>
            </form>

          </div>
        </div>
      </div>
    </div> <!-- /login-screen -->



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
    signIn: function(evt)
    {
      var loginScreen = this.myApp.loginScreen();
      this.myApp.closeModal(loginScreen);
      this.mainView.router.load({pageName: 'about'});
    },
    signOut: function(evt){
      this.mainView.router.load({pageName: 'index'});
    },
    refreshUsers: function(evt){
      // not implemented
    },
    routeToPage: function (pageName, evt) 
    {
      evt.preventDefault();
      this.mainView.router.load({pageName: pageName});
    }
  }
}
</script>

<style>
  .pin-placeholder {
    width: 50px;
    height: 50px;
    margin: 0 3px;
    border: 1px solid black;

    font-size: 22px;
    line-height: 48px;
    text-align: center;

    float: left;

    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
  }

  .pin-container::after {
    content: ' ';
    display: block;
    clear: both;
  }

  .pin-container {
    margin: 0 auto;
    width: 225px;
  }
</style>
