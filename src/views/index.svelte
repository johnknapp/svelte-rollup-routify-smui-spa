<script>
  import {url} from '@roxi/routify'
  import Button, { Label, Icon } from '@smui/button';
  let clicked = 0;
</script>

<style>
  .i-m-red {
    color: red;
  }
</style>

<h1 class="i-m-red">i m index. m i red?</h1>

<a href={$url('/pizza')}>Go for pizza</a>

<a href={$url('/tabs')}>Go for tabs</a>
<br />
<br />
<Button on:click={() => clicked++} variant="raised">
  <Icon class="material-icons">thumb_up</Icon>
  <Label>i m button. m i raised and all caps?</Label>
</Button>

<pre class="status">Clicked: {clicked}</pre>