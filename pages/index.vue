<template>
  <div class="container mx-auto">
    <!-- <input type="file" @change="chooseFile($event)" /> -->
    <!-- <select v-model="headerToClean">
      <option v-for="(h, index) in headers" :key="index" :value="h">{{ h }}</option>
    </select>-->
    <!-- <button @click="downloadCSV()">{{ $t('downloadText') }}</button>
    <br />-->
    <!-- <nuxt-link :to="{ query: { lang: 'ta'}}">Tamil</nuxt-link>
    <nuxt-link :to="{ query: { lang: 'en'}}">English</nuxt-link>
    <div>
      <select>
        <option :to="{ query: { lang: 'ta'}}">$1,000</option>
        <option :to="{ query: { lang: 'en'}}">$5,000</option>
      </select> -->
    <div class="md:flex p-8">
      <div class="md:flex-shrink-0">
        <div class="flex items-center">
          <label
            class="flex  flex-col items-center px-4 py-6 rounded-lg shadow-lg tracking-wide uppercase border border-indigo-700 cursor-pointer hover:text-indigo-900"
          >
            <svg
              class="w-8 h-8 "
              fill="#90cdf4"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
            >
              <path
                d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z"
              />
            </svg>
            <h1 :v-if="!fileContent"><span class="mt-2 text-base leading-normal">{{ $t('selectafile') }}</span></h1>
            <input type="file" class="hidden" @change="chooseFile($event)" />
            <!-- <input type="file"  @change="chooseFile($event) class="hidden" /> -->
          </label>
          <!-- <h1 :v-if="fileContent">{{ file.name }}selected </h1> -->
        </div>
      </div>
      <div class="mt-4 md:mt-0 md:ml-6">
        <label class="block mt-4">
          <span class="text-gray-700"><strong class=" rounded-lg">{{ $t('slctfld') }}</strong>
            <select v-model="headerToClean" class="form-select mt-1 block w-full border border-indigo-700">
              <option v-for="(h, index) in headers" :key="index" :value="h">{{ h }}</option>
            </select></span>
        </label>
        <div class="p-3"><!-- <button class=" p-3 bg-purple-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-full" @click="downloadCSV()"><div>{{ $t('downloadText') }}</div></button> --><!-- <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z"/></svg> -->
        <!-- <button style="background-color:#ff5722" class=" p-3  hover:bg-green-700 text-white font-bold py-2 px-4 rounded-full" @click="downloadCSV()"><div><svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z"/></svg>{{ $t('downloadText') }}</div></button> -->
        <!-- <button  class=" p-3  bg-red-400 hover:bg-green-400 text-white font-bold py-2 px-4 rounded-full" @click="downloadCSV()"><div>{{ $t('downloadText') }}</div></button> -->
      <button  class=" p-3 transition duration-500 ease-in-out bg-red-400 hover:bg-green-400  transform hover:-translate-y-1 hover:scale-110 text-white font-bold py-2 px-4 rounded-full" @click="downloadCSV()"><div>{{ $t('downloadText') }}</div></button>
       </div><!-- <a
            href="#"
            class="block mt-1 text-lg leading-tight font-semibold text-gray-900 hover:underline"
          >Finding customers for your new business</a>
          <p
            class="mt-2 text-gray-600"
          >Getting a new business off the ground is a lot of hard work. Here are five ideas you can use to find your first customers.</p>-->
      </div>
    </div>
    <!-- <h1>data</h1> -->
    <!-- <table style="width:100%">
      <tr v-bind:v-for="a in headerToClean" ><th>{{ a }}</th> </tr>
      </table> -->

  </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";

let file: any = "";
let objectStore: any = {};
let cleanData: any[] = [];

export default Vue.extend({
  middleware: "i18n",
  data() {
    return {
      fileContent: "",
      headerToClean: "",
      data: [],
      headers: [] as any,
      csvOutput: "",
    };
  },
  mounted() {},
  methods: {
    chooseFile(event: any) {
      file = event.target.files[0];

      if (!file) {
        alert("Please choose a file");
        return true;
      }
console.log(file.name)
      // Read the file content
      const reader: FileReader = new FileReader();
      reader.readAsText(file);
      reader.onload = () => {
        this.fileContent = reader.result as string;
        this.parseCSV(this.fileContent);
if (file) {
        alert(" you have selected a file ! now chooose the field you want to remove duplicates");
        return true;
      }
      };
    },
    // Parsing the CSV Headers and Data
    parseCSV(fileContent: string) {
      const lineArray = fileContent.split("\n");
      this.headers = lineArray[0].split(",") as [];
      const data: any = [];

      lineArray.splice(1).forEach((line) => {
        data.push(line.split(","));
      });
      this.data = data;
    },
    // Removing the duplicates in CSV File
    removeDuplicates() {
      const index = this.headers.indexOf(this.headerToClean);
      cleanData = [];
      objectStore = {};
      this.data.forEach((row) => {
        if (!objectStore[row[index]]) {
          objectStore[row[index]] = row;
          cleanData.push(row);
        }
      });
    },
    // Rebuilding the CSV File from Text Data
    buildCSVFile() {
      this.csvOutput = "";
      this.csvOutput = this.headers.join(",") + "\n";
      cleanData.forEach((row: any[]) => {
        this.csvOutput += row.join(",") + "\n";
      });
    },
    // Process and Download as CSV File
    downloadCSV() {
      this.removeDuplicates();
      this.buildCSVFile();
      const element = document.createElement("a");
      element.setAttribute(
        "href",
        "data:text/csv;charset=utf-8," + encodeURIComponent(this.csvOutput)
      );
      element.setAttribute("download", "output.csv");
      element.style.display = "none";
      document.body.appendChild(element);
      element.click();
      document.body.removeChild(element);
    },
  },
});
</script>

<style>
</style>

