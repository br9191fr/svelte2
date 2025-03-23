<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";


    let title = '';
    let subtitle = '';
    let description =' ';
    let imageUrl = '';
    let address = '';
    let email = '';
    let meetups = [
        {
            id: "m1",
            title: "my meeetup",
            subtitle: "information",
            description: "Wonderful meetup",
            imageUrl: "data:image/png;base64,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",
            address: "27th Christmas road, 95645 London",
            contactEmail: "here@example.com"

        },
        {
            id: "m2",
            title: "my second meeetup",
            subtitle: "information",
            description: "Amazing meetup",
            imageUrl: "data:image/png;base64,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",
            address: "192th Jesus Christ road, 22768 New York",
            contactEmail: "there@anywhere.com"
        },
    ];

    function addMeetup() {
        const newMeetup =  {
          id: Math.random().toString(),
            title: title,
            subtitle: title,
            description: description,
            imageUrl: imageUrl,
            address: address,
            contactEmail: email
        };
        meetups = [newMeetup, ...meetups];
    }
</script>

<style>
    main {
        margin-top: 5rem ;
    }
    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>
<Header />

<main>
    <form on:submit|preventDefault="{addMeetup}">
        <TextInput id="title" label="Title" value="{title}" type="text"
        on:input={event => (title = event.target.value)}/>
        <TextInput id="subtitle" label="Subtitle" value="{subtitle}" type="text"
                   on:input={event => (subtitle = event.target.value)}/>
        <TextInput id="address" label="Address" value="{address}" type="text"
                   on:input={event => (address = event.target.value)}/>
        <TextInput id="imageUrl" label="ImageUrl" value="{imageUrl}" type="text"
                   on:input={event => (imageUrl = event.target.value)}/>
        <TextInput id="email" label="Email" value="{email}" type="email"
                   on:input={event => (email = event.target.value)}/>
        <TextInput id="description" label="Description" value="{description}" controlType="textarea"
                   on:input={event => (description = event.target.value)}/>
        <div class="form-control">
        </div>
        <Button type="submit" caption="Save " />
    </form>
    <MeetupGrid meetups={meetups}/>
</main>


