<template>
 <div>
    <nav class="flex items-center justify-between flex-wrap bg-purple-400 p-6">
      <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">Nuxt Dupiter</span>
      </div>
       <!-- <select>
        <option>
          <nuxt-link :to="{ query: { lang: 'ta'}}">Tamil</nuxt-link>
        </option>
        <option>
          <nuxt-link :to="{ query: { lang: 'en'}}">English</nuxt-link>
        </option>
      </select> -->
      <div class=" xl:justify-around">
      <nuxt-link :to="{ query: { lang: 'ta'}}">Tamil</nuxt-link>
      <nuxt-link :to="{ query: { lang: 'en'}}">English</nuxt-link>
      </div>
      <!-- <select>
        <option :to="{ query: { lang: 'ta'}}">$1,000</option>
        <option :to="{ query: { lang: 'en'}}">$5,000</option>
      </select> -->
      <div class="block lg:hidden"></div>
    </nav>
    <Nuxt />
  </div>
</template>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
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
</style>
