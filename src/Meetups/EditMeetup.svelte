<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";

  const dispatch = createEventDispatcher();

  let title = "";
  let subTitle = "";
  let address = "";
  let description = "";
  let email = "";
  let imageUrl = "";

  function submitForm() {
    dispatch("save", {
      title: title,
      subtitle: subTitle,
      address: address,
      description: description,
      email: email,
      imageUrl: imageUrl
    });
  }
</script>

<style>
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<form on:submit|preventDefault={submitForm}>
  <TextInput
    id="title"
    label="Title"
    value={title}
    type="text"
    on:input={event => (title = event.target.value)} />
  <TextInput
    id="sub-title"
    label="Sub Title"
    value={subTitle}
    type="text"
    on:input={event => (subTitle = event.target.value)} />
  <TextInput
    id="address"
    label="Address"
    value={address}
    type="text"
    on:input={event => (address = event.target.value)} />
  <TextInput
    id="image-url"
    label="Image URL"
    value={imageUrl}
    type="text"
    on:input={event => (imageUrl = event.target.value)} />
  <TextInput
    id="email"
    label="Email"
    value={email}
    type="email"
    on:input={event => (email = event.target.value)} />
  <TextInput
    controlType="textarea"
    id="description"
    label="Description"
    value={description}
    on:input={event => (description = event.target.value)} />
  <Button type="submit" caption="Submit" />
</form>
