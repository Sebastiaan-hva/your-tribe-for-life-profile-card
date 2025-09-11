<script>
    let { data } = $props();
    const member = data.member;
    import ProfileCard from "$lib/components/ProfileCard.svelte";
</script>

<!-- <p>Hallo Hallo</p> -->
<ProfileCard />

<main style="background-color:{member.fav_color};">
    <article>
        <img src={member.avatar} alt="" width="200" height="200" />
        <h1>{member.name}</h1>
        <p></p>
    </article>
</main>

<style>
    * {
        color: white;
    }
    main {
    }
    article {
        display: grid;
        grid-template-columns: 1fr 1fr;
    }
</style>
