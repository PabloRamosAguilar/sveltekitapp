<script>
    import {onMount} from "svelte";
    import Buscar from "./Buscar.svelte";

    let data = [];
    let datosFiltrados = [];
   
    onMount( async() => {
        const response = await fetch('https://raw.githubusercontent.com/PabloRamosAguilar/JSON/main/comentarios.JSON');
         data = await response.json();
    });

    $:datosFiltrados = data.filter(articulo => RegExp(busqueda, "i").test(articulo.nombre));

   let busqueda = "";
</script>

<Buscar bind:busqueda/>

<hr>

{#each datosFiltrados as articulo }
   {articulo.nombre} - {articulo.comentario}<br>
   <br>
{/each}
<hr>


