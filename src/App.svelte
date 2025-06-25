<script>
  import {ContentSwitcher,Switch} from 'carbon-components-svelte';
  import Online from './lib/online.svelte';
  import Offline from './lib/offline.svelte';
    import Mergecheck from './lib/mergecheck.svelte';
    import Mergecheck2 from './lib/mergecheck2.svelte';


  let currentpage="online";
  function handleSwitch(page){
    currentpage=page;
  }

</script>

<style>
  .switch {
    position: absolute;
    top: 0; /* Aligns to the top */
    left: 0; /* Aligns to the left */
    padding: 10px; /* Optional: Adds some padding */
  }
  .switch{
    width: 175px; /* Set desired width here */
  }
</style>

<div class="switch">
<ContentSwitcher  size='sm'>
  <Switch text="online" on:click= {()=> handleSwitch('online')}/>
  <Switch text="offline" on:click={()=>handleSwitch('offline')}/>
  <Switch text="mergecheck" on:click={()=>handleSwitch('mergecheck')}/>
  <Switch text="mergecheck2" on:click={()=>handleSwitch('mergecheck2')}/>
</ContentSwitcher>
</div>

<div class="pages">
  {#if currentpage === 'online'}
    <Online />  <!-- Render Online component -->
  {:else if currentpage === 'offline'}
    <Offline /> <!-- Render Offline component -->
  {:else if currentpage === 'mergecheck'}
    <Mergecheck />
  {:else}
    <Mergecheck2 />
  {/if}
</div>