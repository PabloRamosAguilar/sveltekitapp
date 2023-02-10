<script>
    import {onMount} from "svelte";
    import Buscar from "./Buscar.svelte";

    let data = [];
    let busqueda = "Pepe";
    onMount( async() => {
        const response = await fetch('https://raw.githubusercontent.com/PabloRamosAguilar/JSON/main/comentarios.JSON');
         data = await response.json();
    });
</script>

<Buscar bind:busqueda/>

<hr>

{#each data as articulo }
   {articulo.nombre} - {articulo.comentario}<br>
   <br>
{/each}
<hr>


