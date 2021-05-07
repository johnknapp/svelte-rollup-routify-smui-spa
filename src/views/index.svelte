<script>
  import {url} from '@roxi/routify'
  import Button, { Label, Icon } from '@smui/button';
  let clicked = 0;
</script>

<h1>i m index</h1>

<a href={$url('/pizza')}>Go for pizza</a>
<br />
<Button on:click={() => clicked++}>
  <Icon class="material-icons">favorite</Icon>
  <Label>Leading Icon</Label>
</Button>

<pre class="status">Clicked: {clicked}</pre>