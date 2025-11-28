<template>
  <div class="layout">
    <header>
      <nav class="container">
        <div class="logo">
          <img src="~/assets/images/BOM.png" alt="BOM Studios" />
        </div>
        <ul>
          <li><a href="#why-video">Why Video</a></li>
          <li><a href="#quality">Quality</a></li>
          <li><a href="#how-it-works">How It Works</a></li>
          <li><a href="#pricing">Pricing</a></li>
          <li><a href="#faq">FAQ</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <slot />
    </main>

    <footer>
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h4>BOM Studios</h4>
            <p>AI-accelerated. Human-crafted video ads.</p>
          </div>
          <div class="footer-section">
            <h4>Product</h4>
            <ul>
              <li><a href="#why-video">Why Video</a></li>
              <li><a href="#how-it-works">How It Works</a></li>
              <li><a href="#pricing">Pricing</a></li>
            </ul>
          </div>
          <div class="footer-section">
            <h4>Legal</h4>
            <ul>
              <li><a href="#terms">Terms & Conditions</a></li>
              <li><a href="#refunds">Refund Policy</a></li>
              <li><a href="#privacy">Privacy Policy</a></li>
            </ul>
          </div>
        </div>
        <div class="footer-bottom">
          <p>&copy; 2024 BOM Studios. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
header {
  background-color: var(--color-deep-navy);
  border-bottom: 1px solid rgba(125, 209, 231, 0.1);
  padding: var(--space-md) var(--space-lg);
  position: sticky;
  top: 0;
  z-index: 100;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  height: 48px;
  width: auto;
}

.logo img {
  height: 100%;
  width: auto;
}

nav ul {
  display: flex;
  list-style: none;
  gap: var(--space-lg);
}

nav a {
  color: var(--color-white);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  font-size: 0.95rem;
}

nav a:hover {
  color: var(--color-aqua-beam);
}

main {
  min-height: calc(100vh - 200px);
}

footer {
  background-color: rgba(15, 22, 56, 0.8);
  border-top: 1px solid rgba(125, 209, 231, 0.1);
  padding: var(--space-2xl) var(--space-lg);
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);
  margin-bottom: var(--space-2xl);
}

.footer-section h4 {
  color: var(--color-aqua-beam);
  margin-bottom: var(--space-md);
  font-size: 1rem;
}

.footer-section p {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.95rem;
}

.footer-section ul {
  list-style: none;
}

.footer-section li {
  margin-bottom: var(--space-sm);
}

.footer-section a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.3s ease;
}

.footer-section a:hover {
  color: var(--color-aqua-beam);
}

.footer-bottom {
  text-align: center;
  padding-top: var(--space-lg);
  border-top: 1px solid rgba(125, 209, 231, 0.1);
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  nav {
    flex-direction: column;
    gap: var(--space-md);
  }

  nav ul {
    flex-direction: column;
    gap: var(--space-sm);
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: var(--space-md);
  }
}
</style>
