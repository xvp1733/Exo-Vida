<script>
  // Estado reactivo del formulario
  let nombre = '';
  let email = '';
  let areaInteres = '';
  let mensaje = '';
  let enviado = false;
  let cargando = false;

  const areas = [
    { id: 'logistica', etiqueta: 'Optimización y Logística de Despacho' },
    { id: 'terreno', etiqueta: 'Acción y Despliegue en el Terreno' },
    { id: 'tecnologia', etiqueta: 'Sistemas, Datos y Soporte Digital' },
    { id: 'multi-nicho', etiqueta: 'Coordinación Inter-comunitaria' }
  ];

  async function handleSubmit(event) {
    event.preventDefault();
    if (!nombre || !email || !areaInteres) return;
    
    cargando = true;
    
    // Simulación de envío a tu API/PostgreSQL en el futuro (1.5s de delay para UX)
    await new Promise(resolve => setTimeout(resolve, 1500));
    
    cargando = false;
    enviado = true;
    
    // Resetear formulario
    nombre = '';
    email = '';
    areaInteres = '';
    mensaje = '';
  }
</script>

<section id="voluntariado" class="voluntariado-section">
  <div class="container">
    <!-- Bloque de Texto e Invitación de Valor -->
    <div class="info-side">
      <span class="section-tag">Únete a la Estructura</span>
      <h2>Invierte tu tiempo en un impacto real</h2>
      <p>
        No buscamos asistencialismo pasivo. En Exo Vida necesitamos mentes y manos dispuestas a optimizar procesos, gestionar flujos de solicitudes y acelerar los tiempos de respuesta en las comunidades de Charallave. 
      </p>
      
      <div class="benefit-list">
        <div class="benefit-item">
          <div class="benefit-icon">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="20 6 9 17 4 12"/></svg>
          </div>
          <div>
            <h4>Metodología Corporativa</h4>
            <p>Aprende y aplica la disciplina logística y de mejora continua respaldada por Exo Holdings.</p>
          </div>
        </div>

        <div class="benefit-item">
          <div class="benefit-icon">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="20 6 9 17 4 12"/></svg>
          </div>
          <div>
            <h4>Acción Multi-nicho</h4>
            <p>Participa en proyectos modulares que abarcan desde salud preventiva hasta infraestructura social.</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Formulario de Conversión Profesional -->
    <div class="form-side">
      <div class="form-card">
        {#if enviado}
          <div class="success-state">
            <div class="success-icon">
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>
            </div>
            <h3>Solicitud de Ingreso Recibida</h3>
            <p>Hemos registrado tus datos en nuestra base de operaciones. Un coordinador logístico se pondrá en contacto contigo para evaluar tu perfil.</p>
            <button class="btn-reset" on:click={() => enviado = false}>Enviar otra solicitud</button>
          </div>
        {:else}
          <form on:submit={handleSubmit}>
            <div class="form-group">
              <label for="name">Nombre Completo</label>
              <input 
                type="text" 
                id="name" 
                placeholder="Ej. Yorber Sanchez" 
                bind:value={nombre} 
                required 
                disabled={cargando}
              />
            </div>

            <div class="form-group">
              <label for="email">Correo Electrónico Corporativo o Personal</label>
              <input 
                type="email" 
                id="email" 
                placeholder="ejemplo@exoholdings.com" 
                bind:value={email} 
                required 
                disabled={cargando}
              />
            </div>

            <div class="form-group">
              <label for="area">Frente de Acción de Mayor Interés</label>
              <select id="area" bind:value={areaInteres} required disabled={cargando}>
                <option value="" disabled selected>Selecciona un área de optimización</option>
                {#each areas as area}
                  <option value={area.id}>{area.etiqueta}</option>
                {/each}
              </select>
            </div>

            <div class="form-group">
              <label for="message">Mensaje u Observaciones Breves (Opcional)</label>
              <textarea 
                id="message" 
                rows="3" 
                placeholder="Cuéntanos brevemente cómo te gustaría aportar valor..." 
                bind:value={mensaje}
                disabled={cargando}
              ></textarea>
            </div>

            <button type="submit" class="btn-submit" disabled={cargando}>
              {#if cargando}
                <span class="spinner"></span>
                <span>Procesando...</span>
              {:else}
                <span>Postular como Voluntario</span>
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
              {/if}
            </button>
          </form>
        {/if}
      </div>
    </div>
  </div>
</section>

<style>
  .voluntariado-section {
    padding: 6.5rem 10%;
    background-color: #ffffff;
    border-bottom: 1px solid #e2e8f0;
  }

  .container {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: 6rem;
    max-width: 1280px;
    margin: 0 auto;
    align-items: center;
  }

  .info-side {
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
    margin-bottom: 3rem;
  }

  /* Lista de Beneficios */
  .benefit-list {
    display: flex;
    flex-direction: column;
    gap: 1.75rem;
  }

  .benefit-item {
    display: flex;
    gap: 1.25rem;
    align-items: flex-start;
  }

  .benefit-icon {
    background-color: #f0fdf4;
    color: #10b981;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    border: 1px solid rgba(16, 185, 129, 0.15);
  }

  .benefit-item h4 {
    font-size: 1.1rem;
    color: #1f2937;
    font-weight: 700;
    margin: 0 0 0.25rem 0;
  }

  .benefit-item p {
    color: #64748b;
    font-size: 0.95rem;
    line-height: 1.5;
    margin: 0;
  }

  /* Tarjeta del Formulario */
  .form-card {
    background-color: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 24px;
    padding: 3rem 2.5rem;
    box-shadow: 0 10px 30px rgba(15, 23, 42, 0.015);
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
    text-align: left;
  }

  label {
    font-size: 0.88rem;
    font-weight: 700;
    color: #334155;
  }

  input, select, textarea {
    width: 100%;
    padding: 0.85rem 1.2rem;
    border-radius: 12px;
    border: 1px solid #cbd5e1;
    background-color: #ffffff;
    color: #1f2937;
    font-size: 0.95rem;
    font-family: inherit;
    transition: all 0.2s ease;
    box-sizing: border-box;
  }

  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #10b981;
    box-shadow: 0 0 0 4px rgba(16, 185, 129, 0.1);
  }

  input::placeholder, textarea::placeholder {
    color: #94a3b8;
  }

  /* Botones e Interacciones */
  .btn-submit {
    width: 100%;
    background-color: #10b981;
    color: #ffffff;
    border: none;
    padding: 1rem;
    border-radius: 12px;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 0.75rem;
    transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 4px 14px rgba(16, 185, 129, 0.3);
  }

  .btn-submit:hover:not(:disabled) {
    background-color: #059669;
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(16, 185, 129, 0.4);
  }

  .btn-submit:disabled {
    background-color: #94a3b8;
    box-shadow: none;
    cursor: not-allowed;
    opacity: 0.7;
  }

  /* Estado Exitoso */
  .success-state {
    text-align: center;
    padding: 2rem 1rem;
  }

  .success-icon {
    color: #10b981;
    background-color: #dffde9;
    width: 64px;
    height: 64px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 1.5rem auto;
  }

  .success-state h3 {
    font-size: 1.4rem;
    color: #1f2937;
    font-weight: 800;
    margin-bottom: 0.75rem;
  }

  .success-state p {
    color: #4b5563;
    font-size: 0.98rem;
    line-height: 1.6;
    margin-bottom: 2rem;
  }

  .btn-reset {
    background: none;
    border: 1px solid #cbd5e1;
    padding: 0.6rem 1.5rem;
    border-radius: 50px;
    font-size: 0.88rem;
    font-weight: 650;
    color: #64748b;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .btn-reset:hover {
    color: #1f2937;
    border-color: #64748b;
  }

  /* Spinner de carga */
  .spinner {
    width: 18px;
    height: 18px;
    border: 2.5px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    border-top-color: #ffffff;
    animation: spin 0.8s linear infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  /* Responsivo */
  @media (max-width: 1024px) {
    .container {
      grid-template-columns: 1fr;
      gap: 4rem;
    }
    
    .voluntariado-section {
      padding: 5rem 6%;
    }

    .form-card {
      padding: 2.5rem 1.75rem;
    }
  }
</style>