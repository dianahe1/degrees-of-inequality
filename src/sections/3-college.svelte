<script>
    import * as Highcharts from "highcharts";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import IntroBorder from "/intro-border.png";

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
            text: "Median Net Worth of Households",
        },
        subtitle: {
            text: "4-Year College Graduates",
            style: {
                fontSize: "16px",
                color: "#666",
            }
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
            tickInterval: 150000,
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
                groupPadding: 0.2,
            },
        },
        series: [
            {
                name: "White households",
                data: [578700],
                color: "#93BAF1",
            },
            {
                name: "Black households",
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
    <img src={IntroBorder} alt="Introduction Border" style="width:100vw;" />
    <Scroller layout="bottom">
        {#snippet sticky()}
            <h1 class="intro-text">
                From an early age, we’re taught that hard work and education lead to success.
                Do your part, and you’ll climb the ladder.<br>
            </h1>
        {/snippet}

        {#snippet scrolly()}
            <h1 class="intro-highlight">However, the wealth gap remains.</h1>
            <div class="chart-container">
                <div class="chart">
                    <Chart {options} highcharts={Highcharts} />
                </div>
                <p>
                    White households have <span class="highlight-text">$450K</span> more in median wealth than Black households with the same <span class="highlight-text">Bachelor's degree</span>.
                </p>
            </div>
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
        padding-bottom: 30px;
    }
    .intro-text {
        margin: 3.5% 10em 60vh 5em;
        position: sticky;
        font-family: Recoleta;
        top: 0;
        font-size: 2em;
        line-height: 2;
        margin-bottom: 77vh;
    }
    .intro-highlight {
        font-family: Recoleta;
        font-size: 2em;
        color: #f5d0bb;
        margin: 0 5em 2.5em;
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
        width: 30%;
        margin: 0 5% 90px 0;
    }
    p {
        width: 28%;
        font-size: 20px;
        line-height: 2;
        padding-bottom: 100px;
    }
</style>
