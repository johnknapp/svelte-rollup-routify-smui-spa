<script>
  import {url} from '@roxi/routify'

  import Tab, { Label } from '@smui/tab/styled';
  import TabBar from '@smui/tab-bar/styled';
  import Button from '@smui/button/styled';
  
  let active = 'Home';
</script>

<div>
  <!--
    Copied from here: https://github.com/hperrin/svelte-material-ui/blob/master/site/src/routes/demo/tabs/_Simple.svelte
  -->  
  <TabBar tabs={['Home', 'Merchandise', 'About Us']} let:tab bind:active>
    <!-- Note: the `tab` property is required! -->
    <Tab {tab}>
      <Label>{tab}</Label>
    </Tab>  
  </TabBar>  

  <div style="margin-top: 1em;">
    <div>Programmatically select:</div>
    {#each ['Home', 'Merchandise', 'About Us'] as tab}
      <Button on:click={() => (active = tab)}><Label>{tab}</Label></Button>
    {/each}  
  </div>  

  <pre class="status">Selected: {active}</pre>
</div>  

<a href={$url('/')}>Go for index</a>