<template>
    <v-app-bar height="90">
        <router-link to="/">
            <img class="navlogo" src="@/assets/logo1@2x.png" alt="logo" width="80" height="80" />
        </router-link>
        <v-spacer></v-spacer>
        <router-link to="/"><v-btn class="button">Home</v-btn></router-link>
        <router-link to="/pricing"><v-btn class="button">pricing</v-btn></router-link>
        <router-link to="/login" v-if="!isLoggedIn"><v-btn class="button">Log In</v-btn></router-link>
        <router-link v-else><v-btn class="button" @click="logout">Log Out</v-btn></router-link>
    </v-app-bar>
</template>

<style>
v-app-bar {
    position: sticky;
    top: 0%;
}
.button {
    font-family: "Montserrat", sans-serif;
    font-weight: bold;
}
.button:hover,
.button:focus {
    border: 2px solid #566498;
    box-shadow: 0 0.5em 0.5em -0.4em #566498;
    transform: translateY(-0.25em);
    color: #fff;
}

.navlogo {
    margin-left: 5%;
}
</style>

<script>
import { useUserStore } from "@/stores/user";
export default {
    methods: {
        logout() {
            const store = useUserStore();
            store.logout();
            this.$router.push("/");
        },
    },
    setup() {
        const userStore = useUserStore();
        const isLoggedIn = computed(() => userStore.isLoggedIn); // Assuming `isLoggedIn` is a state in your store

        return {
            isLoggedIn,
        };
    },
};
</script>
