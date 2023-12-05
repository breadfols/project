<script lang="ts">
	import type { IPerson } from "$lib/database/films";

    export let person:IPerson
    </script>
<div class="actor-card">
    <img class="actor-card_img" src={person.photo} alt="hardy"/>
    <p class="actor-card_name">{person.name}</p> 
</div>
<style>
    .actor-card_img{
        border-radius: 15px;
        width: 100%;
    }
    	.actor-card_name {
		text-align:center ;
        padding: 15px;
        
	}
</style>