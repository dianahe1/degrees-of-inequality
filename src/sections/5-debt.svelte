<script>
    import * as Highcharts from "highcharts";
    import { Chart } from "@highcharts/svelte";
    import { fade } from "svelte/transition";

    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    import IntroBorder from "/intro-border.png";

    let subTitleVisible = false;

    const observedOptions = {
        threshold: 0,
    };

    const visibleCallback = (entries, observer) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                subTitleVisible = true;
            }
        });
    };

    let options = {
        chart: {
            type: "column",
            backgroundColor: "#F9F3F0",
            borderRadius: 25,
            spacingTop: 20,
            height: 250,
            style: {
                fontFamily: "century-gothic",
                fontSize: 16,
            },
        },
        title: {
            text: "Percentage of Households with<br>Education Debt",
        },
        xAxis: {
            categories: ["Black Households", "White Households"],
            labels: {
                enabled: false,
            },
            title: {
                text: null,
            },
        },
        yAxis: {
            min: 0,
            max: 100,
            tickInterval: 20,
            title: {
                text: "Percentage (%)",
                align: "middle",
                style: {
                    fontSize: 15,
                },
            },
            labels: {
                overflow: "justify",
            },
        },
        plotOptions: {
            column: {
                dataLabels: {
                    enabled: true,
                    format: "{y}%",
                    style: {
                        fontSize: 16,
                    },
                },
                groupPadding: 0.1,
                pointPadding: 0.2,
            },
        },
        series: [
            {
                name: "Black households",
                data: [35.9],
                color: "#CB904D",
            },
            {
                name: "White households",
                data: [19.8],
                color: "#93BAF1",
            },
        ],
        legend: {
            layout: "horizontal",
            align: "center",
            itemStyle: {
                fontSize: "14px",
            },
        },
        credits: {
            enabled: false,
        },
        exporting: {
            enabled: false
        },
    };
</script>

<div class="main">
    <img src={IntroBorder} alt="Introduction Border" style="width:100vw;" />
    <Scroller layout="bottom">
        {#snippet sticky()}
            <div class="intro">
                <h1 class="intro-header">
                    What are the underlying factors that contribute to this disparity?
                </h1>
                {#if subTitleVisible}
                    <h1 class="fade-text" in:fade={{ duration: 5000 }}>
                        One reason is <span class="highlight-text">student debt</span>.
                    </h1>
                {/if}
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText callback={visibleCallback} {observedOptions}>
                <div class="chart-container">
                    <div class="chart">
                        <Chart {options} highcharts={Highcharts} />
                    </div>
                    <p>
                        Black households are nearly <span class="highlight-text">twice as likely</span> to carry student debt compared to White households.
                    </p>
                </div>
            </ObservedArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }
    .main {
        background-color: #543719;
        text-align: left;
        color: #F9F3F0;
    }
    .intro {
        position: sticky;
        top: 0;
        margin: 0 0 70vh;
        font-family: Recoleta;
    }
    .intro-header {
        font-size: 2em;
        line-height: 2;
        margin: 5% 0 5vh;
    }
    .fade-text {
        font-size: 2em;
        transition: opacity 1s ease;
    }
    .highlight-text {
        color: #f5d0bb;
    }
    .chart-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }
    .chart {
        width: 26%;
        margin-right: 5%;
    }
    p {
        width: 28%;
        font-size: 22px;
        line-height: 2;
        padding-bottom: 10px;
    }
</style>
