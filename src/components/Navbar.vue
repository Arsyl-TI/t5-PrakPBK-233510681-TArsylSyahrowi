<template>
  <nav class="navbar">
    <div class="nav-links">
      <router-link to="/" class="link">
        <span class="icon">🏠</span>
        <span class="text">Home</span>
      </router-link>
      <router-link to="/about" class="link">
        <span class="icon">ℹ️</span>
        <span class="text">About</span>
      </router-link>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background-color: #2c3e50;
  min-height: 100vh;
  width: 250px;
  position: fixed;
  left: 0;
  top: 0;
  padding: 20px 0;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.nav-links {
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding: 0 15px;
}

.link {
  color: #ecf0f1;
  text-decoration: none;
  font-weight: 500;
  padding: 12px 15px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all 0.3s ease;
}

.link:hover {
  background-color: #34495e;
  transform: translateX(5px);
}

.link.router-link-exact-active {
  background-color: #3498db;
  color: white;
}

.icon {
  font-size: 1.2em;
}

.text {
  font-size: 1.1em;
}

@media (max-width: 768px) {
  .navbar {
    width: 70px;
    padding: 20px 0;
  }
  
  .text {
    display: none;
  }
  
  .link {
    justify-content: center;
    padding: 12px 0;
  }
  
  .icon {
    font-size: 1.5em;
  }
}
</style>