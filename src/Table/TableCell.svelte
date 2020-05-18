<script>
  export let type;
  export let data;
  export let field;
  export let formatter;
  export let accessor;
  export let align;
  export let hideMobile;
  export let config;
  export let component;
  export let props;
</script>

<style>
  @media (max-width: 680px) {
    .hideMobile {
      display: none;
    }
  }
  .align-right {
    text-align: right;
  }

  .align-left {
    text-align: left;
  }

  .align-center {
    text-align: center;
  }

  .currency {
    font-family: "Helvetica Neue";
  }

  td {
    position: relative;
    padding: 12px 9px;
    line-height: 1.67;
  }
</style>

<td class={`align-${align} ${type || ''}`} class:hideMobile>
  {#if formatter && accessor}
    {@html formatter(accessor(data))}
  {:else if formatter}
    {@html formatter(data[field])}
  {:else if component}
    <svelte:component this={component} {...props(data)} />
  {:else if type === 'image' && typeof config.getSrc === 'function'}
    <img
      src={config.getSrc(data)}
      class="table-image"
      alt={typeof config.getAlt === 'function' ? config.getAlt(data) : 'image'} />
  {:else if type === 'text'}{data[field]}{/if}
</td>
