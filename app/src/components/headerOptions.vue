<template>
    <div class="header-options">
        <div class="notifications" v-on:click="showNotifications()">
            <div class="notification-icon">
                <i class="fas fa-bell icon-clicable"></i>
                <div class="new-notifications"></div>
            </div>
            <notificationsComponent id="notifications-component" />
        </div>
        <router-link :to="'/meeting/' + true" class="video-meeting" @click.native="initiateConferenceTimer()">
            <i class="fas fa-video"></i>
        </router-link>
    </div>
</template>

<script>
import notificationsComponent from '../components/notificationsComponent.vue'
import $ from 'jquery'
import {globalMethods} from '../js/globalMethods.js'

export default {
    name: "headerOptions",
    mixins: [globalMethods],
    methods: {
        showNotifications() {
            $("#notifications-component").toggleClass("d-block");
        }
    },
    components: {
        notificationsComponent
    }
}
</script>

<style scoped>
    .header-options {
        width: 100%;
        background: var(--white);
        border-radius: 10px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        padding: .2rem;
        box-shadow: 0 0 10px rgba(0,0,0,0.2);
        position: relative;
    }

        .header-options i {
            font-size: 1.5rem;
        }

    .notifications, .video-meeting {
        padding: .3rem 0;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 50%;
        border-radius: 5px;
        cursor: pointer;
        text-decoration: none;
    }

    .notifications:hover, .video-meeting:hover {
        background: var(--gray-high);
    }

    .new-notifications {
        width: 9px;
        height: 9px;
        border-radius: 50%;
        background: var(--red);
        border: 2px solid var(--white);
        position: absolute;
        right: 0;
        top: 50%;
    }

    .notification-icon {
        position: relative;
    }

    @media (max-width: 420px) {
        .notifications i, .video-meeting i {
            font-size: 1.3rem;
        }
    }
</style>