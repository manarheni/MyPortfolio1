<template>
    <div id="intro" class="intro">
        <div>
            <img src="./../../assets/Profile.jpg" alt="Profile Photo">
        </div>
        <div>
            <h1 v-text="data.name" :class="data.lang === 'ar' ? 'rtl' : '' " />
            <h2 v-text="data.job" :class="data.lang === 'ar' ? 'rtl' : '' " />
            <p v-text="data.intro" :class="data.lang === 'ar' ? 'rtl' : '' " />
            <a :href="'/pdfs/' + data.cv" target="_BLANK" :class="data.lang === 'ar' ? 'reverse' : '' " >
                <VueFeather type="download" stroke="darkorange" size="25" />
                <span v-text="data.download_link" />
            </a>
        </div>
    </div>
</template>

<script>
import VueFeather from 'vue-feather';

    export default {
        name: 'Intro',
        components: {
            VueFeather,
        },
        props: ['data']
    }
</script>


<style scoped>
    .rtl {
        direction: rtl;
    }

    .reverse {
        flex-direction: row-reverse;
    }

    .intro {
        padding: 5% 5%;
        display: flex;
        align-items: center;
    }

    .intro>div {
        width: 50%;
        padding: 40px;
    }

    h1 {
        font-size: 3rem;
        margin-bottom: 5px;
        color: #ff8c01 ;
    }

    h2 {
        font-size: 2rem;
        font-weight: 400;
        margin-top: 10px;
        color: #1f203a;
    }

    p {
        color: #333;
        font-size: 1.1rem;
        line-height: 1.6;
        margin-bottom: 40px;
    }

    img {
        display: block;
        width: 60%;
        height: auto;
        margin: 0 auto;
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        border-radius: 5%;
        transition: all 0.4s ease-in-out;
    }
    img.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

    img:hover {
        filter: none
    }

    a {
        width: fit-content;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #ff8c01;
        border: 1px solid #ff8c01;
        border-radius: 20px;
        text-decoration: none;
        padding: 5px 20px;
        margin: 0 auto;
        transition: all 0.3s ease-in-out;
    }

    a:hover {
        background-color: #1f203a;
        border-color: #ff8c01;
    }

    a>span {
        margin-left: 10px;
        margin-right: 0;
    }

    .reverse>span {
        margin-right: 10px;
        margin-left: 0;
    }

    @media(max-width: 767px) {
        .intro {
            flex-direction: column;
        }

        .intro>div {
            width: 100%;
            padding: 10px;
        }

        .intro>div:first-of-type {
            order: 2;
        }

        h1 {
            text-align: center;
        }

        h2 {
            text-align: center;
        }

        p {
            font-size: 1.1rem;
            line-height: 1.6;
            text-align: center;
            height: auto;
        }
    }

</style>
