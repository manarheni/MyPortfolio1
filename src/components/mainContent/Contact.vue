<template>
    <div id="contact" class="contact">
        <div>
            <h5 v-text="data.contact_heading" />
            <form>
                <input type="text" :placeholder="data.name_label" v-model="mail.name" required 
                 :class="data.lang === 'ar' ? 'rtl' : '' " />
                <input type="email" :placeholder="data.email_label" v-model="mail.email" required
                 :class="data.lang === 'ar' ? 'rtl' : '' " />
                <textarea rows="8" :placeholder="data.message_label" v-model="mail.message"
                 :class="data.lang === 'ar' ? 'rtl' : '' " >

                </textarea>
                <p id="feedback">&nbsp;</p>
                <button @click.prevent="sendEmail">
                    {{ data.send_btn }}
                </button>
                
            </form>
        </div>
        <div>
            <a :href="'tel:' + data.phone" :class="data.lang === 'ar' ? 'item reverse' : 'item' ">
                <img src="./../../assets/contacts/phone.png">
                <span v-text="data.phone" />
            </a>
            <a :href="'mailto:' + data.email" :class="data.lang === 'ar' ? 'item reverse' : 'item' ">
                <img src="./../../assets/contacts/gmail.png">
                <span v-text="data.email" />
            </a>
            <a :href="'https://www.linkedin.com/in/manar-heni-52113117a/'" target="_BLANK" :class="data.lang === 'ar' ? 'item reverse' : 'item' ">
                <img src="./../../assets/contacts/linkedin.png">
                <span v-text="data.linkedin" />
            </a>
            <a :href="'https://www.facebook.com/manarheni848/'" target="_BLANK" :class="data.lang === 'ar' ? 'item reverse' : 'item' ">
                <img src="./../../assets/contacts/facebook.png">
                <span v-text="data.facebook" />
            </a>
            <a :href="'https://www.instagram.com/' + data.instagram + '/'" target="_BLANK" :class="data.lang === 'ar' ? 'item reverse' : 'item' ">
                <img src="./../../assets/contacts/instagram.png">
                <span v-text="data.instagram" />
            </a>
        </div>
    </div>
</template>

<script>
import emailjs from 'emailjs-com';

    export default {
        name: 'Contact',
        props: ['data'],
        data() {
            return {
                mail: {}
            }
        },
        methods: {
            sendEmail() {
                var templateParams = {
                        name: this.mail.name,
                        email: this.mail.email + " ",
                        message: this.mail.message + " ",
                        
                }
                const serviceID = 'service_dyozx05';
                const templateID = 'template_pwyxb4s';
                const userID = 'user_aew1XU7c2JP3topXNbU9p';
                var feedback =document.getElementById('feedback');

                try {
                    emailjs.send(serviceID, templateID, templateParams, userID);
                    feedback.textContent = this.data.feedback_message;
                    feedback.style.display = "block";

                } catch(error) {
                    console.log({error})
                    feedback.textContent = this.data.error_message;
                    feedback.style.color = "#F00";
                    feedback.style.display = "block";
                }
            },
        },
    }
</script>


<style scoped>
    .rtl {
        direction: rtl;
    }

    .reverse {
        flex-direction: row-reverse;
    }

    .contact {
        padding: 3% 5%;
        display: flex;
        align-items: center;
    }

    .contact>div {
        width: 50%;
        padding: 40px;
    }

    .item {
        display: flex;
        align-items: center;
        margin-bottom: 20px;
        text-decoration: none;
        font-size: 1.6rem;
        font-weight: bold;
        color: #1f203a;
    }

    h5 {
        font-size: 2rem;
        font-weight: 400;
        color: #1f203a;
        margin-bottom: 40px;
        margin-top: 0;
        text-align: center;
    }

    img {
        margin-right: 20px;
        margin-left: 0;
        width: 60px;
        height: 60px;
        transition: all 0.4s ease-in-out;
    }

    .reverse img {
        margin-left: 20px;
        margin-right: 0;
    }

    form {
        display: block;
        margin: 0 auto;
        width: 80%;
    }

    form:after {
        content: '';
        clear: both;
    }

    input, textarea {
        display: block;
        width: 100%;
        margin-bottom: 15px;
        padding: 10px 20px;
        border-radius: 10px;
        border: 1px solid #1f203a;
        font-size: 1.1rem;
        font-family: Arial, Helvetica, sans-serif;
    }

    button {
        padding: 10px 30px;
        border-radius: 10px;
        border: 1px solid #1f203a;
        background-color: #1f203a;
        color: white;
        float: right;
        font-size: 1rem;
        cursor: pointer;
        transition: all 0.5s ease-in-out;
    }

    button:hover {
        background-color: white;
        color: #1f203a;
    }

    #feedback {
        display: none;
        float: left;
        margin-top: 14px;
        font-size: 14px;
        color: #080;
        font-style: italic;
    }

    @media(max-width: 767px) {
        .contact {
            flex-direction: column;
        }

        .contact>div {
            width: 100%;
            padding: 10px;
        }

        .contact>div:first-of-type {
            order: 2;
        }

        .item {
            font-size: 17px
        }

        img {
            width: 50px;
            height: 50px;
        }

        h5 {
            margin-top: 0;
            margin-bottom: 40px;
        }

        form {
            width: 100%;
            margin: 0;

        }

        input, textarea {
            width: 87%;
        }
    }

</style>
