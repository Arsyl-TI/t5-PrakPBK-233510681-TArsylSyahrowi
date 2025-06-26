<template>
  <div class="container">
    <h2>📋 About TodoList App</h2>
    
    <div class="about-card">
      <div class="about-content">
        <p class="about-text">✨ Yuk tetap semangat belajar Vue nyaa! ✨</p>
        
        <div class="features">
          <div class="feature-item">
            <span class="feature-icon">✅</span>
            <span>Antarmuka yang sederhana dan intuitif</span>
          </div>
          <div class="feature-item">
            <span class="feature-icon">🔄</span>
            <span>Real-time updates</span>
          </div>
          <div class="feature-item">
            <span class="feature-icon">📱</span>
            <span>Desain Responsive</span>
          </div>
          <div class="feature-item">
            <span class="feature-icon">⚡</span>
            <span>Performa cepat</span>
          </div>
        </div>
        
        <div class="motivation">
          <h3>💡 Motivation</h3>
          <p>Aplikasi ini dibuat untuk membantu Anda mengatur tugas-tugas Anda saat mempelajari Vue.js dan Pinia. Terus pantau kemajuan Anda!</p>
        </div>
        
        <div class="tech-stack">
          <h3>🛠️ Tech Stack</h3>
          <div class="tech-items">
            <span class="tech-item">Vue 3</span>
            <span class="tech-item">Pinia</span>
            <span class="tech-item">Composition API</span>
            <span class="tech-item">Vite</span>
          </div>
        </div>
      </div>
    </div>
    
    <div class="quote">
      <p>"Produktivitas tidak pernah terjadi secara kebetulan. Produktivitas selalu merupakan hasil dari komitmen terhadap keunggulan, perencanaan yang cerdas, dan upaya yang terfokus."</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 650px;
  margin: 30px auto;
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
  padding: 30px 35px;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
}

h2 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 25px;
  font-weight: 700;
  font-size: 2rem;
  letter-spacing: 0.5px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.about-card {
  background: white;
  border-radius: 12px;
  padding: 25px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  margin-bottom: 25px;
}

.about-text {
  font-size: 1.2rem;
  text-align: center;
  color: #34495e;
  margin-bottom: 30px;
  font-weight: 500;
}

.features {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 30px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 1.05rem;
  color: #2c3e50;
  padding: 10px 15px;
  background: #f8f9fa;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.feature-item:hover {
  background: #e8f4fd;
  transform: translateX(5px);
}

.feature-icon {
  font-size: 1.3rem;
}

.motivation, .tech-stack {
  margin-bottom: 25px;
}

h3 {
  color: #2c3e50;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.3rem;
}

.tech-items {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.tech-item {
  background: #e0e7ff;
  color: #4f46e5;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
}

.quote {
  font-style: italic;
  text-align: center;
  color: #7f8c8d;
  padding: 20px;
  border-top: 1px dashed #ddd;
  margin-top: 20px;
}

.quote p {
  font-size: 1.1rem;
}

@media (max-width: 600px) {
  .container {
    padding: 20px;
    margin: 15px;
  }
  
  .about-card {
    padding: 15px;
  }
  
  h2 {
    font-size: 1.6rem;
  }
}
</style>