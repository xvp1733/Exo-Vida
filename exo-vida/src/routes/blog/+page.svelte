<script>
  import { base } from '$app/paths';
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  // 1. Estado reactivo nativo mediante Runas (Svelte 5)
  let categoriaSeleccionada = $state('todos');

  const categorias = [
    { id: 'todos', etiqueta: 'Ver Todo' },
    { id: 'logistica', etiqueta: 'Procesamiento y Logística' },
    { id: 'comunidad', etiqueta: 'Ecosistemas Locales' },
    { id: 'tecnologia', etiqueta: 'Sistemas e Infraestructura' },
    { id: 'exo-holdings', etiqueta: 'Exo Holdings' }
  ];

  // Listado estático de artículos de producción
  const posts = [
    {
      id: 'optimizacion-tiempos-respuesta-charallave',
      titulo: 'Optimización de tiempos de respuesta en la entrega de suministros médicos',
      resumen: 'Análisis técnico sobre cómo rediseñamos el flujo de despacho logístico en Charallave para reducir un 40% el tiempo muerto en el procesamiento de solicitudes críticas.',
      categoria: 'logistica',
      fecha: '12 Jul, 2026',
      tiempoLectura: '4 min',
      imagen: 'https://images.unsplash.com/photo-1581578731548-c64695cc6952?auto=format&fit=crop&w=600&q=80'
    },
    {
      id: 'ingenieria-social-multi-nicho',
      titulo: 'El enfoque multi-nicho: Más allá de un menú de asistencia estático',
      resumen: 'Analizamos por qué la asignación de tiempos de atención y la optimización de procesos modulares resulta sustancialmente más eficaz para combatir crisis en múltiples frentes paralelos.',
      categoria: 'comunidad',
      fecha: '28 Jun, 2026',
      tiempoLectura: '6 min',
      imagen: 'https://images.unsplash.com/photo-1521737711867-e3b90473bd58?auto=format&fit=crop&w=600&q=80'
    },
    {
      id: 'infraestructura-it-redes-ayuda',
      titulo: 'Modelado de datos para la distribución transparente de donaciones',
      resumen: 'La arquitectura tecnológica y bases de datos relacionales detrás del sistema de monitoreo en tiempo real implementado por Exo Vida en el eje de Miranda.',
      categoria: 'tecnologia',
      fecha: '15 May, 2026',
      tiempoLectura: '8 min',
      imagen: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=600&q=80'
    }
  ];

  // 2. Reactividad óptima mediante Runas derivadas
  let postsFiltrados = $derived(
    categoriaSeleccionada === 'todos'
      ? posts
      : posts.filter(post => post.categoria === categoriaSeleccionada)
  );
</script>

<svelte:head>
  <title>Blog Operativo & Bitácoras | Exo Vida</title>
  <meta name="description" content="Artículos técnicos, reportes logísticos de impacto e ingeniería social aplicados en el terreno por Exo Vida." />
</svelte:head>

<Header />

