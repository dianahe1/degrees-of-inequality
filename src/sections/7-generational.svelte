<script>
    import { fade } from "svelte/transition";
    import WealthBorder from "/wealth-border.png";
    import PooledChart from "../lib/PooledChart.svelte";
    import PooledChart2 from "../lib/PooledChart2.svelte";
    import QuasiChart from "../lib/QuasiChart.svelte";
    import QuasiChart2 from "../lib/QuasiChart2.svelte";
    import StocksChart from "../lib/StocksChart.svelte";
    import StocksChart2 from "../lib/StocksChart2.svelte";

    let chartIntro = $state("Percentage of Black households holding each asset type:");
    let buttonText = $state("Press the button to see asset data for White households.");
    let showDifferentData = $state(false);

    function toggleDiffData() {
        if (showDifferentData) {
            chartIntro = "Percentage of Black households holding each asset type:";
            showDifferentData = false;
            buttonText = "Press this button to see asset data for White households.";
        } else {
            chartIntro = "Percentage of White households holding each asset type:";
            buttonText = "Press this button to see asset data for Black households.";
            showDifferentData = true;
        }
    }
</script>

<div class="main">
    <img src={WealthBorder} alt="Title Border" class="wealth-border" />
    <h1 class="intro-header">
        This link between education and generational wealth is connected to the racial wealth gap in more than one way.
    </h1>
    <h1 class="intro-chart">{chartIntro}</h1>

    <div class="chart-container">
        <div class="charts">
            <div class="chart">
                {#if !showDifferentData}
                    <PooledChart />
                {/if}
                {#if showDifferentData}
                    <PooledChart2 />
                {/if}
            </div>
            <div class="chart">
                {#if !showDifferentData}
                    <QuasiChart />
                {/if}
                {#if showDifferentData}
                    <QuasiChart2 />
                {/if}
            </div>
            <div class="chart">
                {#if !showDifferentData}
                    <StocksChart />
                {/if}
                {#if showDifferentData}
                    <StocksChart2 />
                {/if}
            </div>
        </div>

        <button onclick={toggleDiffData} class="toggle-button">
            {buttonText}
        </button>
    </div>
    <div class="outro-text">
        <h1>White households are more likely to hold liquid assets of high value like pooled funds,</h1>
        <div style="display:flex;">
            <h1>which result in f</h1>
            <h1>inancial f</h1><h1>lexibility to cover higher education costs.</h1>
        </div>
        <h1 style="margin-top:5%;">This advantage continues the cycle of generational wealth-building.</h1>
    </div>
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }
    .wealth-border {
        width: 100vw;
    }
    .main {
        background-color: #496EA2;
        text-align: center;
        color: #F9F3F0;
        padding-bottom: 30px;
    }

    .intro-header {
        font-family: Recoleta;
        font-size: 2em;
        margin: 8% 15% 0;
    }
    .intro-chart {
        font-size: 1.6em;
        margin: 8% 5% 3%;
    }
    .charts {
        display: flex;
        justify-content: center;
        margin-bottom: 20px;
    }
    .chart {
        width: 22%;
        margin: 0 3%;
    }

    .toggle-button {
        background-color: #cb904d;
        color: white;
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        font-size: 1.3em;
        font-family: century-gothic;
        margin-top: 2%;
    }

    .toggle-button:hover {
        background-color: #93BAF1;
    }
    .outro-text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: Recoleta;
        font-size: 1em;
        margin: 8% 5% 3%;
        line-height: 1em;
    }
</style>
