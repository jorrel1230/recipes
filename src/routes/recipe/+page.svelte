<script>
  import Checklist from '../../lib/components/Checklist.svelte'
  import ImageWrapper from '../../lib/components/ImageWrapper.svelte'
  import Timer from '../../lib/components/Timer.svelte'

  const ingredients = [
    { id: 'produce', label: '[Quantity] [main vegetable]' },
    { id: 'oil', label: '[Quantity] olive oil' },
    { id: 'seasoning', label: '[Quantity] [seasoning blend]' },
    { id: 'garnish', label: '[Optional garnish]' }
  ]
</script>

<svelte:head>
  <title>Sample Recipe — Roasted Vegetable Bowl</title>
  <meta name="description" content="A sample recipe with a checkable ingredient list and a cooking timer.">
</svelte:head>

<main>
  <p class="kicker">Sample recipe</p>
  <h1>Roasted Vegetable Bowl</h1>
  <p class="lead">[Add a short description of the dish and what to serve it with.]</p>
  <p class="details">Serves [number] · Prep [minutes] · Cook [minutes]</p>

  <figure>
    <ImageWrapper src="/landscape.svg" alt="" height="clamp(180px, 45vw, 320px)" />
    <figcaption>[Replace this illustration with a photo of the finished dish.]</figcaption>
  </figure>

  <section aria-labelledby="ingredients-heading">
    <h2 id="ingredients-heading">Ingredients</h2>
    <Checklist items={ingredients} storageKey="recipe-vegetable-bowl-ingredients" label="Check off each ingredient" />
  </section>

  <section aria-labelledby="method-heading">
    <h2 id="method-heading">Method</h2>
    <ol>
      <li>Preheat the oven to [temperature]. Chop the vegetables into [size] pieces.</li>
      <li>
        Toss the vegetables with oil and seasoning, then roast for [minutes].
        <div class="step-timer">
          <Timer duration={900} storageKey="recipe-vegetable-bowl-roast" label="Roasting timer (example)" />
        </div>
      </li>
      <li>Divide among bowls and finish with [garnish].</li>
    </ol>
  </section>
</main>

<style>
  .details, figcaption { color: #696961; font-size: 14px; }
  figure { margin: 32px 0; }
  figcaption { margin-top: 8px; }
  section + section { margin-top: 32px; }
  h2 { margin: 0 0 12px; font-weight: 600; }
  ol { margin: 0; padding-left: 1.5rem; line-height: 1.7; }
  li + li { margin-top: 12px; }
  .step-timer { margin-top: 8px; }
</style>
