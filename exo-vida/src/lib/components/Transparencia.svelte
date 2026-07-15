<script>
  // Estructura de producción de estadísticas con iconos vectoriales (SVG)
  const estadisticas = [
    {
      cifra: "+1,200",
      etiqueta: "Familias Atendidas",
      // SVG: Usuarios conectados / Comunidad
      svg: `<svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`
    },
    {
      cifra: "45 min",
      etiqueta: "Tiempo de Procesamiento Promedio",
      // SVG: Cronómetro / Optimización de flujo logístico
      svg: `<svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="10" x2="14" y1="2" y2="2"/><line x1="12" x2="12" y1="14" y2="11"/><circle cx="12" cy="14" r="8"/></svg>`
    },
    {
      cifra: "+30",
      etiqueta: "Voluntarios Activos en Miranda",
      // SVG: Manos / Colaboración activa y soporte local
      svg: `<svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 9V5a3 3 0 0 0-3-3l-4 9v11h11.28a2 2 0 0 0 2-1.7l1.38-9a2 2 0 0 0-2-2.3zM7 22H4a2 2 0 0 1-2-2v-7a2 2 0 0 1 2-2h3"/></svg>`
    },
    {
      cifra: "100%",
      etiqueta: "Transparencia de Recursos",
      // SVG: Escudo con check / Seguridad y auditoría interna
      svg: `<svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="m9 11 2 2 4-4"/></svg>`
    }
  ];
</script>

<section id="transparencia" class="transparencia-section">
  <div class="content-wrapper">
    <!-- Lateral Izquierdo: Información institucional del Holding -->
    <div class="text-side">
      <span class="section-tag">Cuentas Claras</span>
      <h2>Por qué confiar en Exo Vida</h2>
      <p>
        Bajo la dirección estratégica de <strong>Exo Holdings</strong>, redefinimos el concepto clásico de ayuda humanitaria. En lugar de limitarnos a distribuir un menú cerrado, optimizamos integralmente el tiempo de atención y el flujo de procesamiento de cada pedido para garantizar que el impacto llegue con precisión quirúrgica donde más se necesita.
      </p>
      
      <div class="quote-card">
        <p class="quote">
          "Nosotros vendemos tiempo de atención, de procesar pedidos y no un menú. Diseñamos un ecosistema social de respuesta rápida y auditoría transparente capaz de integrarse con múltiples nichos."
        </p>
        <span class="quote-author">— Dirección General de Procesos, Exo Holdings</span>
      </div>
    </div>
    
    <!-- Lateral Derecho: Cuadrícula con KPIs dinámicos e Iconos SVG -->
    <div class="stats-grid">
      {#each estadisticas as stat}
        <div class="stat-card">
          <div class="icon-container">
            {@html stat.svg}
          </div>
          <h3>{stat.cifra}</h3>
          <p>{stat.etiqueta}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .transparencia-section {
    padding: 6.5rem 10%;
    background-color: #f8fafc;
    border-bottom: 1px solid #e2e8f0;
  }

  .content-wrapper {
    display: grid;
    grid-template-columns: 1.15fr 1fr;
    gap: 5rem;
    align-items: center;
    max-width: 1280px;
    margin: 0 auto;
  }

  .text-side {
    text-align: left;
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

  p {
    color: #4b5563;
    line-height: 1.75;
    font-size: 1.05rem;
    margin-bottom: 2.25rem;
  }

  .quote-card {
    border-left: 4px solid #10b981;
    background-color: #ffffff;
    padding: 1.75rem 2rem;
    border-radius: 0 16px 16px 0;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.02);
  }

  .quote {
    font-style: italic;
    color: #374151;
    margin-bottom: 0.75rem;
    font-size: 0.98rem;
    line-height: 1.6;
  }

  .quote-author {
    font-size: 0.8rem;
    font-weight: 700;
    color: #9ca3af;
    text-transform: uppercase;
    letter-spacing: 1px;
    display: block;
  }

  /* Grid de KPIs */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.75rem;
  }

  .stat-card {
    background-color: #ffffff;
    padding: 2.5rem 1.75rem;
    border-radius: 24px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(15, 23, 42, 0.015);
    border: 1px solid #e2e8f0;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stat-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 20px 40px rgba(16, 185, 129, 0.06);
    border-color: rgba(16, 185, 129, 0.25);
  }

  .icon-container {
    background-color: #f0fdf4;
    color: #10b981;
    width: 52px;
    height: 52px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.5rem;
    transition: all 0.3s ease;
  }

  .stat-card:hover .icon-container {
    background-color: #10b981;
    color: #ffffff;
  }

  /* Control y estilización de los SVGs renderizados con {@html} */
  :global(.stat-icon) {
    width: 24px;
    height: 24px;
    stroke-width: 2.25;
  }

  .stat-card h3 {
    font-size: 2.25rem;
    color: #1f2937;
    font-weight: 850;
    margin-bottom: 0.5rem;
    letter-spacing: -1px;
  }

  .stat-card p {
    font-size: 0.9rem;
    color: #64748b;
    margin-bottom: 0;
    font-weight: 600;
    line-height: 1.4;
  }

  /* Responsivo para Tablets y Celulares */
  @media (max-width: 992px) {
    .content-wrapper {
      grid-template-columns: 1fr;
      gap: 4rem;
    }
    
    .transparencia-section {
      padding: 5rem 6%;
    }
  }

  @media (max-width: 560px) {
    .stats-grid {
      grid-template-columns: 1fr;
    }
    
    .stat-card {
      padding: 2.25rem 1.5rem;
    }
  }
</style>