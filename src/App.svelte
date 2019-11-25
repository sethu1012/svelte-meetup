<script>
  import Header from "./UI/Header.svelte";
  import Button from "./UI/Button.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com",
      isFavourite: false
    },
    {
      id: "m2",
      title: "Coding Bootcamp 2",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com",
      isFavourite: false
    },
    {
      id: "m3",
      title: "Coding Bootcamp 3",
      subtitle: "Coding in Hours",
      description: "Description",
      imageUrl: "image",
      address: "Address",
      contactEmail: "email@email.com",
      isFavourite: false
    }
  ];

  let editMode = null;

  function addMeetup(event) {
    console.log(event);
    const newMeetup = {
      id: Math.random().toString(),
      ...event.detail
    };
    meetups = [newMeetup, ...meetups];
    editMode = null;
  }

  function toggleFavourite(event) {
    const id = event.detail;
    const updatedMeetup = { ...meetups.find(m => m.id === id) };
    updatedMeetup.isFavourite = !updatedMeetup.isFavourite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>

<Header />

<main>
  <div class="meetup-controls">
    <Button caption="Add Meetup" on:click={() => (editMode = 'add')} />
  </div>
  {#if editMode === 'add'}
    <EditMeetup on:save={addMeetup} />
  {/if}
  <MeetupGrid {meetups} on:toggle-favourite={toggleFavourite} />
</main>
