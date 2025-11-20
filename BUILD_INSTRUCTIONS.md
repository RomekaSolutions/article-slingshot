ARTICLE SLINGSHOT - IMPLEMENTATION INSTRUCTIONS FOR CLAUDE CODE

BUILD PHASES:
1. Foundation - layout, night sky, river, couples area, slingshot, header
2. Storks - professional bird design with wing flapping, bundle, sentence display
3. Timing bar - green zone, moving indicator, click detection, no lag
4. Boulders - 3 article types, selection, slingshot loading, trajectory physics
5. Crocodile - glowing eyes underwater, jaw snap, splash, dramatic timing
6. Couples - human figures (not stick), emotions (joy/sad/cry/angry), walk-away animation
7. Baskets - barely visible dark brown, float on river, sync with storks
8. Game logic - load questions, randomize, scoring, lives, levels 1-6, win/lose
9. UI polish - score popups, level up banner, game over screen, victory screen
10. Optimization - 60fps mobile, test all 204 questions, landscape enforcement

QUALITY TARGETS:
- Monument Valley / Duolingo level polish
- Storks look like birds, not triangles
- Crocodile reveal is SUDDEN and startling
- Couples have clear facial expressions
- All animations smooth, no jank
- Professional game asset quality

GRAPHICS:
- CSS/SVG only (no images)
- Stork: bird silhouette, flapping wings, bobbing flight, bundle below
- Crocodile: glowing yellow eyes, jaw with teeth, splash particles
- Couples: simple but expressive humans, hearts float up, tears fall, walk away opposite directions
- Baskets: hard to see (night mode), dark brown, bob on river
- Boulders: 3 types - A/AN, THE, ∅ with gradients and glow when selected
- Night sky: gradient with 80-100 twinkling stars
- River: wavy edge, flow animation, depth gradient

BOULDER COLORS (DO NOT USE BRAND COLORS):
- A/AN: Orange gradient (#ff8c42 to #ff6b35)
- THE: Blue gradient (#4A90E2 to #357ABD)  
- ∅: Purple gradient (#9B59B6 to #8E44AD)

BRANDING (TOP-LEFT CORNER ONLY):
- GRASP badge: Orange #F57C00, Poppins Bold, uppercase
- "by Gregor": Montserrat Regular, light gray
- Import fonts: Poppins 700, Montserrat 400
- THIS IS THE ONLY PLACE BRAND COLORS APPEAR

CRITICAL TIMING SEQUENCE:
Wrong answer + good aim = GREEN FLASH on timing bar → boulder hits → stork shakes → bundle drops → THEN crocodile eyes glow → jaw snaps
This false success creates emotional impact

QUESTION BANK:
- 204 questions provided in article-questions.json
- JSON WILL BE EMBEDDED IN HTML FILE
- Leave placeholder: 
  const QUESTIONS = /* PLACEHOLDER_JSON_HERE */;
- Format:
  {
    "id": 1,
    "sentence": "I finished ___ book you lent me.",
    "correctArticle": "the",
    "difficulty": "easy",
    "category": "countable_singular_specific",
    "explanation": "..."
  }
- correctArticle values: "a", "an", "the", "zero"
- Game treats "a" and "an" as same (both use A/AN boulder)

LIVES SYSTEM:
- 3 lives (hearts)
- Lose 1 for: wrong grammar OR bad aim
- 0 lives = game over (couples fight, walk away, fade to black)

LEVEL PROGRESSION:
Level 1: 1 couple, 5 babies to advance, timing bar 20% green, stork speed 100%
Level 2: 2 couples, 5 babies, 18% green, 110% speed
Level 3: 3 couples, 5 babies, 16% green, 120% speed
Level 4: 4 couples, 5 babies, 14% green, 130% speed
Level 5: 5 couples, 5 babies, 12% green, 140% speed
Level 6: 6 couples, 5 babies, 10% green, 150% speed (victory after completion)

MOBILE LANDSCAPE:
- Primary platform
- Force landscape, show rotate message if portrait
- Touch targets minimum 44px × 44px
- No scrolling required
- Works on iOS Safari 14+

PERFORMANCE:
- 60fps constant
- requestAnimationFrame for all movement
- CSS transforms/opacity only for animations
- Test on actual mobile device

OUTCOME MATRIX:
Correct grammar + Hit timing bar = Bundle → Basket → Couple ❤️ (+10 points, combo+1)
Wrong grammar + Hit timing bar = Bundle → 🐊 CROCODILE (-1 life, combo reset)
Any + Miss timing bar = Stork escapes → Couple disappointed (-1 life, combo reset)

FILE OUTPUT:
- index.html (complete game, CSS and JS embedded)
- README.md (usage instructions)

TESTING CHECKLIST:
- All 204 questions load
- No repeats in single playthrough
- Timing bar has no input lag
- Hit detection is fair
- All 3 outcomes work correctly
- Lives/score calculate properly
- Level progression at 5 babies each
- Game over at 0 lives
- Victory after level 6
- 60fps on mobile
- Portrait shows rotate message

DO NOT:
- Use images or external assets
- Use frameworks (vanilla JS only)
- Make storks look like triangles
- Use GRASP brand colors anywhere except the top-left badge
- Add article colors to boulders that match branding
- Skip mobile testing
- Downgrade quality for speed

BUILD QUALITY ASSETS. You have the budget for professional polish.
