<script lang="ts">
  import { fly } from 'svelte/transition'
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
{#if isSlideOpened}
  <aside in:fly="{{ x: -200, duration: 1000 }}" out:fly="{{ x: -200, duration: 1000}}" class="fixed {!isSlideOpened && '-translate-x-60'} h-screen bg-black/60 rounded-r-3xl w-80 px-8 py-7 transition-transform duration-700">
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
      <div class="flex flex-col">
        <p class="text-sm font-semibold"><span class="text-white/60">Hello</span> 👋</p>
        <strong class="text-white">Kenton Park</strong>
      </div>
      <button on:click={toggleSlide} class="absolute top-1/2 -right-12 -translate-y-1/2 flex justify-center items-center w-7 h-7 p-2 text-base rounded-full bg-blue-600 text-white {isSlideOpened && 'rotate-180'} transition-all">
        <FaChevronRight />
      </button>
    </header>
    <AsideMenu {isSlideOpened}/>
    <button on:click|stopPropagation={clickInput} class="flex flex-col justify-center items-center w-full py-8 border-dashed border rounded-lg ">
      <input class="sr-only" type="file" bind:this={inputRef} value={image}/>
      <div class="w-12 h-12 p-4 text-white rounded-full bg-blue-600 mb-3 drop-shadow-[0_0_rgba(28, 117, 253, 0.6)]">
        <FaPlus/>
      </div>
      <div>
        <strong class="text-white">Upload new class</strong>
        <span class="block text-white/50">Drag and drop</span>
      </div>
    </button>
  </aside>

{:else}
  <aside in:fly="{{ x: 100, duration: 1000 }}" class="fixed flex flex-col items-center h-screen bg-black/60 rounded-r-3xl w-44 px-8 py-7 transition-transform duration-700">
    <div class="flex items-center mb-8">
      <!-- TODO: 반복되는 부분 Component화 하기 -->
      <div class="w-3 h-3 bg-red-500 rounded-full mr-1.5 drop-shadow-xl"></div>
      <div class="w-3 h-3 bg-yellow-500 rounded-full mr-1.5 drop-shadow-xl"></div>
      <div class="w-3 h-3 bg-green-500 rounded-full mr-1.5 drop-shadow-xl"></div>
    </div>

    <header class="relative flex mb-8">
      <div class="w-12 h-12 overflow-hidden rounded-xl p-1 bg-white/10 border-white">
        <img class="block rounded-xl object-cover" src="https://ca.slack-edge.com/T030HSNLUTS-U02V57HAGF7-a8b0f252083c-512" alt="user">
      </div>
      <button on:click={toggleSlide} class="absolute top-1/2 -right-20 -translate-y-1/2 flex justify-center items-center w-7 h-7 p-2 text-base rounded-full bg-blue-600 text-white {isSlideOpened && 'rotate-180'} transition-all">
        <FaChevronRight />
      </button>
    </header>
    <AsideMenu {isSlideOpened}/>
    <button on:click|stopPropagation={clickInput} class="flex flex-col justify-center items-center w-full py-8 ">
      <input class="sr-only" type="file" bind:this={inputRef}/>
      <div class="w-12 h-12 p-4 text-white rounded-full bg-blue-600 drop-shadow-xl mb-3">
        <FaPlus/>
      </div>
      <div>
        <strong class="text-white">Upload</strong>
      </div>
    </button>
  </aside>
{/if}

</div>