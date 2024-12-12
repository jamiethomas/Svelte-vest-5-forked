<script>
  // Created by @codechips https://github.com/codechips | https://twitter.com/codechips
  import classnames from "vest/classnames";
  import suite from "./suite";

  import Input from "./components/Input.svelte";
  import ButtonSubmit from "./components/ButtonSubmit.svelte";
  import Checkbox from "./components/Checkbox.svelte";

  let formState = {};
  let usernamePending = false;
  let result = suite.get();

  const handleChange = name => {
    result = suite(formState, name);

    if (name === "username") {
      usernamePending = true;
    }

    result.done(res => {
      usernamePending = false;
      result = res;
    });
  };

  $: cn = classnames(result, {
    warning: "warning",
    invalid: "error",
    valid: "success"
  });
  $: disabled = !result.isValid();
</script>

<form on:submit|preventDefault>
  <Input
    name="username"
    label="Username"
    bind:value={formState.username}
    onInput={handleChange}
    pending={usernamePending}
    validityClass={cn('username')}
    messages={result.getErrors('username')}
  />
  <Input
    name="password"
    label="Password"
    bind:value={formState.password}
    onInput={handleChange}
    validityClass={cn('password')}
    messages={[...result.getErrors('password'), ...result.getWarnings('password')]}
  />
  <Input
    name="confirm"
    label="Confirm"
    bind:value={formState.confirm}
    onInput={handleChange}
    messages={result.getErrors('confirm')}
    validityClass={cn('confirm')}
  />
  <Checkbox
    name="tos"
    label="I have read and agreed to the terms of service."
    bind:checked={formState.tos}
    onChange={() => handleChange("tos")}
    validityClass={cn('tos')}
  />
  <ButtonSubmit {disabled}>Submit</ButtonSubmit>
</form>


<style>
  form {
    --color-error: rgb(245, 137, 137);
    --color-warning: #bea073;
    --color-success: rgb(121, 196, 114);
    --color-content-active: #5081a6;
    --color-content-semi: #89b8dd;
    --color-content-inactive: #cfe3f0;
    color: #999;
    width: 500px;
    padding: 1.5em;
    margin: 0 auto;
    border-radius: 10px;
    background: #fff;
    box-shadow: 0 10px 25px rgba(27, 37, 46, 0.5);
  }
</style>