<main class="blog-page">
  <!-- Encabezado de Sección -->
  <header class="blog-header">
    <span class="tag">Exo Vida Journal</span>
    <h1>Análisis, Logística e Impacto</h1>
    <p class="subtitle">
      Documentamos nuestros despliegues técnicos, modelado de datos y estrategias de optimización social con el rigor de Exo Holdings.
    </p>

    <!-- Filtros de Categoría Mejorados -->
    <nav class="categories-nav" aria-label="Filtros de categorías del blog">
      {#each categorias as cat}
        <button 
          class="cat-btn" 
          class:active={categoriaSeleccionada === cat.id}
          on:click={() => categoriaSeleccionada = cat.id}
          aria-pressed={categoriaSeleccionada === cat.id}
        >
          {cat.etiqueta}
        </button>
      {/each}
    </nav>
  </header>

  <!-- Grilla Dinámica de Artículos con Animación Suave -->
  <section class="blog-grid" aria-live="polite">
    {#each postsFiltrados as post (post.id)}
      <article class="post-card">
        <!-- Imagen con contenedor adaptativo -->
        <div class="image-wrapper">
          <img src={post.imagen} alt={post.titulo} class="post-image" loading="lazy" />
          <span class="category-badge">{post.categoria.replace('-', ' ')}</span>
        </div>

        <div class="post-content">
          <div class="post-meta">
            <span class="post-date">
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
              {post.fecha}
            </span>
            <span class="reading-time">
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
              {post.tiempoLectura}
            </span>
          </div>

          <h2>
            <a href="{base}/blog/{post.id}">{post.titulo}</a>
          </h2>
          <p class="summary">{post.resumen}</p>

          <div class="post-footer">
            <a href="{base}/blog/{post.id}" class="read-more">
              <span>Leer Reporte</span>
              <svg class="arrow" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
            </a>
          </div>
        </div>
      </article>
    {:else}
      <div class="no-posts">
        <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
        <p>No se encontraron artículos en esta categoría en este momento.</p>
      </div>
    {/each}
  </section>
</main>

<Footer />

<style>
  .blog-page {
    min-height: 100vh;
    padding: 6rem 10% 8rem 10%;
    background-color: #f8fafc;
  }

  .blog-header {
    text-align: center;
    max-width: 850px;
    margin: 0 auto 5rem auto;
  }

  .blog-header .tag {
    color: #10b981;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 0.85rem;
    letter-spacing: 1.5px;
    display: block;
    margin-bottom: 1.25rem;
  }

  h1 {
    font-size: clamp(2.5rem, 5vw, 3.5rem);
    color: #1f2937;
    font-weight: 800;
    letter-spacing: -1.5px;
    margin-bottom: 1.5rem;
    line-height: 1.15;
  }

  .subtitle {
    color: #4b5563;
    font-size: 1.15rem;
    line-height: 1.7;
    margin-bottom: 3rem;
  }

  /* Barra de Navegación de Categorías */
  .categories-nav {
    display: inline-flex;
    background-color: #ffffff;
    padding: 0.4rem;
    border-radius: 50px;
    border: 1px solid #e2e8f0;
    gap: 0.25rem;
    flex-wrap: wrap;
    justify-content: center;
    box-shadow: 0 4px 12px rgba(15, 23, 42, 0.03);
  }

  .cat-btn {
    background: none;
    border: none;
    padding: 0.6rem 1.4rem;
    border-radius: 50px;
    font-size: 0.85rem;
    font-weight: 600;
    color: #64748b;
    cursor: pointer;
    transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .cat-btn:hover {
    color: #1f2937;
  }

  .cat-btn.active {
    background-color: #10b981;
    color: #ffffff;
    box-shadow: 0 4px 12px rgba(16, 185, 129, 0.2);
  }

  /* Grid del Blog */
  .blog-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 3rem;
    max-width: 1280px;
    margin: 0 auto;
  }

  /* Tarjetas Profesionales */
  .post-card {
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 24px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    box-shadow: 0 10px 30px rgba(15, 23, 42, 0.01);
    transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1), border-color 0.3s;
  }

  .post-card:hover {
    transform: translateY(-6px);
    border-color: rgba(16, 185, 129, 0.3);
    box-shadow: 0 20px 40px rgba(16, 185, 129, 0.05);
  }

  .image-wrapper {
    position: relative;
    height: 240px;
    overflow: hidden;
    background-color: #e2e8f0;
  }

  .post-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
  }

  .post-card:hover .post-image {
    transform: scale(1.05);
  }

  .category-badge {
    position: absolute;
    top: 1rem;
    left: 1rem;
    background-color: rgba(15, 23, 42, 0.85);
    backdrop-filter: blur(4px);
    color: #ffffff;
    padding: 0.4rem 0.9rem;
    border-radius: 50px;
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  /* Contenido Interno */
  .post-content {
    padding: 2.5rem 2rem;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .post-meta {
    display: flex;
    gap: 1.25rem;
    font-size: 0.8rem;
    color: #64748b;
    margin-bottom: 1.25rem;
    font-weight: 600;
  }

  .post-meta span {
    display: flex;
    align-items: center;
    gap: 0.35rem;
  }

  h2 {
    margin-bottom: 1rem;
    line-height: 1.35;
  }

  h2 a {
    font-size: 1.35rem;
    color: #1f2937;
    font-weight: 800;
    text-decoration: none;
    letter-spacing: -0.3px;
    transition: color 0.2s;
  }

  h2 a:hover {
    color: #10b981;
  }

  .summary {
    color: #4b5563;
    font-size: 0.95rem;
    line-height: 1.65;
    margin-bottom: 2rem;
    flex-grow: 1;
  }

  /* Pie de la Tarjeta */
  .post-footer {
    border-top: 1px solid #f1f5f9;
    padding-top: 1.5rem;
  }

  .read-more {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    color: #10b981;
    font-weight: 700;
    text-decoration: none;
    font-size: 0.95rem;
    transition: gap 0.2s;
  }

  .read-more .arrow {
    transition: transform 0.2s;
  }

  .read-more:hover .arrow {
    transform: translateX(4px);
  }

  /* Estado de Vacío */
  .no-posts {
    grid-column: 1 / -1;
    text-align: center;
    padding: 5rem 2rem;
    color: #94a3b8;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    background: #ffffff;
    border-radius: 24px;
    border: 1px dashed #cbd5e1;
  }

  /* Responsivo */
  @media (max-width: 768px) {
    .blog-page {
      padding: 5rem 6%;
    }

    .categories-nav {
      border-radius: 24px;
      padding: 0.5rem;
    }

    .cat-btn {
      padding: 0.5rem 1rem;
      font-size: 0.8rem;
    }

    .post-content {
      padding: 2rem 1.5rem;
    }
  }
</style>