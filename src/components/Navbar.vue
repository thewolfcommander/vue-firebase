<template>
  <nav>
    <div class="nav-left">
      <h1>Manoj Tyagi</h1>
    </div>
    <div class="nav-right">
      <ul>
        <li><a href="">Home</a></li>
        <li><a href="">About</a></li>
        <li><a href="">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data () {
    return {

    }
  }
}
</script>

<style>
nav {
  background: teal;
  width: 100%;
  display: flex;
  min-height: 50px;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 4px rgba(0,0,0,0.15);
}

.nav-left {
  width: 50%;
  height: auto;
  padding: 10px 30px;
  vertical-align: middle;
}

nav h1 {
  color: #fff;
}

.nav-right {
  width: 50%;
  height: auto;
  vertical-align: middle;
  color: white;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
