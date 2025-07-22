<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#FFFFF9",
            borderColor: "#CB904D",
            borderWidth: 5,
            borderRadius: 25,
            spacing: [25, 25, 20, 15],
        },
        title: {
            text: "Median Net Worth of Households",
            style: {
                fontFamily: "century-gothic",
            },
        },
        xAxis: {
            title: {
                text: null,
            },
            tickInterval: 3,
        },
        yAxis: {
            min: 0,
            title: {
                text: "Net Worth (USD)",
                align: "middle",
            },
            labels: {
                overflow: "justify",
                formatter: function () {
                    return `$${this.value}K`;
                },
            },
        },
        plotOptions: {
            series: {
                marker: {
                    enabled: false
                },
                dataLabels: {
                    enabled: true,
                    formatter: function () {
                        if (this.point.index === this.series.data.length - 1) {
                            return `$${this.y}K`;
                        }
                        return null;
                    },
                },
            },
        },
        series: [
            {
                name: "White",
                data: [
                    [2013, 181],
                    [2016, 211],
                    [2019, 219],
                    [2022, 284],
                ],
                color: "#CB904D",
            },
            {
                name: "All",
                data: [
                    [2013, 104],
                    [2016, 120],
                    [2019, 141],
                    [2022, 193],
                ],
                color: "#AAAFB6",
            },
            {
                name: "Other",
                data: [
                    [2013, 52],
                    [2016, 80],
                    [2019, 86],
                    [2022, 132],
                ],
                color: "#BBD4F6",
            },
            {
                name: "Hispanic",
                data: [
                    [2013, 18],
                    [2016, 26],
                    [2019, 42],
                    [2022, 62],
                ],
                color: "#496EA2",
            },
            {
                name: "Black",
                data: [
                    [2013, 17],
                    [2016, 21],
                    [2019, 28],
                    [2022, 44],
                ],
                color: "#523619",
            },
        ],
        credits: {
            enabled: false,
        },
        exporting: {
            enabled: false
        },
    };
</script>

<div class="intro">
    <div class="header">
        <h1>In America, there is a sign</h1>
        <h1>if</h1>
        <h1>icant difference in wealth between racial groups.</h1>
    </div>
    <div class="container">
        <div class="chart">
            <Chart {options} highcharts={Highcharts} />
        </div>
        <p>White households have a much higher median net worth than Black and Hispanic households.</p>
    </div>
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }
    .intro {
        background-color: #f9f3f0;
        text-align: center;
        margin: 0;
        padding: 5% 0 30px;
    }
    .header {
        display: flex;
        justify-content: center;
    }
    .container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }
    h1 {
        font-family: Recoleta;
        margin-bottom: 3.5%;
    }
    .chart {
        width: 32%;
        margin: 30px 75px 80px 20px;
    }
    p {
        width: 20%;
        font-size: 22px;
        padding-bottom: 80px;
    }
</style>