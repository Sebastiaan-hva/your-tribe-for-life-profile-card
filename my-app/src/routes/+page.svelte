<script>
    let { data } = $props();
    const member = data.member;
    import ProfileCard from "$lib/components/ProfileCard.svelte";
</script>

<ProfileCard {member} />
