<script>
    import { base } from '$app/paths';

    let menuAbierto = false;
    let submenuActivo = '';

    function toggleMenu() {
        menuAbierto = !menuAbierto;
        if (!menuAbierto) submenuActivo = '';
    }

    function toggleSubmenu(nombre) {
        submenuActivo = submenuActivo === nombre ? '' : nombre;
    }

    // Función auxiliar para forzar el scroll suave en SPA cuando se navega en la misma página
    function handleAnchorClick(event) {
        const link = event.currentTarget;
        const anchor = link.getAttribute('href').split('#')[1];
        const targetElement = document.getElementById(anchor);
        
        if (targetElement) {
            event.preventDefault();
            targetElement.scrollIntoView({ behavior: 'smooth' });
            if (menuAbierto) toggleMenu();
        }
    }
</script>

<header class="navbar">
    <!-- Logotipo de Exo Vida y Exo Holdings -->
    <a href="{base}/" class="logo" on:click={handleAnchorClick}>
        <div class="logo-text">
            <span class="holding">Exo</span><span class="ong">Vida</span>
        </div>
        <span class="holding-sub">Iniciativa de Exo Holdings</span>
    </a>

    <!-- Navegación para Computadoras (Desktop) -->
    <nav class="nav-desktop">
        <a href="{base}/#inicio" class="nav-link" on:click={handleAnchorClick}>Inicio</a>
        
        <!-- Nosotros con Dropdown -->
        <div class="dropdown">
            <button class="dropdown-btn" aria-haspopup="true">
                Nosotros 
                <svg class="arrow" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
            </button>
            <div class="dropdown-content">
                <a href="{base}/#nosotros" on:click={handleAnchorClick}>Quiénes Somos</a>
                <a href="{base}/#transparencia" on:click={handleAnchorClick}>Transparencia y Cuentas</a>
                <a href="{base}/#equipo" on:click={handleAnchorClick}>Nuestro Equipo</a>
            </div>
        </div>

        <!-- Frentes con Dropdown -->
        <div class="dropdown">
            <button class="dropdown-btn" aria-haspopup="true">
                Frentes de Acción 
                <svg class="arrow" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
            </button>
            <div class="dropdown-content">
                <a href="{base}/#proyectos-sociales" on:click={handleAnchorClick}>Desarrollo Comunitario</a>
                <a href="{base}/#frentes" on:click={handleAnchorClick}>Procesos de Ayuda</a>
                <a href="{base}/#alianzas" on:click={handleAnchorClick}>Alianzas con Nichos</a>
            </div>
        </div>

        <!-- Cómo colaborar -->
        <div class="dropdown">
            <button class="dropdown-btn" aria-haspopup="true">
                Involúcrate 
                <svg class="arrow" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
            </button>
            <div class="dropdown-content">
                <a href="{base}/#voluntariado" on:click={handleAnchorClick}>Ser Voluntario</a>
                <a href="{base}/#donaciones" on:click={handleAnchorClick}>Donar Insumos/Fondos</a>
                <a href="{base}/#empresas" on:click={handleAnchorClick}>Sponsor Corporativo</a>
            </div>
        </div>

        <a href="{base}/#blog" class="nav-link" on:click={handleAnchorClick}>Noticias</a>
        <a href="{base}/#contacto" class="btn-cta" on:click={handleAnchorClick}>Unirse Ahora</a>
    </nav>

    <!-- Menú de navegación para celulares (Botón Hamburguesa con SVG) -->
    <button class="menu-toggle" on:click={toggleMenu} aria-label="Controlar menú" aria-expanded={menuAbierto}>
        {#if menuAbierto}
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6 6 18M6 6l12 12"/></svg>
        {:else}
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 12h16M4 6h16M4 18h16"/></svg>
        {/if}
    </button>
</header>

<!-- Menú móvil desplegable -->
{#if menuAbierto}
  <div class="nav-mobile">
    <a href="{base}/#inicio" on:click={handleAnchorClick}>Inicio</a>
    
    <!-- Nosotros Móvil -->
    <button class="mobile-accordion-btn" on:click={() => toggleSubmenu('nosotros')}>
        Nosotros 
        <svg class="arrow" class:rotated={submenuActivo === 'nosotros'} width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
    </button>
    {#if submenuActivo === 'nosotros'}
        <div class="mobile-submenu">
            <a href="{base}/#nosotros" on:click={handleAnchorClick}>Quiénes Somos</a>
            <a href="{base}/#transparencia" on:click={handleAnchorClick}>Transparencia y Cuentas</a>
            <a href="{base}/#equipo" on:click={handleAnchorClick}>Nuestro Equipo</a>
        </div>
    {/if}

    <!-- Frentes Móvil -->
    <button class="mobile-accordion-btn" on:click={() => toggleSubmenu('frentes')}>
        Frentes de Acción
        <svg class="arrow" class:rotated={submenuActivo === 'frentes'} width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
    </button>
    {#if submenuActivo === 'frentes'}
        <div class="mobile-submenu">
            <a href="{base}/#proyectos-sociales" on:click={handleAnchorClick}>Desarrollo Comunitario</a>
            <a href="{base}/#frentes" on:click={handleAnchorClick}>Procesos de Ayuda</a>
            <a href="{base}/#alianzas" on:click={handleAnchorClick}>Alianzas con Nichos</a>
        </div>
    {/if}

    <!-- Involúcrate Móvil -->
    <button class="mobile-accordion-btn" on:click={() => toggleSubmenu('involucrate')}>
        Involúcrate
        <svg class="arrow" class:rotated={submenuActivo === 'involucrate'} width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
    </button>
    {#if submenuActivo === 'involucrate'}
        <div class="mobile-submenu">
            <a href="{base}/#voluntariado" on:click={handleAnchorClick}>Ser Voluntario</a>
            <a href="{base}/#donaciones" on:click={handleAnchorClick}>Donar Insumos/Fondos</a>
            <a href="{base}/#empresas" on:click={handleAnchorClick}>Sponsor Corporativo</a>
        </div>
    {/if}

    <a href="{base}/#blog" on:click={handleAnchorClick}>Noticias</a>
    <a href="{base}/#contacto" class="btn-cta" on:click={handleAnchorClick}>Unirse Ahora</a>
  </div>
{/if}

<style>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.25rem 5%;
    background-color: #ffffff;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
    position: sticky;
    top: 0;
    z-index: 100;
    border-bottom: 3px solid #10b981;
  }

  .logo {
    display: flex;
    flex-direction: column;
    text-decoration: none;
    line-height: 1.1;
  }
  
  .logo-text {
    display: flex;
  }

  .logo .holding {
    font-size: 1.6rem;
    font-weight: 800;
    color: #1f2937;
    letter-spacing: -0.5px;
  }
  .logo .ong {
    font-size: 1.6rem;
    font-weight: 800;
    color: #10b981;
    letter-spacing: -0.5px;
  }
  .logo .holding-sub {
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #9ca3af;
    font-weight: 600;
    margin-top: 2px;
  }

  .nav-desktop {
    display: flex;
    align-items: center;
    gap: 1.75rem;
  }

  .nav-desktop .nav-link {
    text-decoration: none;
    color: #4b5563;
    font-weight: 600;
    font-size: 0.95rem;
    transition: color 0.3s ease;
  }

  .nav-desktop .nav-link:hover {
    color: #10b981;
  }

  .dropdown {
    position: relative;
    display: inline-block;
  }

  .dropdown-btn {
    background: none;
    border: none;
    color: #4b5563;
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
    padding: 0.5rem 0;
    display: flex;
    align-items: center;
    gap: 0.35rem;
    transition: color 0.3s;
  }

  .dropdown-btn:hover {
    color: #10b981;
  }

  .arrow {
    transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .dropdown:hover .arrow {
    transform: rotate(180deg);
  }

  .dropdown-content {
    display: none;
    position: absolute;
    background-color: #ffffff;
    min-width: 220px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
    border-radius: 8px;
    padding: 0.5rem 0;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 1px solid #f3f4f6;
  }

  .dropdown-content a {
    color: #4b5563;
    padding: 0.75rem 1.25rem;
    text-decoration: none;
    display: block;
    font-size: 0.9rem;
    font-weight: 500;
    transition: background-color 0.2s, color 0.2s;
  }

  .dropdown-content a:hover {
    background-color: #f0fdf4;
    color: #10b981;
  }

  .dropdown:hover .dropdown-content {
    display: block;
  }

  .btn-cta {
    background-color: #10b981;
    color: white !important;
    padding: 0.6rem 1.5rem;
    border-radius: 50px;
    font-weight: 700;
    font-size: 0.9rem;
    text-decoration: none;
    box-shadow: 0 4px 12px rgba(16, 185, 129, 0.2);
    transition: background-color 0.3s, transform 0.2s, box-shadow 0.2s;
  }

  .btn-cta:hover {
    background-color: #059669;
    transform: translateY(-2px);
    box-shadow: 0 6px 18px rgba(16, 185, 129, 0.3);
  }

  .menu-toggle {
    display: none;
    background: none;
    border: none;
    color: #1f2937;
    cursor: pointer;
    align-items: center;
    justify-content: center;
    padding: 0.5rem;
  }

  .nav-mobile {
    display: flex;
    flex-direction: column;
    background-color: #ffffff;
    border-top: 1px solid #f3f4f6;
    padding: 1.5rem 5%;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
  }

  .nav-mobile a, .mobile-accordion-btn {
    padding: 1rem 0;
    text-decoration: none;
    color: #4b5563;
    font-weight: 600;
    font-size: 1rem;
    border-bottom: 1px solid #f3f4f6;
    text-align: left;
    width: 100%;
    background: none;
    border-left: none;
    border-right: none;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .mobile-submenu {
    background-color: #f9fafb;
    padding-left: 1rem;
    display: flex;
    flex-direction: column;
    border-bottom: 1px solid #f3f4f6;
  }

  .mobile-submenu a {
    padding: 0.8rem 0;
    font-size: 0.9rem;
    font-weight: 500;
    border-bottom: none;
  }

  .nav-mobile .btn-cta {
    margin-top: 1.5rem;
    justify-content: center;
  }

  .arrow.rotated {
    transform: rotate(180deg);
  }

  @media (max-width: 992px) {
    .nav-desktop {
      display: none;
    }
    .menu-toggle {
      display: flex;
    }
  }
</style>