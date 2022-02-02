<script lang="ts">
  import {IMenu} from '../type/MenuType';
  import {slide} from 'svelte/transition'
  import ChatController from './ChatController.svelte';
  import FaChevronRight from 'svelte-icons/fa/FaChevronRight.svelte'
 
  export let menu:IMenu, isSlideOpened;
  const {link, icon, content, sub_category} = menu;
  let isAcodianOpened = false;
  const handleAcodianToggle = () => isAcodianOpened = !isAcodianOpened;

</script>


<li class="{!isSlideOpened && 'flex justify-center'}">
  <a href={link} class="relative flex items-center {isSlideOpened ? 'mr-3': 'm-0'} {!isAcodianOpened && 'mb-8'}">
    <div class="w-6 y-6 {isSlideOpened ? 'mr-3': 'm-0'} text-white/60" aria-hidden="true">
      <!-- TODO: HOC 개념 보고 적용 해 볼 것 -->
      <svelte:component this={icon}/>
      <!-- {#if icon==='MdDeveloperBoard'} -->
      <!--   <MdDeveloperBoard/> -->
      <!-- {:else if  icon === 'FaCommentDots'} -->
      <!--   <div class="relative"> -->
      <!--     <FaCommentDots/> -->
      <!--     <div class="absolute -top-1 -right-1.5 flex justify-center items-center w-3.5 h-3.5 bg-orange-400 rounded-full text-black text-sm">3</div> -->
      <!--   </div> -->
      <!-- {:else if  icon === 'FaComments'} -->
      <!--   <FaComments /> -->
      <!-- {:else if icon === 'TiChartArea'} -->
      <!--   <TiChartArea/> -->
      <!-- {:else if icon === 'FaBookOpen'} -->
      <!--   <FaBookOpen/> -->
      <!-- {:else if icon === 'DiTrello'} -->
      <!--   <DiTrello /> -->
      <!-- {/if} -->
    </div>
    {#if isSlideOpened}
      <span class="text-lg text-white/80">
        {content}
      </span>
      {#if content==='Chat'}
        <ChatController />
      {/if}
      {#if sub_category[0]}
      <button on:click|stopPropagation={handleAcodianToggle} class="absolute top-1/2 -translate-y-1/2 right-0 w-3 y-3 text-white {isAcodianOpened ? '-rotate-90' : 'rotate-90'} transition-all" >
        <FaChevronRight />
      </button>
      {/if}
    {/if}
  </a>
  
  {#if sub_category[0]&&isAcodianOpened}
    <ul transition:slide class="last:mb-5">
      {#each sub_category as category}
      <li class="text-white/80 text-md font-light pl-8 px-5 py-3 ">
        <a href="#">{category}</a>
      </li>
      {/each}
    </ul>
  {/if}

  </li>
