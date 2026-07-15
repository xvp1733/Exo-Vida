<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  // Importación de todos los legos de tu árbol de archivos
  import Hero from '$lib/components/Hero.svelte';
  import Mision from '$lib/components/Mision.svelte';
  import Transparencia from '$lib/components/Transparencia.svelte';
  import FrentesAccion from '$lib/components/FrentesAccion.svelte';
  import Proyectos from '$lib/components/Proyectos.svelte';
  import Voluntarios from '$lib/components/Voluntarios.svelte';
  import Voluntariado from '$lib/components/Voluntariado.svelte';
</script>

<svelte:head>
  <title>Exo Vida | Ingeniería Social y Optimización Logística</title>
  <meta name="description" content="Maximizando el tiempo de atención y procesamiento de solicitudes de ayuda humanitaria en Charallave. Respaldado por Exo Holdings." />
</svelte:head>

<!-- Header Único -->
<Header />

<main id="main-content">
  
  <!-- Sección: Inicio -->
  <section id="inicio">
    <Hero />
  </section>

  <!-- Sección: Quiénes Somos (Misión) -->
  <section id="nosotros">
    <Mision />
  </section>

  <!-- Sección: Transparencia de Procesos -->
  <section id="transparencia">
    <Transparencia />
  </section>

  <!-- Sección: Procesos de Ayuda y Canales -->
  <section id="frentes">
    <FrentesAccion />
  </section>

  <!-- Sección: Proyectos y Frentes Activos -->
  <section id="proyectos-sociales">
    <Proyectos />
  </section>

  <!-- Sección: El Equipo de Voluntarios Activos (Testimonios/Directorio) -->
  <section id="equipo">
    <Voluntarios />
  </section>

  <!-- Sección: Formulario de Registro / Ser Voluntario -->
  <section id="voluntariado">
    <Voluntariado />
  </section>

</main>

<Footer />

<style>
  :global(html) {
    scroll-behavior: smooth;
    font-family: 'Inter', sans-serif;
    background-color: #f8fafc;
  }

  main {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    width: 100%;
    overflow-x: hidden;
  }

  /* Asegura que al hacer clic en los enlaces, el scroll no corte el título con el menú pegajoso */
  section {
    scroll-margin-top: 80px; 
  }
</style>