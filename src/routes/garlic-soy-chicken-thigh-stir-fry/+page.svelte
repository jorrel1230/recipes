<script>
  import Checklist from '../../lib/components/Checklist.svelte'
  import ImageWrapper from '../../lib/components/ImageWrapper.svelte'
  import List from '../../lib/components/List.svelte'
  import Timer from '../../lib/components/Timer.svelte'

  const ingredientGroups = [
    {
      id: 'marinade',
      label: 'Chicken & marinade',
      items: [
        { id: 'chicken', label: '1 lb (~1 costco packet) boneless, skinless chicken thighs' },
        { id: 'soy', label: '1 tbsp soy sauce' },
        { id: 'cornstarch', label: '1 tsp cornstarch' },
        { id: 'pepper', label: '½ tsp black or white pepper' },
        { id: 'oil', label: '1 tsp neutral oil' }
      ]
    },
    {
      id: 'sauce',
      label: 'Garlic-soy sauce',
      items: [
        { id: 'soy', label: '1½ tbsp soy sauce' },
        { id: 'oyster', label: '1 tbsp oyster sauce' },
        { id: 'sugar', label: '1 tsp packed brown sugar' },
        { id: 'water', label: '2 tbsp water' },
        { id: 'vinegar', label: '1 tsp rice vinegar (optional)' }
      ]
    },
    {
      id: 'stir-fry',
      label: 'Aromatics & stir-fry',
      items: [
        { id: 'garlic', label: '6 cloves garlic, minced' },
        { id: 'oil', label: '1 tbsp neutral oil' },
        { id: 'chili', label: '1–2 tsp chili flakes, to taste' }
      ]
    }
  ]

  const steps = [
    {
      id: 'marinate',
      title: 'Marinate the chicken.',
      description: 'Wash chicken, then dry. Toss with the marinade ingredients and let sit for 10–15 minutes. No need to cut or trim.'
    },
    {
      id: 'mix',
      title: 'Mix the sauce.',
      description: 'While the chicken marinates, stir the soy sauce, oyster sauce, brown sugar, water, and optional rice vinegar in a small bowl until the sugar dissolves.'
    },
    {
      id: 'sear',
      title: 'Sear the chicken (5–7 minutes).',
      description: 'Heat 1 tbsp neutral oil in the wok over medium-high heat. Add the chicken in a single layer and leave it undisturbed for 2 minutes. Flip and cook another 2 minutes. Chop up in the wok and cook until browned and nearly cooked through. Work in batches if needed to avoid crowding the wok.',
      timer: { duration: 120, label: 'Initial sear' }
    },
    {
      id: 'aromatics',
      title: 'Fry the aromatics (20–30 seconds).',
      description: 'Reduce the heat to medium-low or medium and push the chicken to the sides. Stir-fry the garlic, scallion whites, and chili flakes in the center just until fragrant. Don’t let the garlic or chili burn. Toss with the chicken.',
      timer: { duration: 30, label: 'Aromatics' }
    },
    {
      id: 'glaze',
      title: 'Glaze the chicken (1–2 minutes).',
      description: 'Pour in the sauce and raise the heat slightly to bring it to a simmer. Toss until the glaze coats the chicken. Just keep going until the glaze looks like it\'s gone.'
    },
    {
      id: 'serve',
      title: 'Finish and serve.',
      description: 'Turn off the heat and serve with steamed rice.'
    }
  ]
</script>

<svelte:head>
  <title>Garlic Soy Chicken Thigh Stir-Fry</title>
  <meta name="description" content="A quick wok stir-fry with browned chicken thighs, six cloves of garlic, chili flakes, and a savory brown sugar–soy glaze.">
</svelte:head>

<main>
  <p class="kicker">Wok recipe</p>
  <h1>Garlic Soy Chicken Thigh Stir-Fry</h1>
  <p class="lead">Serve with Rice, optionally top with Lime</p>
  <p class="details">About 25 minutes · Serves 2–3 · Wok</p>

  <figure>
    <ImageWrapper src="/garlic-soy-chicken.webp" alt="Garlic soy chicken thighs served with steamed rice and lime wedges" height="auto" />
  </figure>

  <section aria-labelledby="ingredients-heading">
    <h2 id="ingredients-heading">Ingredients</h2>
    <div class="ingredient-groups">
      {#each ingredientGroups as group (group.id)}
        <Checklist items={group.items} storageKey={`recipe-garlic-soy-chicken-${group.id}`} label={group.label} />
      {/each}
    </div>
  </section>

  <section aria-labelledby="method-heading">
    <h2 id="method-heading">Method</h2>
    <List items={steps} ordered>
      {#snippet renderItem(step)}
        <strong>{step.title}</strong> {step.description}
        {#if step.timer}
          <div class="step-timer">
            <Timer {...step.timer} storageKey={`recipe-garlic-soy-chicken-${step.id}`} />
          </div>
        {/if}
      {/snippet}
    </List>
  </section>
</main>

<style>
  .details { color: #696961; font-size: 14px; }
  figure { max-width: 360px; margin: 32px 0; }
  section + section { margin-top: 32px; }
  h2 { margin: 0 0 12px; font-weight: 600; }
  .ingredient-groups { display: grid; gap: 12px; }
  .step-timer { margin-top: 8px; }
</style>
