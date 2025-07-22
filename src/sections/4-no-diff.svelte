<script>
    import { fade, fly } from "svelte/transition";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";
    import * as Highcharts from "highcharts";
    import { Chart } from "@highcharts/svelte";

    let graphIsVisible = $state(false);

    const observedOptions = {
        threshold: [0.85, 0.95],
    };

    const showGraphCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                graphIsVisible = true;
            }
        });
    };

    let options = {
        chart: {
            type: "column",
            backgroundColor: "#F9F3F0",
            borderRadius: 25,
            spacingTop: 20,
            height: 280,
            style: {
                fontFamily: "century-gothic",
                fontSize: 16,
            },
        },
        title: {
            text: "Median Net Worth Comparison",
        },
        xAxis: {
            categories: ["4-Year College Graduates"],
            labels: {
                enabled: false,
            },
            title: {
                text: null,
            },
        },
        yAxis: {
            min: 0,
            tickInterval: 50000,
            title: {
                text: "Net Worth (USD)",
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
                    format: "${y:,.0f}",
                    style: {
                        fontSize: 16,
                    },
                },
                groupPadding: 0,
                pointPadding: 0.3,
            },
        },
        series: [
            {
                name: "White households<br>(High school diploma)",
                data: [153050],
                color: "#93BAF1",
            },
            {
                name: "Black households<br>(Bachelor's degree)",
                data: [128550],
                color: "#CB904D",
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
    <div class="staticText">
        <ObservedArticleText callback={showGraphCallback} {observedOptions}>
            In fact, Black households with a <span class="highlight-text">Bachelor's degree</span> have less median wealth than White households with a <span class="highlight-text">high school diploma</span>.
        </ObservedArticleText>
    </div>
    <div class="chart">
        {#if graphIsVisible}
            <div transition:fade={{ delay: 1500, duration: 2000 }}>
                <Chart {options} highcharts={Highcharts} />
            </div>
        {/if}
        <br />
    </div>
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }
    .main {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #496EA2;
        text-align: left;
        color: #F9F3F0;
    }
    .staticText {
        background-color: #496EA2;
        font-family: Recoleta;
        font-size: 2em;
        margin: 0 10% 3% 0;
        width: 25%;
    }
    .highlight-text {
        color: #d8e8fe;
    }
    .chart {
        width: 30%;
    }
</style>