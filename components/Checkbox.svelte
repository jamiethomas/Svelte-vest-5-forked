<script>
  export let name = "";
  export let checked = false;
  export let label = "";
  export let onChange = () => {};
  export let validityClass;
</script>

<label for={name} class={`form-checkbox ${validityClass}`}>
  <input type="checkbox" {name} bind:checked on:change={onChange}/>
  <small>{ label }</small>
</label>

<style>
  .form-checkbox {
    font-size: 0.8em;
    padding: 1em 0;
  }

  .form-checkbox {
    display: flex;
    align-items: center;
  }

  .form-checkbox input {
    margin-right: 0.5em;
  }

  .form-checkbox.error {
    color: var(--color-error);
  }

  .form-checkbox.success {
    color: var(--color-success);
  }
</style>
