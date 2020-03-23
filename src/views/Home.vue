<template lang="pug">
    .main
        h2 Home page
        p
            | here are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which don't look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden in the middle of text. 
        
        hr
        router-link(class='link' to="/todos") Go to app
</template>

<style lang="scss">
    .link {
        color: #41b883;
        text-decoration: underline;
        transition: all .3s;

        &:hover {
            text-decoration: underline;
            color: #35495e;
        }
    }
</style>