<script>
  import { base } from '$app/paths';

  // 1. Declaración de estado reactivo nativo mediante Runas (Svelte 5)
  let filtroActivo = $state('todos');

  const categorias = [
    { id: 'todos', etiqueta: 'Todos los Frentes' },
    { id: 'logistica', etiqueta: 'Procesamiento y Logística' },
    { id: 'desarrollo', etiqueta: 'Desarrollo Sostenible' },
    { id: 'infraestructura', etiqueta: 'Infraestructura y Salud' }
  ];

  // Listado estático de proyectos operativos
  const proyectos = [
    {
      id: 'red-logistica-charallave',
      categoria: 'logistica',
      titulo: 'Optimización del Canal de Suministro',
      ubicacion: 'Casco Central, Charallave',
      metrica: 'Reducción del 40% en tiempos de espera',
      descripcion: 'Implementación de un sistema de control de inventario y flujos de despacho analítico para procesar pedidos de insumos médicos críticos con velocidad corporativa.',
      svg: `<svg class="project-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/><polyline points="3.27 6.96 12 12.01 20.73 6.96"/><line x1="12" y1="22.08" x2="12" y2="12"/></svg>`
    },
    {
      id: 'microeconomias-miranda',
      categoria: 'desarrollo',
      titulo: 'Ecosistemas de Autonomía Local',
      ubicacion: 'Eje Periférico, Miranda',
      metrica: '3 micro-empresas autosuficientes',
      descripcion: 'Diseño de incentivos y estructuras operativas modulares para capacitar a comunidades en la gestión de sus propios recursos, quebrando el ciclo de dependencia.',
      svg: `<svg class="project-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>`
    },
    {
      id: 'conectividad-atencion',
      categoria: 'infraestructura',
      titulo: 'Células de Atención Multi-nicho',
      ubicacion: 'Comunidades Organizadas',
      metrica: 'Procesamiento simultáneo en 3 sectores',
      descripcion: 'Despliegue de nodos de atención equipados para dar respuesta paralela en telemedicina preventiva, soporte técnico básico y educación digital guiada.',
      svg: `<svg class="project-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"/><path d="M12 6v6l4 2"/></svg>`
    }
  ];

  // 2. Cálculo reactivo derivado (Sustituye al problemático '$:')
  let proyectosFiltrados = $derived(
    filtroActivo === 'todos' 
      ? proyectos 
      : proyectos.filter(p => p.categoria === filtroActivo)
  );
</script>

<section id="proyectos" class="proyectos-section">
  <div class="section-header">
    <span class="section-tag">Operaciones en el Terreno</span>
    <h2>Frentes y Proyectos Ejecutados</h2>
    <p class="subtitle">Resultados medibles y sistemas de atención desplegados con el respaldo estratégico de Exo Holdings.</p>
    
    <!-- Filtros de Navegación Profesional -->
    <div class="filter-container">
      {#each categorias as cat}
        <button 
          class="filter-btn" 
          class:active={filtroActivo === cat.id}
          on:click={() => filtroActivo = cat.id}
        >
          {cat.etiqueta}
        </button>
      {/each}
    </div>
  </div>

  <!-- Grid Dinámica de Proyectos -->
  <div class="projects-grid">
    {#each proyectosFiltrados as proyecto (proyecto.id)}
      <div class="project-card">
        <div class="card-top">
          <div class="icon-box">
            {@html proyecto.svg}
          </div>
          <span class="location">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
            {proyecto.ubicacion}
          </span>
        </div>

        <h3>{proyecto.titulo}</h3>
        <p class="description">{proyecto.descripcion}</p>

        <div class="card-footer">
          <div class="metric-badge">
            <span class="metric-label">Impacto Clave</span>
            <span class="metric-value">{proyecto.metrica}</span>
          </div>
        </div>
      </div>
    {/each}
  </div>
</section>

<style>
  .proyectos-section {
    padding: 6.5rem 10%;
    background-color: #f8fafc;
    border-bottom: 1px solid #e2e8f0;
  }

  .section-header {
    text-align: center;
    max-width: 750px;
    margin: 0 auto 4rem auto;
  }

  .section-tag {
    color: #10b981;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 0.85rem;
    letter-spacing: 1.5px;
    display: block;
    margin-bottom: 1.25rem;
  }

  h2 {
    font-size: clamp(2rem, 4vw, 2.5rem);
    color: #1f2937;
    font-weight: 800;
    margin-bottom: 1.25rem;
    letter-spacing: -0.5px;
  }

  .subtitle {
    color: #4b5563;
    font-size: 1.1rem;
    line-height: 1.7;
    margin-bottom: 2.5rem;
  }

  /* Contenedor de Botones de Filtro */
  .filter-container {
    display: inline-flex;
    background-color: #ffffff;
    padding: 0.4rem;
    border-radius: 50px;
    border: 1px solid #e2e8f0;
    box-shadow: 0 4px 12px rgba(15, 23, 42, 0.03);
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.25rem;
  }

  .filter-btn {
    background: none;
    border: none;
    padding: 0.6rem 1.4rem;
    border-radius: 50px;
    font-size: 0.9rem;
    font-weight: 600;
    color: #64748b;
    cursor: pointer;
    transition: all 0.25s ease;
  }

  .filter-btn:hover {
    color: #1f2937;
  }

  .filter-btn.active {
    background-color: #10b981;
    color: #ffffff;
    box-shadow: 0 4px 12px rgba(16, 185, 129, 0.2);
  }

  /* Grid de Tarjetas */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
    gap: 2.5rem;
    max-width: 1280px;
    margin: 0 auto;
  }

  .project-card {
    background-color: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 24px;
    padding: 2.5rem 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 10px 30px rgba(15, 23, 42, 0.01);
  }

  .project-card:hover {
    transform: translateY(-6px);
    border-color: rgba(16, 185, 129, 0.3);
    box-shadow: 0 20px 40px rgba(16, 185, 129, 0.05);
  }

  .card-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1.75rem;
  }

  .icon-box {
    color: #10b981;
    background-color: #f0fdf4;
    width: 48px;
    height: 48px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  :global(.project-icon) {
    width: 24px;
    height: 24px;
  }

  .location {
    font-size: 0.85rem;
    color: #64748b;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 0.35rem;
    background-color: #f8fafc;
    padding: 0.4rem 0.8rem;
    border-radius: 50px;
    border: 1px solid #e2e8f0;
  }

  h3 {
    font-size: 1.3rem;
    color: #1f2937;
    font-weight: 700;
    margin-bottom: 1rem;
    letter-spacing: -0.3px;
    line-height: 1.3;
  }

  .description {
    color: #4b5563;
    font-size: 0.95rem;
    line-height: 1.65;
    margin-bottom: 2rem;
    flex-grow: 1;
  }

  /* Insignia de métrica inferior */
  .card-footer {
    border-top: 1px solid #f1f5f9;
    padding-top: 1.25rem;
  }

  .metric-badge {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    text-align: left;
  }

  .metric-label {
    font-size: 0.75rem;
    color: #94a3b8;
    text-transform: uppercase;
    font-weight: 700;
    letter-spacing: 0.5px;
  }

  .metric-value {
    font-size: 1.05rem;
    color: #10b981;
    font-weight: 700;
  }

  /* Responsivo */
  @media (max-width: 768px) {
    .proyectos-section {
      padding: 5rem 6%;
    }

    .project-card {
      padding: 2rem 1.5rem;
    }
  }
</style>