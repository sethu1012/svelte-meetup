<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";

  let title = "";
  let subTitle = "";
  let address = "";
  let description = "";
  let email = "";
  let imageUrl = "";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com"
    },
    {
      id: "m2",
      title: "Coding Bootcamp 2",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com"
    },
    {
      id: "m3",
      title: "Coding Bootcamp 3",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com"
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subTitle,
      description: description,
      imageUrl: imageUrl,
      address: address,
      contactEmail: email
    };
    meetups = [...meetups, newMeetup];
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="sub-title"
      label="Sub Title"
      value={subTitle}
      on:input={event => (subTitle = event.target.value)} />
    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="image-url"
      label="Image URL"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="email"
      label="Email"
      value={email}
      on:input={event => (email = event.target.value)} />
    <TextInput
      controlType="textarea"
      id="description"
      label="Description"
      value={description}
      on:input={event => (description = event.target.value)} />
    <button type="submit">Save</button>
  </form>
  <MeetupGrid {meetups} />
</main>
