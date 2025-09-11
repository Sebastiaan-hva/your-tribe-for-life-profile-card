<script>
    let { data } = $props();
    const member = data.member;
    import ProfileCard from "$lib/components/ProfileCard.svelte";
</script>

<p>Hallo Hallo</p>

<main>
    <h1>{member.name}</h1>
    <ProfileCard />
</main>
