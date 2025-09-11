<script>
    let { data } = $props();
    const member = data.member;
    import ProfileCard from "$lib/components/ProfileCard.svelte";
</script>

<!-- <p>Hallo Hallo</p> -->
<ProfileCard />

<main>
    <article style="background-color:{member.fav_color};">
        <img src={member.avatar} alt="" width="200" height="200" />
        <h1>{member.name}</h1>
        <p>{member.bio}</p>
    </article>
</main>

<style>
    * {
        color: white;
    }

    main {
        display: grid;
        place-items: center;
        @media (width < 32em) {
            article {
                max-width: 24em;
            }
            img {
                height: 150px;
                width: 150px;
            }
        }
    }
    article {
        max-width: 32em;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        img {
            grid-row: 1/3;
            grid-column: 1/2;
        }
        p {
            grid-row: 2/2;
        }
    }
</style>
