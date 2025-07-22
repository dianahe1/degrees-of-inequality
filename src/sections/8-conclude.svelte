<script>
    import { fade } from "svelte/transition";
    import WealthBorder from "/wealth-border.png";
</script>

<div class="main">
    <img src={WealthBorder} alt="Title Border" class="wealth-border" />
    <h1 class="intro-header">
        Structural solutions are needed.
    </h1>
    <div class="solution-container">
        <div class="solution">
            Provide pathways to reduce student debt that address wealth and income.
        </div>
        <div class="solution">
            Boost college affordability through increased support for low-income students.
        </div>
        <div class="solution">
            Strengthen HBCUs and other community-based programs or scholarships.
        </div>
    </div>
    <div class="outro-text">
        <h1>
            Education might be seen as a ladder to success, but it is not enough.<br><br>
            To close the racial wealth gap, we must rethink how we reward effort, and who gets to build wealth.
        </h1>
    </div>
    <div class="footer">All data except the <a href="https://nces.ed.gov/pubs2022/2022241.pdf">NCES 2020 study</a> is from the <a href="https://blackwealthdata.org/">Black Wealth Data Center</a> © 2025.</div>
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
        background-color: #F9F3F0;
        text-align: center;
        color: #1b1b1b;
    }

    .intro-header {
        font-family: Recoleta;
        font-size: 2em;
        margin: 7% 15% 2%;
    }
    .solution-container {
        display: flex;
        justify-content: center;
    }
    .solution {
        background: #e1edff;
        width: 20%;
        margin: 3%;
        padding: 5px;
        font-size: 1.2em;
        border-radius: 10px;
        border: 5px solid #bbd4f6;
    }
    .outro-text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: Recoleta;
        font-size: 1em;
        margin: 5% 12% 5%;
    }
    .footer {
        background: #543719;
        color: #F9F3F0;
        font-size: 1.25em;
        padding: 5%;
    }
    a {
        color: #bbd4f6;
        text-decoration: none;
    }
    a:hover {
        text-decoration: underline;
    }
</style>
