<template>
  <div class="style-guide-container">
    <h1>Guía de Estilos</h1>

    <div class="style-guide-section">
      <h2>Colores</h2>
      <div class="style-guide-colors">
        <div class="style-guide-color-box" style="background: var(--color-bg)">
          <span>BG</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#0d0b14</span>
        </div>
        <div class="style-guide-color-box" style="background: var(--color-surface)">
          <span>Surface</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#161324</span>
        </div>
        <div class="style-guide-color-box" style="background: var(--color-primary)">
          <span>Primary</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#8e70ff</span>
        </div>
        <div class="style-guide-color-box" style="background: var(--color-primary-hover)">
          <span>Hover</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#aa94ff</span>
        </div>
        <div class="style-guide-color-box" style="background: var(--color-error)">
          <span>Error</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#ed5e6a</span>
        </div>
        <div class="style-guide-color-box" style="background: var(--color-success)">
          <span>Success</span>
          <span style="font-size: 0.75rem; opacity: 0.8;">#17cc73</span>
        </div>
      </div>
    </div>

    <div class="style-guide-section">
      <h2>Tipografía</h2>
      <div class="style-guide-card">
        <h1 style="margin-bottom: 1rem;">Título H1</h1>
        <h2 style="margin-bottom: 1rem; border: none; padding: 0; margin-top: 0; color: inherit;">Título H2</h2>
        <p style="margin-bottom: 0.5rem;">Texto normal de ejemplo.</p>
        <p style="color: var(--color-text-muted);">Texto secundario / muted.</p>
      </div>
    </div>

    <div class="style-guide-section">
      <h2>Botones</h2>
      <div class="style-guide-card style-guide-buttons">
        <button class="btn btn-primary">Primario</button>
        <button class="btn btn-success style-guide-buttons btn-success">Éxito</button>
        <button class="btn btn-error style-guide-buttons btn-error">Error</button>
      </div>
    </div>

    <div class="style-guide-section">
      <h2>Inputs</h2>
      <div class="style-guide-card">
        <input class="style-guide-input" placeholder="Escribe algo..." />
      </div>
    </div>
  </div>
</template>
