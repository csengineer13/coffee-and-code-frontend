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
                  <div class="pin-placeholder" :class="{ 'has-value': pin.length > 0 }"></div>
                  <div class="pin-placeholder" :class="{ 'has-value': pin.length > 1 }"></div>
                  <div class="pin-placeholder" :class="{ 'has-value': pin.length > 2 }"></div>
                  <div class="pin-placeholder" :class="{ 'has-value': pin.length > 3 }"></div>
                </div>
              </div>


              <div class="list-block">
                <div class="list-block-label">
                  <p>Some text with login information.</p>
                  <p><a href="#" @click="closeLoginScreen">Close Login Screen</a></p>
                </div>
              </div>

              <div class="content-block">
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('1')">1</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('2')">2</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('3')">3</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('4')">4</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('5')">5</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('6')">6</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('7')">7</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('8')">8</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('9')">9</a>
                </p>
                <p class="buttons-row">
                  <a href="#" class="button button-fill color-red" @click="clearPinNumberTapped">Clear</a>
                  <a href="#" class="button button-fill color-blue" @click="pinNumberTapped('0')">0</a>
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
                <div class="center">Coffee <i class="fa fa-heart" aria-hidden="true"></i></div>
              </div>
            </div>
            <!-- /Navbar -->

            <!-- Toolbar -->
            <div class="toolbar toolbar-bottom">
              <div class="toolbar-inner">
                <!-- Toolbar links -->
                <a href="#" class="link" @click="routeToPage('index', $event)">Home</a>
              </div>
            </div>
            <!-- /Toolbar -->

            <div class="page-content">
            </div>
          </div>
          <!-- /About -->


          <!-- All pages, except initial, should have 'cached' class -->
          <!-- data-page=* is pageName -->
          <div class="page" data-page="questions">

            <!-- Navbar -->
            <div class="navbar">
              <div class="navbar-inner">
                <div class="center">Coffee <i class="fa fa-heart" aria-hidden="true"></i></div>
              </div>
            </div>
            <!-- /Navbar -->

            <!-- Toolbar -->
            <div class="toolbar toolbar-bottom">
              <div class="toolbar-inner">
                <!-- Toolbar links -->
                <a href="#" class="link" @click="signOut">Sign Out</a>
              </div>
            </div>
            <!-- /Toolbar -->

            <div class="page-content">

            <h1>{{activeUser.coffeeToday}} oz <i class="fa fa-coffee" aria-hidden="true"></i></h1>
            <span class="subheading">and counting (:</span>

              <div class="content-block-title">Add Coffee Intake</div>
              <div class="content-block">
                <div class="content-block-inner">
                  <p class="buttons-row">
                    <a href="#" class="button button-raised button-fill color-red" @click="addCoffee(4, $event)">4 oz</a>
                    <a href="#" class="button button-raised button-fill color-green" @click="addCoffee(6, $event)">6 oz</a>
                    <a href="#" class="button button-raised button-fill color-blue" @click="addCoffee(8, $event)">8 oz</a>
                  </p>
                  <p class="buttons-row">
                    <a href="#" class="button button-raised button-fill color-orange" @click="addCoffee(10, $event)">10 oz</a>
                    <a href="#" class="button button-raised button-fill color-pink" @click="addCoffee(12, $event)">12 oz</a>
                    <a href="#" class="button button-raised button-fill color-purple" @click="addCoffee(16, $event)">16 oz</a>
                  </p>
                  <!-- <img style="width: 10%;" src="./assets/coffee-cup.png" /> -->
                </div>
              </div>
            </div>
          </div>
          <!-- /Questions -->

          <!-- Page, "data-page" contains page name -->
          <div class="page" data-page="index">

            <!-- Top Navbar -->
            <div class="navbar">
              <div class="navbar-inner">
                <div class="center">fastidious</div>
              </div>
            </div><!-- /Top Navbar -->

            <!-- Toolbar -->
            <div class="toolbar toolbar-bottom">
              <div class="toolbar-inner">
                <!-- Toolbar links -->
                <a href="#" class="link" @click="routeToPage('about', $event)">About</a>
                <a href="#" class="link" @click="refreshUsers">Refresh Users</a>
              </div>
            </div><!-- /Toolbar -->

            <!-- Scrollable page content -->
            <div class="page-content">
              <div class="content-block-title">Users</div>
              
              <div class="list-block media-list">
                <ul>

                  <li v-for="user in users">
                    <media-list-item
                      @click.native="userTapped(user, $event)"
                      v-bind:media-image="user.userPicUrl"
                      v-bind:name="user.name"
                    ></media-list-item>
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
//import Vue from 'vue'
//import Vuex from 'vuex'
import Framework7 from 'Framework7'
import MediaListItem from './components/MediaListItem'
var $$ = Dom7;

// Kickstart vuex
//Vue.use(Vuex);

export default {
  name: 'app',
  components: {
    MediaListItem
  },
  data: function(){
    return {
      myApp: undefined,
      mainView: undefined,
      users: [],
      activeUser: {},
      pin: ""
    }
  },
  mounted: function()
  {
    var vm = this;

    /* Init Framework7 */
    this.myApp = new window.Framework7({
        root: '#app',               // Vue is not a fan of mounting to body
        material: true,             // Android
        materialPageLoadDelay: 50,  // Performance increase
        domCache: true,             // https://framework7.io/docs/pages-inline.html
        preroute: function (view, options) {
          if(options.pageName == 'index'){
            vm.refreshUsers();
          }
          //return false; //required to prevent default router action
          return true;
        }
    });

    /* Init Main View */
    this.mainView = this.myApp.addView('.view-main', {});
    vm.refreshUsers();

    /* Page Callbacks */
    // Important for binding as content is added/removed from DOM
    // http://framework7.io/docs/pages.html

  }, // mounted
  methods: {
    signIn: function(evt)
    {
      var vm = this;

      // Min 4 numbers
      if(this.pin.length != 4)
      { 
        this.signInFail();
        return;
      }

      $$.ajax({
        //method: "POST",
        //url: 'http://localhost:3000/account/signin',
        method: "GET",
        url: "http://localhost:3000/success/1",
        data: { userId: vm.activeUser.Id, pin: vm.pin },
        cache: false,
        success: vm.signInSuccess,
        error: vm.signInFail
      });
    },
    signInSuccess: function(data, status, xhr)
    {
      var loginScreen = this.myApp.loginScreen();
      this.myApp.closeModal(loginScreen);
      this.closeAllNotifications();
      this.mainView.router.load({pageName: 'questions'});
    },
    signInFail: function(xhr, status){
      this.myApp.addNotification({
          message: 'Incorrect Pin Number'
      });
      this.pin = "";
    },
    signOut: function(evt){
      this.mainView.router.load({pageName: 'index'});
    },
    closeAllNotifications: function()
    {
      var vm = this;
      $$(".notification-item").each(function(index, notificationElement){
        vm.myApp.closeNotification(notificationElement);
      });
    },
    closeLoginScreen: function(evt){
      evt.preventDefault();
      this.pin = "";
      this.closeAllNotifications();
      var loginScreen = this.myApp.loginScreen();
      this.myApp.closeModal(loginScreen);
    },
    userTapped: function(user, evt)
    {
      this.activeUser = user;
      this.myApp.loginScreen();
    },
    clearPinNumberTapped: function(){
      this.pin = "";
    },
    pinNumberTapped: function(number){
      if(this.pin.length < 4){
        this.pin += number;
      }
    },
    refreshUsers: function(evt)
    {
      var vm = this;

      $$.ajax({
        method: "GET",
        url: 'http://localhost:3000/users',
        cache: false,
        success: function(data, status, xhr){
          var object = JSON.parse(data);
          vm.users = object; 
        }
      });
    },
    routeToPage: function (pageName, evt) 
    {
      evt.preventDefault();
      this.mainView.router.load({pageName: pageName});
    },
    addCoffee: function(oz, evt){
      this.mainView.router.load({pageName: 'index'});
    }
  }
}
</script>

<style>
  h1 {
    text-align: center;
    margin-bottom: 5px;
  }
  .subheading {
    display:block;
    width: 100%;
    text-align: center;
  }

  .notifications {
    z-index: 11001; /* one higher than sign-in screen */
  }

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

  .pin-placeholder.has-value::after{
    content: "•";
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
