<script>
    export let member;
</script>

<div class="container">
    <article style="background-color:{member.fav_color};">
        <img src={member.avatar} alt={member.name} width="200" height="200" />
        <h1>{member.name}</h1>
        <p>{member.bio}</p>
    </article>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@400;700&display=swap");

    * {
        color: white;
        font-family: "Roboto Slab", serif;
    }

    h1 {
        font-size: clamp(1.3em, 1.5em, 2em);
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.6);
    }

    p {
        font-size: clamp(1.1em, 1.3em, 2em);
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.6);
    }

    .container {
        display: grid;
        place-items: center;
    }

    article {
        margin-top: 2em;
        aspect-ratio: 17/9;
        height: 20vw;
        display: grid;
        place-items: center;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        position: relative;
        overflow: hidden;
        transition:
            transform 0.5s ease-in-out,
            box-shadow 0.2s ease;
        transform-style: preserve-3d;
    }

    @media (width < 1350px) {
        article {
            height: 30vw;
        }
    }

    @media (width < 1050px) {
        article {
            height: 35vw;
        }
    }

    @media (width < 750px) {
        article {
            height: 45vw;
        }
    }

    @media (width < 550px) {
        article {
            height: 50vw;
        }
    }

    article:after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-repeat: no-repeat;
        mix-blend-mode: screen;
        opacity: 0;
        transition: opacity 0.5s ease;
        background-image: linear-gradient(
            45deg,
            rgba(255, 255, 255, 0.2),
            rgba(255, 255, 255, 0.8),
            rgba(255, 255, 255, 0.2)
        );
        background-size: 300% 300%;
        z-index: 0;
    }

    img {
        grid-row: 1/3;
        grid-column: 1/2;
        height: 100%;
        width: auto;
        position: relative;
        z-index: 1;
    }

    @media (width < 550px) {
        img {
            height: 50vw;
        }
    }

    h1 {
        grid-row: 1/2;
        grid-column: 2/3;
        align-self: end;
    }

    p {
        grid-row: 2/3;
        grid-column: 2/3;
    }

    /* Hover effects */
    article:hover:after {
        opacity: 1;
        animation: silverShine 2s infinite linear;
    }

    article:not(:hover):after {
        animation: none;
    }

    article:hover h1,
    article:hover p {
        filter: brightness(1.1);
    }

    article:hover {
        box-shadow: 0 0 20px 5px rgba(255, 255, 255, 0.5);
        transform: scale(1.05) perspective(1000px) rotateX(5deg) rotateY(-5deg);
    }

    @keyframes silverShine {
        0% {
            background-position: -100% 50%;
        }
        100% {
            background-position: 200% 50%;
        }
    }
</style>
