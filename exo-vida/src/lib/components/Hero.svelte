<script>
  import { base } from '$app/paths';

  const titulo = "Transformando realidades desde Charallave para el mundo";
  const descripcion = "En Exo Vida optimizamos los procesos de ayuda social y coordinamos esfuerzos en múltiples nichos para llevar bienestar donde más se necesita, con el respaldo estratégico de Exo Holdings.";

  // Función para manejar el scroll suave idéntico al Header
  function handleAnchorClick(event) {
    const link = event.currentTarget;
    const anchor = link.getAttribute('href').split('#')[1];
    const targetElement = document.getElementById(anchor);
    
    if (targetElement) {
      event.preventDefault();
      targetElement.scrollIntoView({ behavior: 'smooth' });
    }
  }
</script>

<section id="inicio" class="hero-container">
  <!-- Malla técnica de fondo para dar profundidad visual -->
  <div class="hero-grid"></div>
  <div class="hero-overlay"></div>
  
  <div class="hero-content">
    <div class="badge-wrapper">
      <span class="badge">
        <svg class="badge-icon" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="m12 8-4 4 4 4M16 12H8"/></svg>
        Iniciativa Global
      </span>
    </div>
    
    <h1>{titulo}</h1>
    <p>{descripcion}</p>
    
    <div class="hero-buttons">
      <a href="{base}/#voluntariado" class="btn-primary" on:click={handleAnchorClick}>
        <span>Quiero Ser Voluntario</span>
        <!-- Icono: Flecha indicativa de acción -->
        <svg class="btn-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
      </a>
      <a href="{base}/#frentes" class="btn-secondary" on:click={handleAnchorClick}>
        <span>Ver Qué Hacemos</span>
        <!-- Icono: Ojo / Descubrir -->
        <svg class="btn-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M2 12s3-7 10-7 10 7 10 7-3 7-10 7-10-7-10-7Z"/><circle cx="12" cy="12" r="3"/></svg>
      </a>
    </div>
  </div>
</section>

<style>
  .hero-container {
    position: relative;
    background: radial-gradient(circle at 50% 30%, #065f46 0%, #022c22 100%);
    min-height: 85vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 6rem 5%;
    text-align: center;
    color: #ffffff;
    overflow: hidden;
  }

  /* Cuadrícula o patrón de ingeniería de fondo (SVG inline) */
  .hero-grid {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='80' height='80' viewBox='0 0 80 80'%3E%3Cg fill='%2310b981' fill-opacity='0.03'%3E%3Cpath fill-rule='evenodd' d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm1-61c3.148 0 5.7-2.552 5.7-5.7 0-3.148-2.552-5.7-5.7-5.7-3.148 0-5.7 2.552-5.7 5.7 0 3.148 2.552 5.7 5.7 5.7zm22-3c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM106 17c3.148 0 5.7-2.552 5.7-5.7 0-3.148-2.552-5.7-5.7-5.7-3.148 0-5.7 2.552-5.7 5.7 0 3.148 2.552 5.7 5.7 5.7zm-2 56c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm-.021-39.61c-1.195-.011-2.231-.73-2.634-1.802-.545-1.455.19-3.083 1.645-3.628a2.716 2.716 0 0 1 1.984.053c1.425.592 2.112 2.228 1.542 3.659-.4 1.002-1.371 1.666-2.537 1.718z'/%3E%3C/g%3E%3C/svg%3E");
    opacity: 0.85;
    pointer-events: none;
  }

  .hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: radial-gradient(circle at 50% 30%, rgba(16, 185, 129, 0.12) 0%, rgba(2, 44, 34, 0) 80%);
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 880px;
    margin: 0 auto;
  }

  .badge-wrapper {
    display: flex;
    justify-content: center;
    margin-bottom: 1.75rem;
  }

  .badge {
    background-color: rgba(16, 185, 129, 0.12);
    border: 1px solid rgba(16, 185, 129, 0.4);
    color: #34d399;
    padding: 0.5rem 1.2rem;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    box-shadow: 0 4px 12px rgba(16, 185, 129, 0.05);
  }

  .badge-icon {
    animation: rotateSlow 8s linear infinite;
  }

  @keyframes rotateSlow {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  h1 {
    font-size: clamp(2.3rem, 6vw, 4rem);
    font-weight: 800;
    line-height: 1.15;
    margin-bottom: 1.75rem;
    letter-spacing: -1.5px;
    color: #ffffff;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
  }

  p {
    font-size: clamp(1.05rem, 2vw, 1.3rem);
    line-height: 1.75;
    color: #e5e7eb;
    margin-bottom: 3rem;
    max-width: 720px;
    margin-left: auto;
    margin-right: auto;
  }

  .hero-buttons {
    display: flex;
    gap: 1.25rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn-primary, .btn-secondary {
    display: inline-flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.95rem 2.25rem;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 700;
    font-size: 0.95rem;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .btn-primary {
    background-color: #10b981;
    color: #ffffff;
    box-shadow: 0 4px 20px rgba(16, 185, 129, 0.35);
  }

  .btn-primary:hover {
    background-color: #059669;
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(16, 185, 129, 0.45);
  }

  .btn-secondary {
    background-color: rgba(255, 255, 255, 0.03);
    color: #ffffff;
    border: 2px solid rgba(255, 255, 255, 0.25);
    backdrop-filter: blur(4px);
  }

  .btn-secondary:hover {
    background-color: rgba(255, 255, 255, 0.1);
    border-color: #ffffff;
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(255, 255, 255, 0.08);
  }

  .btn-icon {
    transition: transform 0.3s ease;
  }

  .btn-primary:hover .btn-icon {
    transform: translateX(4px);
  }

  .btn-secondary:hover .btn-icon {
    transform: scale(1.15);
  }

  /* Adaptabilidad para pantallas extremadamente pequeñas */
  @media (max-width: 480px) {
    .hero-buttons {
      flex-direction: column;
      width: 100%;
      padding: 0 1rem;
    }
    
    .btn-primary, .btn-secondary {
      width: 100%;
      justify-content: center;
    }
  }
</style>