<script>
  import { page } from '$app/state'
  import '../app.css'
  let { children } = $props()
  const recipePath = '/garlic-soy-chicken-thigh-stir-fry/'
  const mapoTofuPath = '/mapo-tofu/'
</script>

<div class="page">
  <header>
    <span class="brand">Jorrel and Keith's Recipes</span>
    <nav aria-label="Main navigation">
      <a class="nav" href="/" aria-current={page.url.pathname === '/' ? 'page' : undefined}>Home</a>
      <a class="nav" href={recipePath} aria-current={page.url.pathname === recipePath ? 'page' : undefined}>Garlic Soy Chicken Thigh Stir-Fry</a>
      <a class="nav" href={mapoTofuPath} aria-current={page.url.pathname === mapoTofuPath ? 'page' : undefined}>Mapo Tofu</a>
      <a class="nav" href="/about/" aria-current={page.url.pathname.replace(/\/$/, '') === '/about' ? 'page' : undefined}>About</a>
    </nav>
  </header>

  {@render children()}

  <footer>© 2026 Jorrel Rajan</footer>
</div>
