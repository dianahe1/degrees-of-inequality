<script>
    import { onMount } from "svelte";
    import * as Highcharts from "highcharts";
    import { Chart } from "@highcharts/svelte";

    let options = {
        chart: {
            type: "pie",
            backgroundColor: "#bbd4f6",
            borderRadius: 25,
            spacingTop: 20,
            height: 180,
            style: {
                fontFamily: "century-gothic",
                fontSize: 15,
            },
        },
        title: {
            text: "Quasi-Liquid Retirement Account",
        },
        plotOptions: {
            pie: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 0,
                        format: "{point.percentage:.1f}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                            color: "#496ea2",
                        },
                    },
                ],
            },
        },
        series: [
            {
                name: "",
                data: [
                    {
                        name: "",
                        y: 34.7,
                        color: "#496ea2",
                    },
                    {
                        name: "",
                        y: 65.3,
                        color: "#d4d7e0",
                        dataLabels: {
                            enabled: false,
                        },
                    },
                ],
                animation: false,
            },
        ],
        credits: {
            enabled: false,
        },
        exporting: {
            enabled: false,
        },
    };

    let chart2;

    // Function to update data with a fade effect
    function updateChartData(newData) {
        chart2.series[0].setData(newData, true, { duration: 800 });  // Apply fade on update
    }

    onMount(() => {
        // Store the chart reference
        chart2 = Highcharts.chart("chart-container2", options);
    });

    let newData = [
        { name: "", y: 61.7, color: "#496ea2" },
        { name: "", y: 38.3, color: "#d4d7e0" }
    ];

    // Change chart data after a timeout to show effect
    setTimeout(() => {
        updateChartData(newData);
    }, 300);
</script>

<div class="chart" id="chart-container2">
    <Chart {options} highcharts={Highcharts} />
</div>

<style>
    .chart {
        width: 100%;
        max-width: 400px;
        margin: 0 auto;
    }
</style>