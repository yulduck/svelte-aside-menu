<script lang="ts">
  import { fly } from 'svelte/transition'
  // import { flip } from 'svelte/animate'
  import AsideMenu from '$lib/AsideMenu.svelte'
  import FaChevronRight from 'svelte-icons/fa/FaChevronRight.svelte'
  import FaPlus from 'svelte-icons/fa/FaPlus.svelte'

  let inputRef;
  let image = '';
  let isSlideOpened = true;
  const toggleSlide = () => isSlideOpened = !isSlideOpened;
  const clickInput = () => inputRef.click()
</script>

<div class="w-full h-screen bg-gray-200">
<!-- {#if isSlideOpened} -->
  <aside class="fixed h-screen bg-black/60 rounded-r-3xl px-8 py-7 ptran" class:w-80={isSlideOpened} class:w-32={!isSlideOpened}>
  <!-- class:w-50={!isSlideOpened} class:w-80={isSlideOpened} > -->
    <div class="flex items-center mb-8">
      <!-- TODO: 반복되는 부분 Component화 하기 -->
      <div class="w-3 h-3 bg-red-500 rounded-full mr-1.5 drop-shadow-xl"></div>
      <div class="w-3 h-3 bg-yellow-500 rounded-full mr-1.5 drop-shadow-xl"></div>
      <div class="w-3 h-3 bg-green-500 rounded-full mr-1.5 drop-shadow-xl"></div>
    </div>

    <header class="relative flex mb-8">
      <div class="w-12 h-12 mr-4 overflow-hidden rounded-xl p-1 bg-white/10 border-white">
        <img class="block rounded-xl object-cover" src="https://ca.slack-edge.com/T030HSNLUTS-U02V57HAGF7-a8b0f252083c-512" alt="user">
      </div>
{#if isSlideOpened}
      <div class="flex flex-col">
        <p class="text-sm font-semibold"><span class="text-white/60">Hello</span> 👋</p>
        <strong class="text-white">Kenton Park</strong>
      </div>
      {/if}
      <button on:click={toggleSlide} class="absolute top-1/2 -right-12 -translate-y-1/2 flex justify-center items-center w-7 h-7 p-2 text-base rounded-full bg-blue-600 text-white {isSlideOpened && 'rotate-180'} transition-all">
        <FaChevronRight />
      </button>
    </header>
    <AsideMenu {isSlideOpened}/>
    <button on:click|stopPropagation={clickInput} class="flex flex-col justify-center items-center w-full py-8 rounded-lg " class:border-dashed={isSlideOpened} class:border={isSlideOpened} >
      <input class="sr-only" type="file" bind:this={inputRef} value={image}/>
      <div class="w-12 h-12 p-4 text-white rounded-full bg-blue-600 mb-3 drop-shadow-[0_0_rgba(28, 117, 253, 0.6)]">
        <FaPlus/>
      </div>
      <div>
        {#if isSlideOpened}
        <strong class="text-white">Upload new class</strong>
        <span class="block text-white/50">Drag and drop</span>
        {:else}
        <strong class="text-white">Upload</strong>
        {/if}
      </div>
    </button>
  </aside>
</div>
<style>
.ptran{
transition: width 0.5s;
}
</style>
