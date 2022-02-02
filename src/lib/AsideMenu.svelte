<script lang="ts">
  export let isSlideOpened;
  import AsideMenuItem from './AsideMenuItem.svelte';
  import {IMenu} from '../type/MenuType';
  import MdDeveloperBoard from 'svelte-icons/md/MdDeveloperBoard.svelte'
  import FaCommentDots from 'svelte-icons/fa/FaCommentDots.svelte'
  import FaComments from 'svelte-icons/fa/FaComments.svelte'
  import TiChartArea from 'svelte-icons/ti/TiChartArea.svelte'
  import FaBookOpen from 'svelte-icons/fa/FaBookOpen.svelte'
  import DiTrello from 'svelte-icons/di/DiTrello.svelte'
 

  const MENU_ITEMS:IMenu[] = [
    {
      icon: MdDeveloperBoard,
      content: 'DashBorad',
      link: '#',
      sub_category:[]
    },
    {
      icon: FaCommentDots,
      content: 'Message',
      link: '#',
      sub_category:[]
    },
    {
      icon: FaComments,
      content: 'Chat',
      link: '#',
      sub_category:[]
    },
    {
      icon: TiChartArea,
      content: 'Challenges',
      link: '#',
      sub_category:[]
    },
    {
      icon: FaBookOpen,
      content: 'Classes',
      link: '#',
      sub_category:['Maths', 'English', 'Economics', 'Accounts']
    },
    {
      icon: DiTrello,
      content: 'TimeTable',
      link: '#',
      sub_category:[]
    },
  ]
</script>

<ul class="border-y border-white px-1 py-8 mb-6">
  {#each MENU_ITEMS as menu}
    <AsideMenuItem {menu} {isSlideOpened}/> 
  {/each}
</ul>
