<template>
  <div class="layout">
    <header>
      <div class="container">
        <nav>
          <div class="logo">
            <img src="~/assets/images/BOM.png" alt="BOM Studios" />
          </div>
          <ul class="nav-links">
            <li><a href="#why-video">Why Video</a></li>
            <li><a href="#quality">Quality</a></li>
            <li><a href="#how-it-works">How It Works</a></li>
            <li><a href="#pricing">Pricing</a></li>
            <li><a href="#faq">FAQ</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <main>
      <slot />
    </main>

    <footer>
      <div class="container">
        <div class="footer-grid">
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
        <div class="pixel-divider"></div>
        <div class="footer-bottom">
          <p>&copy; 2024 BOM Studios. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}

/* Nav Links */
.nav-links {
  display: flex;
  list-style: none;
  gap: var(--space-4);
}

@media (max-width: 768px) {
  nav {
    flex-direction: column;
    gap: var(--space-2);
  }

  .nav-links {
    display: none;
  }
}
</style>
