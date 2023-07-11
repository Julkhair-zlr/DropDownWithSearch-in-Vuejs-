<template>
  <div class="flex p-2 justify-between items-center">
    <h1>SeekGeak</h1>
    <div
      class="border-2 border-gray-400 flex rounded-lg overflow-hidden w-[30%]"
    >
      <img
        class="w-8"
        src="https://png.pngtree.com/png-vector/20190115/ourmid/pngtree-vector-search-icon-png-image_320926.jpg"
        alt="Search icon"
      />
      <input
        @click="toggleShowBorder"
        type="text"
        placeholder="Search..."
        class="outline-none w-full p-1"
      />
      <button
        @click="toggleShowBorder"
        class="bg-blue-800 w-[20%] p-1 text-white font-bold cursor-pointer tracking-tight"
      >
        Search
      </button>
    </div>
    <div
      v-bind:style="
        showRedBorder ? 'border: 1px solid red;' : 'border: 1px solid #000;'
      "
      class="absolute top-[5%] left-[35.8%] border-2 border-gray-400 w-[25%] h-auto bg-white py-2 px-5 flex gap-5"
    >
      <div>
        <ul>
          <li>apple1</li>
          <li>apple2</li>
          <li>apple3</li>
          <li>apple4</li>
          <li>apple5</li>
          <li>apple6</li>
        </ul>
      </div>
      <div class="border-l-2"></div>
      <div>
        <ul>
          <li>apple1</li>
          <li>apple2</li>
          <li>apple3</li>
          <li>apple4</li>
          <li>apple5</li>
          <li>apple6</li>
        </ul>
      </div>
    </div>
    <p>Profile</p>
  </div>
</template>
<script>

</script>
