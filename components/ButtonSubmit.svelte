<script>
  export let disabled;
</script>

<button  type="submit" class="btn-submit" disabled={disabled}>
  <slot />
</button>

<style>
  button.btn-submit {
    border: 0;
    background: rgb(47, 73, 118);
    background: linear-gradient(
      180deg,
      rgba(47, 73, 118, 1) -50%,
      rgba(26, 30, 65, 1) 150%
    );
    padding: 1em;
    margin-top: 1em;
    width: 100%;
    color: white;
    font-size: 1em;
    border-radius: 10px;
    outline: none;
    transition: 0.25s;
    font-weight: 500;
  }

  button.btn-submit:hover:not(:disabled) {
    box-shadow: 0 0 10px rgba(47, 73, 118, 0.8);
    cursor: pointer;
    background: linear-gradient(
      180deg,
      rgba(47, 73, 118, 1) 0%,
      rgba(26, 30, 65, 1) 200%
    );
  }

  button.btn-submit:active {
    background: linear-gradient(
      0deg,
      rgba(47, 73, 118, 1) 0%,
      rgba(26, 30, 65, 1) 200%
    );
    box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.5);
  }

  button.btn-submit:disabled {
    background: rgb(209, 209, 209);
  }
</style>
