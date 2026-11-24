<script>
  import Checklist from '../../lib/components/Checklist.svelte'
  import ImageWrapper from '../../lib/components/ImageWrapper.svelte'
  import List from '../../lib/components/List.svelte'
  import Timer from '../../lib/components/Timer.svelte'

  const ingredients = [
    { id: 'beef', label: '0.9 lb (408 g) ground beef' },
    { id: 'tofu', label: '1½–2 lb soft or silken tofu, cut into 1-inch cubes' },
    { id: 'oil', label: '2 tbsp neutral oil, divided' },
    { id: 'chili', label: '1–2 tsp Sichuan chili flakes' },
    { id: 'garlic', label: '3 tbsp minced garlic (about 9 medium cloves)' },
    { id: 'peppercorns', label: '1–2 tsp whole Sichuan peppercorns, toasted and finely ground' },
    { id: 'paste', label: '2 tbsp broad bean paste with chili oil (doubanjiang)' },
    { id: 'broth', label: '¾–1 cup water or low-sodium chicken broth' },
    { id: 'cornstarch', label: '2 tsp cornstarch' },
    { id: 'slurry-water', label: '2 tbsp cold water, for the slurry' },
    { id: 'scallions', label: '2 scallions, chopped' },
    { id: 'sugar', label: '¼ tsp sugar (optional)' },
    { id: 'sesame-oil', label: '¼ tsp sesame oil (optional)' }
  ]

  const steps = [
    {
      id: 'chili-oil',
      title: 'Make the chili oil.',
      text: 'Warm 1 tbsp neutral oil over low heat. Stir in the chili flakes for 20–30 seconds, just until fragrant. Transfer the oil and flakes to a small bowl.'
    },
    {
      id: 'garlic',
      title: 'Fry the garlic.',
      text: 'Heat the remaining 1 tbsp neutral oil in the wok over medium-low heat. Stir in the garlic and cook for 30–60 seconds, until fragrant but not browned.'
    },
    {
      id: 'beef',
      title: 'Brown the beef.',
      text: 'Raise the heat to medium-high. Add the ground beef and break it into small crumbles. Cook until browned and fully cooked (160°F / 71°C).'
    },
    {
      id: 'peppercorns',
      title: 'Add the Sichuan peppercorns.',
      text: 'Stir in the ground peppercorns, reserving a pinch for serving. Cook for 15–30 seconds.'
    },
    {
      id: 'paste',
      title: 'Fry the bean paste.',
      text: 'Stir in 2 tbsp broad bean paste with chili oil and fry for about 1 minute.'
    },
    {
      id: 'broth',
      title: 'Build the sauce.',
      text: 'Pour in ¾ cup broth or water and stir to loosen the browned bits. Simmer gently for 1–2 minutes, keeping the remaining liquid on hand to thin the sauce.'
    },
    {
      id: 'slurry',
      title: 'Thicken the sauce.',
      text: 'Stir the cornstarch slurry again, then pour it in a little at a time, stirring until the sauce lightly thickens. You may not need all of it.'
    },
    {
      id: 'return-oil',
      title: 'Add the chili oil.',
      text: 'Stir in the reserved chili oil, including the flakes.'
    },
    {
      id: 'tofu',
      title: 'Simmer the tofu.',
      text: 'Gently fold in the tofu and simmer for 3–5 minutes. Spoon the sauce over the cubes rather than stirring vigorously. Add a splash of the reserved liquid if the sauce gets too thick.',
      timer: { duration: 180, label: 'Tofu simmer (check at 3 minutes)' }
    },
    {
      id: 'finish',
      title: 'Finish and serve.',
      text: 'Turn off the heat. Add the scallions, reserved Sichuan pepper, and optional sugar and sesame oil. Taste before adding more bean paste; it’s already salty. Serve hot over steamed rice.'
    }
  ]
</script>

<svelte:head>
  <title>Mapo Tofu</title>
  <meta name="description" content="Mapo tofu with ground beef, soft tofu, homemade chili oil, and toasted Sichuan peppercorns.">
</svelte:head>

<main>
  <p class="kicker">Wok recipe</p>
  <h1>Mapo Tofu</h1>
  <p class="lead">Soft tofu and ground beef in a glossy, spicy bean sauce with homemade chili oil and the tingle of toasted Sichuan peppercorns.</p>
  <p class="details">30–35 minutes · Serves 4–6 · Wok</p>

  <figure>
    <ImageWrapper src="/mapo-tofu.webp" alt="Mapo tofu with ground beef and chili sauce in a wok" height="auto" />
  </figure>

  <section aria-labelledby="ingredients-heading">
    <h2 id="ingredients-heading">Ingredients</h2>
    <Checklist items={ingredients} storageKey="recipe-mapo-tofu-ingredients" label="Check off ingredients" />
  </section>

  <section aria-labelledby="prep-heading">
    <h2 id="prep-heading">Prep</h2>
    <p>Toast the Sichuan peppercorns in a dry pan over medium-low heat for 1–2 minutes, until fragrant, then grind them finely. Cube the tofu, mince the garlic, and chop the scallions. Mix the cornstarch with 2 tbsp cold water in a small bowl.</p>
  </section>

  <section aria-labelledby="method-heading">
    <h2 id="method-heading">Method</h2>
    <List items={steps} ordered>
      {#snippet renderItem(step)}
        <strong>{step.title}</strong> {step.text}
        {#if step.timer}
          <div class="step-timer">
            <Timer {...step.timer} storageKey={`recipe-mapo-tofu-${step.id}`} />
          </div>
        {/if}
      {/snippet}
    </List>
  </section>

  <p class="details attribution">Adapted from <a href="https://thewoksoflife.com/ma-po-tofu-real-deal/">The Woks of Life’s Mapo Tofu recipe</a>.</p>
</main>

<style>
  .details { color: #696961; font-size: 14px; }
  figure { max-width: 360px; margin: 32px 0; }
  .step-timer { margin-top: 8px; }
  section + section, .attribution { margin-top: 32px; }
  h2 { margin: 0 0 12px; font-weight: 600; }
  section p { margin: 0; line-height: 1.7; }
  .attribution a { color: inherit; }
</style>
