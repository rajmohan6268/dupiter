<template>
  <div>
    <nav style="background-color:#00bcd4" class="flex items-center justify-between flex-wrap  p-6">
          <!-- <nav class="flex items-center justify-between flex-wrap bg-purple-400 p-6"> -->
      <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">
          <img src="filter.svg" alt="dupiter logo" width="40" height="50" /> Nuxt Dupiter
        </span>
      </div>
      <!-- <select>
        <option>
          <nuxt-link :to="{ query: { lang: 'ta'}}">Tamil</nuxt-link>
        </option>
        <option>
          <nuxt-link :to="{ query: { lang: 'en'}}">English</nuxt-link>
        </option>
      </select>-->
      <div class="xl:justify-around text-white">
        <nuxt-link :to="{ query: { lang: 'ta'}}">தமிழ்</nuxt-link>
        <nuxt-link :to="{ query: { lang: 'en'}}">English</nuxt-link>
      </div>
      <!-- <select>
        <option :to="{ query: { lang: 'ta'}}">$1,000</option>
        <option :to="{ query: { lang: 'en'}}">$5,000</option>
      </select>-->
      <div class="block lg:hidden"></div>
    </nav>
    <Nuxt />
    <div style="background-color:#00bcd4" class=" footr sm:absolute w-full  text-center py-4 lg:px-4">
    <!-- <div class=" footr sm:absolute w-full bg-indigo-900 text-center py-4 lg:px-4"> -->
      <div
        class="p-2 items-center text-indigo-100 leading-none lg:rounded-full flex lg:inline-flex"
      >
        <h4><img src="logo.png" alt="lmes logo" width="100" height="50" /> © Lmes</h4>
        <!-- <span class="flex rounded-full bg-indigo-500 uppercase px-2 py-1 text-xs font-bold mr-3">New</span> -->
        <!-- <span class="font-semibold mr-2 text-left flex-auto">Get the coolest t-shirts from our brand new store</span> -->
        <!-- <svg class="fill-current opacity-75 h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M12.95 10.707l.707-.707L8 4.343 6.586 5.757 10.828 10l-4.242 4.243L8 15.657l4.95-4.95z"/></svg> -->
      </div>
    </div>
  </div>
</template>

<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
.footr {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
}
</style>
