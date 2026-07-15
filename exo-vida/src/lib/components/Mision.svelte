<script>
  // Pilares operativos de la misión con vectores SVG profesionales
  const pilares = [
    {
      titulo: "Velocidad de Procesamiento",
      descripcion: "Nuestra prioridad absoluta es el tiempo. Minimizamos la burocracia logística para que la ayuda crítica sea procesada y entregada en tiempo récord en las comunidades de Charallave.",
      // SVG: Rayo / Eficiencia temporal
      svg: `<svg class="pilar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>`
    },
    {
      titulo: "Estructura Multi-nicho Adaptable",
      descripcion: "No operamos bajo un catálogo rígido. Diseñamos un canal de procesamiento dinámico capaz de canalizar soluciones médicas, alimentarias o tecnológicas según la demanda en tiempo real.",
      // SVG: Bloques modulares / Arquitectura flexible
      svg: `<svg class="pilar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m12 3-10 9h3v8h14v-8h3L12 3z"/></svg>`
    },
    {
      titulo: "Rigor y Auditoría de Recursos",
      descripcion: "Cada pedido, donación e insumo es catalogado y rastreado con el mismo rigor y sistemas de trazabilidad que implementa Exo Holdings a nivel corporativo.",
      // SVG: Gráfico de líneas / Control analítico
      svg: `<svg class="pilar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="m18.7 8-5.1 5.2-2.8-2.7L7 14.3"/></svg>`
    }
  ];
</script>

<section id="nosotros" class="mision-section">
  <div class="container">
    <!-- Columna Izquierda: Bloque de Misión Central -->
    <div class="mision-main">
      <span class="section-tag">Nuestra Razón de Ser</span>
      <h2>Misión con Enfoque de Ingeniería Social</h2>
      <p class="main-text">
        En Exo Vida no distribuimos un menú estático de asistencia. Nuestra misión es <strong>diseñar, optimizar y disponibilizar el mejor tiempo de atención y procesamiento de pedidos de ayuda humanitaria</strong>.
      </p>
      <p class="sub-text">
        Transformamos la infraestructura de soporte comunitario en Miranda aplicando tecnología y procesos ágiles, garantizando que el esfuerzo de nuestros aliados se traduzca en un impacto inmediato, auditable y de largo plazo.
      </p>

      <!-- Tarjeta destacada de compromiso corporativo -->
      <div class="commitment-card">
        <div class="commitment-badge">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
          <span>Garantía de Optimización</span>
        </div>
        <p>Alineamos cada centavo y cada hora de voluntariado bajo metodologías de mejora continua (Lean/Kaizen).</p>
      </div>
    </div>

    <!-- Columna Derecha: Pilares de Ejecución -->
    <div class="mision-pilares">
      {#each pilares as pilar}
        <div class="pilar-card">
          <div class="pilar-icon-wrapper">
            {@html pilar.svg}
          </div>
          <div class="pilar-info">
            <h3>{pilar.titulo}</h3>
            <p>{pilar.descripcion}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .mision-section {
    padding: 6.5rem 10%;
    background-color: #ffffff;
    border-bottom: 1px solid #e2e8f0;
  }

  .container {
    display: grid;
    grid-template-columns: 1.1fr 1fr;
    gap: 6rem;
    max-width: 1280px;
    margin: 0 auto;
    align-items: start;
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
    line-height: 1.2;
    margin-bottom: 1.5rem;
    letter-spacing: -0.5px;
  }

  .main-text {
    font-size: 1.15rem;
    color: #374151;
    line-height: 1.7;
    margin-bottom: 1.25rem;
  }

  .sub-text {
    font-size: 1rem;
    color: #64748b;
    line-height: 1.75;
    margin-bottom: 2.5rem;
  }

  /* Tarjeta de Compromiso */
  .commitment-card {
    background-color: #f8fafc;
    border: 1px solid #e2e8f0;
    padding: 1.75rem;
    border-radius: 20px;
  }

  .commitment-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    color: #10b981;
    font-weight: 700;
    font-size: 0.85rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 0.75rem;
  }

  .commitment-card p {
    color: #4b5563;
    font-size: 0.95rem;
    line-height: 1.6;
    margin: 0;
  }

  /* Pilares (Columna Derecha) */
  .mision-pilares {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .pilar-card {
    display: flex;
    gap: 1.5rem;
    padding: 2rem;
    background-color: #f8fafc;
    border-radius: 20px;
    border: 1px solid #e2e8f0;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .pilar-card:hover {
    transform: translateX(6px);
    background-color: #ffffff;
    border-color: rgba(16, 185, 129, 0.3);
    box-shadow: 0 10px 30px rgba(16, 185, 129, 0.04);
  }

  .pilar-icon-wrapper {
    background-color: #ffffff;
    color: #10b981;
    width: 48px;
    height: 48px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    box-shadow: 0 4px 12px rgba(15, 23, 42, 0.03);
    border: 1px solid #e2e8f0;
    transition: all 0.3s ease;
  }

  .pilar-card:hover .pilar-icon-wrapper {
    background-color: #10b981;
    color: #ffffff;
    border-color: #10b981;
  }

  :global(.pilar-icon) {
    width: 22px;
    height: 22px;
  }

  .pilar-info h3 {
    font-size: 1.15rem;
    color: #1f2937;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }

  .pilar-info p {
    color: #4b5563;
    font-size: 0.95rem;
    line-height: 1.65;
    margin: 0;
  }

  /* Adaptabilidad */
  @media (max-width: 1024px) {
    .container {
      grid-template-columns: 1fr;
      gap: 4rem;
    }

    .mision-section {
      padding: 5rem 6%;
    }
  }

  @media (max-width: 640px) {
    .pilar-card {
      flex-direction: column;
      gap: 1.25rem;
      padding: 1.75rem;
    }
  }
</style>