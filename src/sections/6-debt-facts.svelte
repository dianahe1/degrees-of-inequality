<script>
    import { fade } from "svelte/transition";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    let factsVisible = $state(false);

    const observedOptions = {
        threshold: [0.85, 0.95],
    };

    const showCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                factsVisible = true;
            }
        });
    };

    const fadeElements = document.querySelectorAll('.newfact');
    fadeElements.forEach(el => observer.observe(el));
</script>

<div class="main">
    <h1 class="intro-header">
        <ObservedArticleText callback={showCallback} {observedOptions}>
            Statistics from a 2020 NCES study on federal student loan debt, 4 years after graduation:
        </ObservedArticleText>
    </h1>
    {#if factsVisible}
    <div class="newfact-container">
        <p class="newfact" transition:fade={{ delay: 1500, duration: 2000 }}>
            The average borrowed by Black students was <span class="highlight-text">$58K</span>, higher than Asian ($49K) and White ($43K) students.
        </p>
        <p>→</p>
        <p class="newfact" transition:fade={{ delay: 1500, duration: 5000 }}>
            Four years later, Black graduates owed an average <span class="highlight-text">105%</span> of the amount borrowed.
        </p>
        <p>→</p>
        <p class="newfact" transition:fade={{ delay: 1500, duration: 8000 }}>
            They were the <span class="highlight-text">only</span> racial/ethnic group whose average debt was <span class="highlight-text">higher</span> than borrowed.
        </p>
    </div>
    {/if}
    <h1 class="outro-header">
        For many Black graduates, student debt delays homeownership and savings, which reduces wealth for <span class="highlight-text">generations</span>.
    </h1>
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }
    .main {
        background-color: #543719;
        text-align: center;
        color: #F9F3F0;
        padding-bottom: 7%;
    }
    .intro-header {
        margin: -20vh 0 -12vh;
        font-size: 1.5em;
        line-height: 2;
    }
    .newfact-container {
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 5%;
    }
    .newfact {
        width: 20%;
        margin: 0 3%;
        font-size: 20px;
        border: 5px solid #775a3b;
        border-radius: 15px;
        background: #684B2C;
        padding: 10px;
    }
    .highlight-text {
        color: #f5d0bb;
    }
    .outro-header {
        font-family: Recoleta;
        font-size: 2em;
        margin: 4em 6em 1em;
    }
</style>