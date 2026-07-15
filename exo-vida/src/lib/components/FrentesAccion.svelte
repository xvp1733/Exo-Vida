<script>
  // Datos estructurados reales optimizados para producción con SVGs vectoriales inline
  const frentes = [
    {
      id: "proyectos-sociales", // Alineado con el Header para scroll automático
      titulo: "Desarrollo Social Sostenible",
      descripcion: "Impulsamos micro-economías locales en comunidades vulnerables de Charallave, aplicando metodologías que garantizan la autosuficiencia a largo plazo sin dependencias infinitas de donaciones.",
      // SVG: Crecimiento / Planta corporativa
      svg: `<svg class="frente-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.25" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22V12M12 12c-2.5 0-4-1-5-2.5S6.5 6 9 6c2.5 0 3 1.5 3 3.5M12 12c2.5 0 4-1 5-2.5S17.5 6 15 6c-2.5 0-3 1.5-3 3.5M12 6V2"/></svg>`
    },
    {
      id: "optimizacion", // Alineado con el Header para scroll automático
      titulo: "Optimización de Procesamiento",
      descripcion: "Reducimos radicalmente los tiempos de respuesta y entrega mediante un control de flujo analítico y la automatización de procesos heredada de Exo Holdings. Gestionamos tiempo de atención con precisión de ingeniería.",
      // SVG: Flujo de procesamiento / Línea de tiempo optimizada
      svg: `<svg class="frente-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.25" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10"/></svg>`
    },
    {
      id: "alianzas", // Alineado con el Header para scroll automático
      titulo: "Atención Multi-nicho Integrada",
      descripcion: "Nuestra arquitectura operativa es modular, lo que nos faculta para coordinar y procesar solicitudes simultáneas en sectores diversos (salud, educación, infraestructura) sin saturar los canales logísticos.",
      // SVG: Red de nichos interconectados / Nodos jerárquicos
      svg: `<svg class="frente-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.25" stroke-linecap="round" stroke-linejoin="round"><path d="M5 17a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z"/><path d="M19 13a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z"/><path d="M12 7a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z"/><path d="M12 23a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z"/><path d="M7.5 13.5 10 11.5"/><path d="M14 9.5 16.5 7.5"/></svg>`
    }
  ];
</script>

<section id="frentes" class="frentes-section">
  <span class="section-tag">Impacto Inteligente</span>
  <h2>Nuestros Frentes de Acción</h2>
  <p class="subtitle">Aplicamos la disciplina estructural de un holding corporativo al servicio de la optimización logística y la ayuda humanitaria.</p>

  <div class="grid-frentes">
    {#each frentes as frente}
      <div class="frente-card" id={frente.id}>
        <div class="icono-wrapper">
          <!-- Renderizado nativo y seguro de vectores SVG en Svelte -->
          {@html frente.svg}
        </div>
        <h3>{frente.titulo}</h3>
        <p>{frente.descripcion}</p>
      </div>
    {/each}
  </div>
</section>

<style>
  .frentes-section {
    padding: 6.5rem 10%;
    text-align: center;
    background-color: #ffffff;
    border-bottom: 1px solid #e2e8f0;
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
    max-width: 680px;
    margin: 0 auto 4.5rem auto;
    color: #4b5563;
    font-size: 1.1rem;
    line-height: 1.7;
  }

  .grid-frentes {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 2.5rem;
    max-width: 1280px;
    margin: 0 auto;
  }

  .frente-card {
    background-color: #f8fafc;
    padding: 3.5rem 2.25rem;
    border-radius: 24px;
    text-align: left;
    border: 1px solid #e2e8f0;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .frente-card:hover {
    transform: translateY(-8px);
    background-color: #ffffff;
    box-shadow: 0 20px 40px rgba(16, 185, 129, 0.06);
    border-color: rgba(16, 185, 129, 0.25);
  }

  .icono-wrapper {
    background-color: #ffffff;
    color: #10b981;
    width: 64px;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 16px;
    margin-bottom: 1.75rem;
    box-shadow: 0 8px 20px rgba(15, 23, 42, 0.04);
    border: 1px solid #e2e8f0;
    transition: all 0.3s ease;
  }

  .frente-card:hover .icono-wrapper {
    background-color: #10b981;
    color: #ffffff;
    border-color: #10b981;
    box-shadow: 0 8px 20px rgba(16, 185, 129, 0.25);
  }

  /* Modificador global exclusivo para inyección dinámica de SVG en el DOM */
  :global(.frente-icon) {
    width: 26px;
    height: 26px;
  }

  .frente-card h3 {
    font-size: 1.3rem;
    color: #1f2937;
    margin-bottom: 1rem;
    font-weight: 700;
    letter-spacing: -0.2px;
  }

  .frente-card p {
    color: #4b5563;
    font-size: 0.95rem;
    line-height: 1.7;
  }

  @media (max-width: 768px) {
    .frentes-section {
      padding: 5rem 6%;
    }
    
    .frente-card {
      padding: 2.75rem 1.75rem;
    }
  }
</style>