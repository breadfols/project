<script>
	import Navbar from "./Navbar.svelte";

</script>
<header class="header">
    <Navbar />
</header>

<style lang="scss">
    .header{
        background: url('/images/phon.jpg') no-repeat center;
        background-size: cover;
        height: 600px;
        @media (max-width:theme('screens.desktop')){
            height: 500px;
        }
        @media (max-width:theme('screens.laptop')){
            height:400px;
        }
        @media (max-width:theme('screens.tablet')){
            height: 300px;
        } 

    }
</style>