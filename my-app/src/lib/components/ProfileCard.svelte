<script>
    import { onMount } from "svelte";

    export let member;

    let flyAway = false;
    let flyBack = false;
    let showSpace = false;

    function handleClick() {
        flyAway = true;
        showSpace = true;

        if (typeof document !== "undefined") {
            document.body.classList.add("space"); // keep background permanently
        }

        // After fly-away, start fly-back
        setTimeout(() => {
            flyAway = false;
            flyBack = true;

            // After fly-back completes, reset flyBack
            setTimeout(() => {
                flyBack = false;
            }, 3000);
        }, 3000);
    }
</script>

<div class="container">
    <article
        class:fly-away={flyAway}
        class:fly-back={flyBack}
        style="background-color:{member.fav_color};"
        on:click={handleClick}
    >
        <img src={member.avatar} alt={member.name} />
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

    .container {
        display: grid;
        place-items: center;
        position: relative;
        overflow: hidden;
        padding: 2em;
    }

    article {
        aspect-ratio: 17/9;
        margin-top: 4em;
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
        cursor: pointer;
        z-index: 1;
    }

    /* Fly-away animation */
    .fly-away {
        animation: flyAway 3s forwards ease-in;
    }

    /* Fly-back animation */
    .fly-back {
        animation: flyBack 3s forwards ease-out;
    }

    @keyframes flyAway {
        0% {
            transform: scale(1) translate(0, 0) rotate(0);
            opacity: 1;
        }
        30% {
            transform: scale(1.2) translate(50px, -100px) rotate(10deg);
        }
        100% {
            transform: scale(0.5) translate(600px, -1200px) rotate(45deg);
            opacity: 0;
        }
    }

    @keyframes flyBack {
        0% {
            transform: scale(0.5) translate(600px, -1200px) rotate(45deg);
            opacity: 0;
        }
        30% {
            transform: scale(1.2) translate(50px, -100px) rotate(10deg);
            opacity: 1;
        }
        100% {
            transform: scale(1) translate(0, 0) rotate(0);
            opacity: 1;
        }
    }

    h1 {
        font-size: clamp(1.3em, 1.5em, 2em);
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.6);
        grid-row: 1/2;
        grid-column: 2/3;
        align-self: end;
        z-index: 2;
    }

    p {
        font-size: clamp(1.1em, 1.3em, 2em);
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.6);
        grid-row: 2/3;
        grid-column: 2/3;
        z-index: 2;
    }

    img {
        grid-row: 1/3;
        grid-column: 1/2;
        height: 100%;
        width: auto;
        position: relative;
        z-index: 2;
    }

    /* Hover shine effect */
    article:after {
        content: "";
        position: absolute;
        inset: 0;
        background: linear-gradient(
            45deg,
            rgba(255, 255, 255, 0.2),
            rgba(255, 255, 255, 0.8),
            rgba(255, 255, 255, 0.2)
        );
        background-size: 300% 300%;
        opacity: 0;
        transition: opacity 0.5s ease;
        mix-blend-mode: screen;
        z-index: 3;
    }

    article:hover:after {
        opacity: 1;
        animation: silverShine 2s linear 2;
        /* animation: silverShine 2s linear infinite; either version is ok */
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

    /* Responsive sizes */
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
        img {
            height: 50vw;
        }
    }
</style>
