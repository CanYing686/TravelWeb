<template>
  <header>
    <a href="#" class="brand">Travel</a>
    <div class="menu-btn" :class="{active:active===true}" @click="btnClick"></div>
    <div class="navigation" :class="{active:active===true}" @click="btnClick">
      <div class="navigation-items">
        <a href="#" v-for="Item in navigation" :key="Item">{{ Item }}</a>
      </div>
    </div>
  </header>

  <section class="home">
    <video class="video" :src="item" v-for="(item,index) in video" autoplay muted loop :key="index" v-show="index===this.barNum-1"></video>
    <div class="content">
      <h1>Wonderful.
        <br/>
        <span>Island</span>
      </h1>

      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore
        magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
        pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est
        laborum.</p>
      <a href="#" class="btn">Read More</a>

      <div class="media-icons">
        <a href="#"><i class="fab fa-facebook-f"></i></a>
        <a href="#"><i class="fab fa-instagram"></i></a>
        <a href="#"><i class="fab fa-twitter"></i></a>
      </div>

      <div class="slider-navigation">
        <div class="nav-bar" v-for="item in video.length" :key="item" :class="{back:item===barNum}"
             @click="btn(item)"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      active: false,
      barNum: 1,
      navigation: [
        "Home", "About", "Explore", "Gallery", "Contact"
      ],
      video: [
        require('../../public/清除潜影贝子弹.mp4'),
        require('../../public/boxing.mp4')
      ]
    }
  },
  methods: {
    btnClick: function () {
      this.active = !this.active;
    },
    btn: function (value) {
      this.barNum = value


    },
  },
  mounted() {

  }
}
</script>

<style>

header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 200px;
  transition: .5s ease;
  z-index: 999;
}

header .brand {
  color: #fff;
  font-size: 1.5rem;
  font-weight: 700;
  text-transform: uppercase;
  text-decoration: none;
}

header .navigation {
  position: relative;
}

header .navigation .navigation-items a {
  position: relative;
  font-size: 1rem;
  font-weight: 500;
  text-decoration: none;
  color: #fff;
  margin-left: 30px;
  transition: .3s ease;
}

header .navigation .navigation-items a:before {
  content: '';
  position: absolute;
  background-color: #fff;
  bottom: 0;
  width: 0;
  left: 0;
  height: 2px;
  transition: .3s ease;

}

header .navigation .navigation-items a:hover:before {
  width: 100%;
}

section {
  padding: 100px 200px;
  position: relative;
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  background-color: #2696E9;
}

section:before {
  z-index: 777;
  content: '';
  background-color: rgba(139, 251, 3, 0.1);
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  position: absolute;
}

.content {
  color: #fff;
  margin-top: 50px;
}

.home .content {
  z-index: 888;

}

.content h1 {
  font-size: 4em;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 5px;
  line-height: 75px;
  margin-bottom: 40px;
}

.content h1 span {

  font-size: 1.2em;
  font-weight: 600;
}

.content p {
  width: 70%;
  margin-bottom: 65px;
}

.content .btn {
  background: #fff;
  padding: 15px 35px;
  color: #1680AC;
  font-size: 1.1em;
  font-weight: 500;
  text-decoration: none;
  border-radius: 2px;
}

.media-icons {
  position: absolute;
  right: 30px;
  display: flex;
  flex-direction: column;
  transition: .5s ease;
  top: 50%;
}

.media-icons a {
  color: #fff;
  font-size: 1.6em;
  transition: .3s ease;
}

.media-icons a:hover {
  transform: scale(1.3);
}

.media-icons a:not(:last-child) {
  margin-bottom: 20px;
}

.home video {
  z-index: 000;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  object-fit: fill;
}

.home video.back {
  z-index: 000;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  transition: 2s ease;
}


.slider-navigation {

  z-index: 888;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  transform: translateY(80px);
  margin-bottom: 12px;
}

.nav-bar {
  width: 12px;
  height: 12px;
  background-color: #fff;
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0 0 2px rgba(255, 255, 255, .5);
  transition: .3s ease;
}

.back {
  background-color: #000;
}

.nav-bar:not(:last-child) {
  margin-right: 20px;
}

.nav-bar:hover {
  transform: scale(1.2);
}

@media (max-width: 1040px) {
  header {
    padding: 12px 20px
  }

  section {
    padding: 100px 20px;
  }

  .media-icons {
    right: 15px;
  }

  header .navigation {
    display: none;
  }

  header .navigation.active {
    position: fixed;
    width: 100%;
    height: 100vh;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(1, 1, 1, 0.5);
  }

  header .navigation.active .navigation-items {
    background-color: #fff;
    width: 600px;
    max-width: 600px;
    margin: 20px;
    padding: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 5px;
    box-shadow: 0 5px 25px rgb(1 1 1 / 20%);
  }

  header .navigation .navigation-items a {
    color: #222;
    font-size: 1.2em;
    margin: 20px;
  }

  header .navigation .navigation-items a:before {
    background-color: #222;
    height: 4px;
  }

  .menu-btn {
    background: url("../../public/menu.png") no-repeat center;
    background-size: 30px;
    width: 40px;
    height: 40px;
    cursor: pointer;
    transition: .3s ease;
  }

  .menu-btn.active {
    z-index: 999;
    background: url("../../public/close.png") no-repeat center;
    background-size: 25px;
    transition: .3s ease;

  }
}


</style>
