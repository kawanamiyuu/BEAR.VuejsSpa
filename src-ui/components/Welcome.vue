<template>
<div id="welcome">
    <img src="../assets/logo.png">
    <h2>Essential Links</h2>
    <ul>
        <li v-for="link in essential_links">
            <a :href="link.url" target="_blank">{{ link.label }}</a>
        </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
        <li v-for="link in ecosystem_links">
            <a :href="link.url" target="_blank">{{ link.label }}</a>
        </li>
    </ul>
</div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'welcome',
    created() {
        this.fetchLinks();
    },
    data() {
        return {
            essential_links: [],
            ecosystem_links: []
        };
    },
    methods: {
        fetchLinks() {
            axios.get('/links')
                .then(res => {
                    this.essential_links = res.data.essential_links;
                    this.ecosystem_links = res.data.ecosystem_links;
                });
        }
    }
};
</script>

<style scoped>
#welcome {
    margin-top: 30px;
}

h1, h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
