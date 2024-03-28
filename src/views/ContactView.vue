<script setup></script>

<template>
    <div class="contact_container">
        <h1 class="title"><span class="brackets">&lt; Contact us &gt;</span></h1>
        <div class="contact_content">
            <div class="contact_infor">
                <p><span class=" "><img src="../assets/images/gmail.png" alt="gmail icon" width="25px" height="25px"></span> mwangilawrence661@gmail.com</p>
                <p><span class="icon"><img src="../assets/images/phone.png" alt="gmail icon" width="25px" height="25px"></span>+254 799 509 242</p>
            </div>
            <div class="contact_form">
                <form action="#" method="post">
                    <div class="input_group">
                        <div class="name">
                            <input type="text" name="first_name" id="first_name" v-model="first_name" placeholder="Enter first name" required>
                            <input type="text" name="last_name" id="last_name" v-model="last_name" placeholder="Enter last name" required>
                        </div>
                        <div class="input_group">
                            <input type="email" name="email" id="email"  v-model="email" placeholder="Enter you email" required>
                        </div>
                        <div class="input_group">
                            <textarea name="message" id="message" cols="7" rows="5" v-model="message" placeholder="Type you message here" required></textarea>
                        </div>
                    </div>
                    <button type="submit">Submit</button>
                </form>
            </div>
        </div>
    </div>
</template>