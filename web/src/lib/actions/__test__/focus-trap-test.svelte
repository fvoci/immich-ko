<script lang="ts">
  import { focusTrap } from '$lib/actions/focus-trap';

  interface Props {
    show: boolean;
    active?: boolean;
  }

  let { show = $bindable(), active = $bindable() }: Props = $props();
</script>

<button type="button" onclick={() => (show = true)}>Open</button>

{#if show}
  <div use:focusTrap={{ active }}>
    <div>
      <span>text</span>
      <button data-testid="one" type="button" onclick={() => (show = false)}>Close</button>
    </div>
    <input data-testid="two" disabled />
    <input data-testid="three" />
  </div>
{/if}
