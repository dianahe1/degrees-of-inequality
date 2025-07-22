<script>
    import TitleImg from "/hat-outline.png";
    import TitleBorder from "/kwk_bdwc_1.png";
</script>

<div class="title-card">
    <img src={TitleImg} alt="Education Slideshow" class="title-img"/>
    <div class="content">
        <h1>Degrees of Inequality</h1>
        <p>How Higher Education Fails to Bridge the Racial Wealth Gap</p>
    </div>
    <img src={TitleBorder} alt="Title Border" class="title-border" />
</div>

<style>
    @font-face {
        font-family: Recoleta;
        src: url("/Recoleta-Regular.otf");
    }

    .title-card {
        background: linear-gradient(#dee5fb, #f9f3f0);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
    }

    .title-img {
        width: 10vw;
        margin-top: 77px;
        opacity: 0.5;
    }

    .content {
        margin: 70px 0;
        max-width: 700px;
        background-color: #496EA2;
        padding: 3rem 3.5rem 2rem;
        border: 15px solid #bbd4f6;
        border-radius: 25px;
    }

    h1 {
        font-size: 3.2rem;
        margin: 0;
        color: #e8f1ff;
        text-shadow: 1px 1px 5px #f1f3f6;
        font-family: Recoleta;
    }

    p {
        font-size: 1.3rem;
        color: #e8f1ff;
        margin-top: 2rem;
    }

    .title-border {
        width: 100vw;
        margin-top: 50px;
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.2rem;
        }

        p {
            font-size: 1.1rem;
        }
    }
</style>
