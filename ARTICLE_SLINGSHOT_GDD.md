# ARTICLE SLINGSHOT - GAME DESIGN DOCUMENT

**Version:** 1.0  
**Date:** November 2025  
**Project:** GRASP by Gregor - English Article Practice Game  
**Target Platform:** Web (Mobile-first, Landscape orientation)

---

## 🎯 GAME OVERVIEW

### Core Concept
A high-stakes article practice game where players shoot article boulders at flying storks carrying baby bundles. Correct grammar + accurate aim = happy families. Wrong grammar = crocodile punishment. Built to teach Russian speakers English articles through emotional engagement and time pressure.

### Target Audience
- Russian-speaking ESL students (intermediate level)
- Ages: 16-40+
- Learning English articles (a/an/the/zero)
- Mobile users primarily

### Learning Objectives
1. Rapid article recognition (no time to analyze)
2. Pattern recognition over rule memorization
3. Emotional memory anchoring (crocodile = wrong article)
4. Build intuition for specific vs general context

---

## 🎮 CORE MECHANICS

### 1. ARTICLE SELECTION PHASE

**Player Action:**
- Stork appears flying right-to-left with sentence
- Player clicks one of three article boulders:
  - **A/AN** (orange boulder, white text)
  - **THE** (blue boulder, white text)
  - **∅** (purple boulder, white text for "NONE")

**No Immediate Feedback:**
- Selection does NOT show green/red
- Boulder loads into slingshot
- Player doesn't know if grammar is correct yet

**Time Pressure:**
- Stork keeps flying while player decides
- ~8-10 seconds visible window before off-screen
- Forces fast decision-making

---

### 2. TIMING BAR MECHANIC

**Activation:**
- Immediately after article selection
- Timing bar appears above/near slingshot
- Moving indicator sweeps left ↔ right

**Bar Structure:**
```
┌─────────────────────────────────┐
│ [RED] [GREEN] [RED]             │ ← Zones
│       ↕ Indicator               │
└─────────────────────────────────┘
```

**Zone Sizes (starting):**
- Green zone: 20% of bar width (Level 1)
- Red zones: 80% of bar width (failure zones)

**Indicator Speed:**
- Starts moderate (~1 second per sweep)
- Increases with each level
- Smooth easing (not linear)

**Player Action:**
- Click/tap when indicator is in GREEN ZONE
- One chance only - click registers immediately

---

### 3. SHOOTING & REVEAL SEQUENCE

**Timing Bar Result:**

**IF PLAYER HITS GREEN ZONE:**
```
1. Green flash on timing bar (0.2s)
2. Boulder launches toward stork
3. Trajectory arc (parabolic path)
4. Boulder hits stork (0.5s flight time)
5. Stork shakes/reacts
6. Bundle drops
7. REVEAL HAPPENS HERE:
```

**CORRECT GRAMMAR + GOOD AIM:**
- Bundle falls smoothly into basket
- Basket floats to couple
- Couple shows love ❤️ (hearts animation)
- +10 points
- Combo +1

**WRONG GRAMMAR + GOOD AIM:**
- Bundle starts to fall toward basket
- Crocodile eyes glow underwater
- Crocodile mouth opens (jaw animation)
- Snaps bundle mid-air
- Basket knocks away
- Couple devastated/crying
- Combo resets to 0
- Lives -1

**IF PLAYER MISSES GREEN ZONE:**
```
1. Red flash on timing bar
2. Boulder launches but trajectory is off
3. Misses stork completely
4. Stork flies past (disappointed animation)
5. Empty basket floats past couple
6. Couple shows disappointment
7. No points
8. Combo resets to 0
9. Lives -1
```

---

### 4. OUTCOME MATRIX

| Grammar | Aim | Visual Result | Score | Lives | Combo |
|---------|-----|---------------|-------|-------|-------|
| ✅ Correct | 🎯 Green zone | Baby → Basket → ❤️ | +10 | No change | +1 |
| ✅ Correct | ❌ Red zone | Boulder misses | 0 | -1 | Reset |
| ❌ Wrong | 🎯 Green zone | Baby → 🐊 SNATCH | 0 | -1 | Reset |
| ❌ Wrong | ❌ Red zone | Boulder misses | 0 | -1 | Reset |

**Critical Design Decision:**
- Wrong grammar + perfect aim = STILL GREEN FLASH before reveal
- This creates "false success" → emotional impact when crocodile appears
- Player thinks they succeeded, THEN learns they failed

---

## 📈 PROGRESSION SYSTEM

### Level Structure

```
LEVEL 1: 1 Family
- 1 couple waiting at left
- 1 stork at a time (center height)
- 5 successful deliveries = Level Up
- Timing bar: 20% green zone
- Stork speed: 100% (baseline)

LEVEL 2: 2 Families
- Original couple + NEW couple joins (below first)
- 2 storks possible (staggered timing)
- Never both at exactly same time
- 5 successful deliveries = Level Up (10 total)
- Timing bar: 18% green zone
- Stork speed: 110%

LEVEL 3: 3 Families
- 3 couples (stacked vertically)
- Up to 3 storks (more overlap possible)
- 5 successful deliveries = Level Up (15 total)
- Timing bar: 16% green zone
- Stork speed: 120%

LEVEL 4: 4 Families
- 4 couples
- Up to 4 storks
- 5 successful deliveries = Level Up (20 total)
- Timing bar: 14% green zone
- Stork speed: 130%

LEVEL 5: 5 Families
- 5 couples
- Up to 5 storks (screen getting busy)
- 5 successful deliveries = Level Up (25 total)
- Timing bar: 12% green zone
- Stork speed: 140%

LEVEL 6: 6 Families (FINAL)
- 6 couples (maximum)
- Up to 6 storks (maximum chaos)
- 5 successful deliveries = VICTORY (30 total)
- Timing bar: 10% green zone
- Stork speed: 150%
```

### Difficulty Scaling

**Dual escalation:**
1. **Timing bar shrinks** (less margin for error)
2. **Stork speed increases** (less time to decide grammar)

**Stork Staggering:**
- Level 1: Single stork, 8-12 second gaps
- Level 2: 2 storks, 5-8 second gaps, different heights
- Level 3+: More overlap, multiple storks visible simultaneously
- Level 6: Near-constant storks (3-5 second gaps)

---

## 💔 LIVES & GAME OVER

### Lives System
- **Start with 3 lives** (displayed as hearts: ❤️❤️❤️)
- **Lose 1 life for:**
  - Missing timing bar (bad aim)
  - Wrong article (crocodile)
- **Lives do NOT regenerate**

### Game Over Condition
**When lives reach 0:**
```
1. Current stork disappears
2. All baskets stop floating
3. All couples turn to face each other
4. Anger emojis appear (💢)
5. Couples argue animation
6. Walk in opposite directions (leaving screen)
7. Screen fades to black
8. "GAME OVER" text appears
9. Final stats displayed:
   - Total Score
   - Questions Answered
   - Accuracy %
   - Highest Level Reached
10. [PLAY AGAIN] button
```

**Emotional Design:**
- Guilt trip: "You failed them all"
- Makes player want to retry
- Reinforces consequences of wrong grammar

---

## 🏆 VICTORY CONDITION

**Completing Level 6:**
```
1. 30th successful delivery
2. All families celebrate together
3. Fireworks/stars animation
4. "FAMILY COMPLETE!" message
5. Final stats:
   - Total Score
   - Perfect Accuracy Bonus (if 0 mistakes)
   - Time Taken
6. [PLAY AGAIN] button
```

---

## 🎨 VISUAL DESIGN

### Theme: Night Sky

**Color Palette:**
```css
--night-sky-dark: #0a0e27
--night-sky-light: #1a1f3a
--river-dark: #1e3a5f
--river-light: #2a4f7f
--crocodile-eyes: #ffeb3b
--basket-brown: #4a3520
--couple-skin: #ffdbac
--hearts-red: #ff6b9d
--stars-white: #ffffff
```

### Minimalist/Geometric Style

**Why this style:**
- Claude Code can build with CSS/SVG
- No custom artwork needed
- Clean, modern aesthetic
- Performs well on mobile
- Easy to animate

---

### Visual Elements Breakdown

#### 1. BACKGROUND (Sky)
```
- Dark gradient (top: #0a0e27 → bottom: #1a1f3a)
- Scattered white dots (stars, 50-100 stars)
- Stars twinkle (CSS animation, 2-4s random)
- Static background (doesn't scroll)
```

#### 2. STORK
```
SVG Path or CSS Shapes:
- Bird body: Triangle or ellipse (#2d3436)
- Wings: Two triangles, flapping animation
- Beak: Small triangle (#ff7f00)
- Bundle below: White cloth shape, tied with ribbon
- Sentence: White text above/beside stork
  - Font: 18-20px, bold
  - Black outline (text-shadow for visibility)
  - Blank shown as: "___"

Animation:
- Flies right → left (transform: translateX)
- Slight up/down bobbing (sine wave, 10px amplitude)
- Wings flap (rotate animation, 0.3s cycle)
- When hit: Shake animation (0.3s)
```

#### 3. RIVER
```
- Horizontal strip (20% screen height)
- Dark blue gradient with transparency
- Wavy top edge (CSS clip-path or SVG)
- Gentle flow animation (slow scroll effect)
- Darker than sky (depth perception)
```

#### 4. CROCODILE
```
Default state: HIDDEN

When triggered:
1. Two glowing eyes appear (yellow circles, #ffeb3b)
   - Glow effect: box-shadow: 0 0 20px #ffeb3b
   - Rise from bottom of river
   - Fade in (0.3s)

2. Jaw opens:
   - Two dark triangular shapes (upper/lower jaw)
   - Teeth: White zigzag pattern
   - Opens rapidly (0.2s)

3. Snaps bundle:
   - Bundle disappears instantly
   - Splash effect (white circles expanding)
   - Crocodile submerges (eyes fade out)

Total sequence: ~1 second
```

#### 5. BASKETS
```
- Simple rounded rectangle shape
- Dark brown (#4a3520)
- Small (80px × 60px)
- Float left on river surface
- Gentle bob animation (vertical, 5px)
- Synchronized with stork timings
- Each basket "belongs" to a stork
- Almost invisible at night (hard mode feature)
```

#### 6. COUPLES
```
Position: Left edge of screen, vertically stacked

Each couple:
- Two stick figures or simple shapes
- Standing side-by-side
- Colors: Pink/Blue or varied skin tones
- Simple circles for heads, lines for bodies

States:
1. WAITING: Looking right (toward river)
2. SUCCESS: Hearts appear above (❤️❤️), jump animation
3. FAILURE (Crocodile): Crying eyes, sad posture
4. FAILURE (Miss): Disappointed slump
5. GAME OVER: Turn to face each other, anger emoji (💢), walk away

Animations:
- Hearts: Rise and fade (1s)
- Jump: Quick bounce (0.5s)
- Crying: Tears fall (CSS animation)
- Walking away: Slide opposite directions (2s)
```

#### 7. SLINGSHOT
```
Position: Bottom-center of screen

Structure:
- Two vertical posts (brown rectangles, 8px × 100px)
- Elastic band (brown curved path between posts)
- Band stretches when boulder loaded

Boulder states:
1. Resting at bottom (3 boulders in a row)
2. Loaded in slingshot (selected boulder moves up)
3. Launching (boulder travels along parabolic path)

Boulder colors:
- A/AN: Orange (#F57C00)
- THE: Blue (#1976D2)
- ∅: Purple (#7B1FA2)
- White text, bold, uppercase
```

#### 8. TIMING BAR
```
Position: Above slingshot OR floating near stork

Structure:
┌─────────────────────────────────┐
│ [    RED    |GREEN|    RED    ] │
│              ↑                  │
│          Indicator              │
└─────────────────────────────────┘

Dimensions:
- Width: 300px (mobile), 400px (desktop)
- Height: 40px
- Border: 2px solid white
- Border-radius: 8px

Zones:
- Green: Center, variable width (20%-10%)
- Red: Sides, remainder
- Background: Semi-transparent dark

Indicator:
- Vertical line or arrow (white)
- Width: 4px
- Height: 100% of bar
- Moves smoothly (CSS transition or requestAnimationFrame)
- Easing: linear (for predictability)

Flash effects:
- Green hit: Entire bar glows green (0.2s)
- Red miss: Entire bar glows red (0.2s)
```

#### 9. SENTENCE DISPLAY
```
Position: Attached to stork (speech bubble style) OR floating above

Format:
"I finished ___ book you lent me."
          ^^^
         BLANK

Styling:
- Font: 18-20px, bold, sans-serif
- Color: White (#ffffff)
- Stroke: 2px black (text-shadow for outline)
- Background: Semi-transparent dark box
  - Background: rgba(0,0,0,0.6)
  - Padding: 10px 15px
  - Border-radius: 8px
- Max-width: 80% of stork flight path
- Word wrap if needed

Blank marker:
- "___" (three underscores)
- Same style as rest of text
- Could add yellow highlight behind blank
```

---

### UI Layout (Mobile Landscape)

```
┌─────────────────────────────────────────────────────────────┐
│ [GRASP badge] [by Gregor]    LIVES: ❤️❤️❤️     SCORE: 120  │ ← HEADER (50px)
├─────────────────────────────────────────────────────────────┤
│                    ✨  ✨  ✨  ✨  ✨                         │
│  🦅→ "I saw ___ dog"                                        │
│                                              🦅→             │ SKY ZONE
│                                                              │ (60% height)
│  🦅→                                                         │
├─────────────────────────────────────────────────────────────┤
│ ~~~~~~~~~~~~~~~~ 🌊 [basket→] [basket→] 🌊 ~~~~~~~~~~~~~~~~│ RIVER (15%)
│  👫❤️  👫   👫   👫   👫   👫                                │ COUPLES (10%)
├─────────────────────────────────────────────────────────────┤
│                        🎯 SLINGSHOT                          │
│                  [A/AN]  [THE]  [∅]                         │ CONTROL ZONE
│              ┌─────────▶●◀──────────┐                      │ (15% height)
│              │   Timing Bar          │                      │
└─────────────────────────────────────────────────────────────┘

Screen regions:
- Header: 50px fixed
- Sky: ~400px (60%)
- River: ~100px (15%)
- Couples: ~70px (10%)
- Controls: ~100px (15%)

Total: ~720px (fits landscape mobile)
```

### Responsive Breakpoints
```css
/* Mobile Landscape (PRIMARY) */
@media (min-width: 568px) and (max-width: 1024px) and (orientation: landscape)

/* Tablet Landscape */
@media (min-width: 1024px) and (orientation: landscape)

/* Desktop */
@media (min-width: 1280px)

/* Portrait Warning */
@media (orientation: portrait) {
  /* Show "Please rotate device" message */
}
```

---

## 🔊 SOUND EFFECTS (Phase 2 - Placeholder hooks)

### Sound Events
```javascript
// Placeholder functions - implement later
function playWhoosh() {}      // Boulder launches
function playSplash() {}      // Crocodile emerges
function playCelebrate() {}   // Couple receives baby
function playCry() {}          // Couple disappointed
function playClick() {}        // UI interactions
function playLevelUp() {}      // New family joins
function playGameOver() {}     // Final game over sound

// Volume control
let soundEnabled = true;
function toggleSound() {
  soundEnabled = !soundEnabled;
}
```

---

## 💻 TECHNICAL SPECIFICATIONS

### Tech Stack
- **HTML5** (semantic markup)
- **CSS3** (animations, transforms, flexbox/grid)
- **Vanilla JavaScript** (ES6+, no frameworks)
- **SVG** (for shapes if needed, or pure CSS)
- **LocalStorage** (for high score persistence)

### Performance Targets
- **60 FPS** animations (requestAnimationFrame)
- **<2 second** initial load time
- **<500ms** response to user input
- **<100KB** total bundle size (uncompressed)

### Browser Support
- **Chrome** 90+ (primary)
- **Safari** iOS 14+ (mobile primary)
- **Firefox** 88+
- **Edge** 90+
- No IE11 support required

### File Structure
```
article-slingshot/
├── index.html           (main game file)
├── styles.css          (all styles)
├── game.js             (game logic)
├── article-questions.json  (question bank)
├── README.md           (setup instructions)
└── assets/             (optional folder for future sounds)
```

### Data Flow
```
1. Load questions from JSON
2. Shuffle questions
3. Game loop:
   a. Display stork + sentence
   b. Player selects article
   c. Timing bar challenge
   d. Calculate outcome
   e. Animate result
   f. Update score/lives
   g. Check win/lose conditions
   h. Next question or end game
```

---

## 🎮 GAME FLOW DIAGRAM

```
┌─────────────┐
│ LOAD SCREEN │
│   (Logo)    │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ START MENU  │
│  [PLAY]     │
│  [RULES]    │
└──────┬──────┘
       │
       ▼
┌────────────────────┐
│ GAME INITIALIZES   │
│ - Load 200 questions│
│ - Shuffle          │
│ - Set Level 1      │
│ - Lives = 3        │
└──────┬─────────────┘
       │
       ▼
┌────────────────────┐
│  GAMEPLAY LOOP     │◄─────────┐
│                    │          │
│  1. Spawn stork    │          │
│  2. Show sentence  │          │
│  3. Player picks   │          │
│  4. Timing bar     │          │
│  5. Resolve        │          │
│  6. Update UI      │          │
│                    │          │
│  Lives > 0?  ──────┴─YES──────┘
│     │                          
│     NO                         
│     │                          
│     ▼                          
│ GAME OVER                      
│  - Show stats                  
│  - [PLAY AGAIN]                
└────────────────────┘           
```

---

## 📱 USER INTERACTIONS

### Input Methods
1. **Touch** (mobile primary)
   - Tap boulder to select
   - Tap anywhere to trigger timing bar

2. **Mouse** (desktop)
   - Click boulder to select
   - Click anywhere to trigger timing bar

3. **Keyboard** (optional enhancement)
   - `1` = A/AN
   - `2` = THE
   - `3` = ∅
   - `SPACE` = Trigger timing bar

### Feedback Systems

**Visual Feedback:**
- Boulder selection: Scale up selected boulder
- Timing bar: Color flash (green/red)
- Score: +10 floats up from couple
- Lives: Heart disappears with fade
- Level up: "NEW FAMILY!" banner

**Animation Feedback:**
- Smooth boulder trajectory
- Stork reaction (shake if hit)
- Crocodile emergence (scary!)
- Couple emotions (hearts, tears)

**No Audio Feedback** (Phase 1)
- Placeholder hooks only
- Add in Phase 2

---

## 🐛 EDGE CASES & ERROR HANDLING

### Question Bank Issues
```javascript
// Handle missing/invalid questions
if (!questions || questions.length < 30) {
  showError("Question bank too small");
  return;
}

// Handle duplicate questions
questions = removeDuplicates(questions);

// Validate question format
questions.forEach(q => {
  if (!q.sentence || !q.correctArticle) {
    console.error("Invalid question:", q);
  }
});
```

### Timing Issues
```javascript
// Handle rapid clicking
let isProcessing = false;
function handleClick() {
  if (isProcessing) return;
  isProcessing = true;
  // ... process click
  setTimeout(() => isProcessing = false, 100);
}

// Handle stork off-screen
if (stork.x < -stork.width) {
  // Count as miss
  loseLife();
  nextQuestion();
}
```

### State Management
```javascript
const gameState = {
  level: 1,
  lives: 3,
  score: 0,
  correctCount: 0,
  incorrectCount: 0,
  currentQuestion: null,
  isProcessing: false,
  gameOver: false,
  questionsUsed: []
};
```

---

## 📊 ANALYTICS & TRACKING

### Session Data (LocalStorage)
```javascript
{
  highScore: 0,
  gamesPlayed: 0,
  totalQuestionsAnswered: 0,
  totalCorrect: 0,
  bestStreak: 0,
  highestLevel: 1,
  lastPlayed: "2025-11-20"
}
```

### Per-Game Stats
```javascript
{
  score: 0,
  questionsAnswered: 0,
  correct: 0,
  incorrect: 0,
  accuracy: 0,
  levelReached: 1,
  timeElapsed: 0
}
```

---

## 🚀 DEVELOPMENT PHASES

### Phase 1: Core Mechanics (MVP)
- ✅ Basic layout (sky, river, couples, slingshot)
- ✅ Stork spawning and movement
- ✅ Article selection system
- ✅ Timing bar mechanic
- ✅ Hit detection and outcomes
- ✅ Lives and game over
- ✅ Question loading from JSON
- ✅ Level progression (1-6)

### Phase 2: Polish
- Animations (smooth, juice)
- Sound effects
- Particle effects (stars, splashes)
- Better visual feedback
- Mobile optimization

### Phase 3: Enhancement
- Statistics screen
- Difficulty settings
- Question categories filter
- Explanation mode (show why answer is correct)
- Tutorial/practice mode

---

## 🎯 SUCCESS CRITERIA

### Functional Requirements
- ✅ Game runs smoothly on mobile (60fps)
- ✅ All 200 questions load correctly
- ✅ Win/lose conditions work properly
- ✅ Progression system scales difficulty
- ✅ Crocodile reveal creates emotional impact
- ✅ Timing bar feels fair and responsive

### Learning Requirements
- ✅ Students can complete 30 questions (~10 min)
- ✅ Wrong answers are memorable (crocodile!)
- ✅ Time pressure forces pattern recognition
- ✅ Multiple playthroughs show different questions

### Polish Requirements
- ✅ Game feels polished and complete
- ✅ GRASP branding visible and correct
- ✅ No bugs or crashes
- ✅ Mobile landscape works perfectly

---

## 📝 NOTES FOR IMPLEMENTATION

### For Claude Code:
1. **Start with static layout first** - get all visual elements positioned
2. **Then add movement** - stork flying, timing bar
3. **Then add game logic** - scoring, lives, outcomes
4. **Test on mobile constantly** - this is the primary platform
5. **Keep it simple** - no over-engineering, vanilla JS only
6. **Comment thoroughly** - explain why, not just what

### Critical Implementation Details:
- Use `requestAnimationFrame` for smooth 60fps
- Timing bar MUST feel fair (no lag between click and registration)
- Stork trajectory MUST be visible for 8-10 seconds minimum
- Crocodile reveal MUST be surprising (eyes glow suddenly)
- Green flash MUST happen even on wrong grammar (false success)

### Testing Checklist:
- [ ] Portrait mode shows rotate message
- [ ] All 200 questions load without errors
- [ ] No question repeats in single playthrough
- [ ] Lives decrement correctly
- [ ] Level progression happens at 5 babies
- [ ] Game over triggers at 0 lives
- [ ] Victory triggers at level 6 completion
- [ ] Timing bar feels responsive
- [ ] Crocodile appears only on wrong grammar
- [ ] Baskets are hard to see (night mode feature)

---

## 🎨 BRANDING REQUIREMENTS

### GRASP Badge (Top-Left)
```css
.brand-badge {
  background: #F57C00;  /* Orange #2 */
  color: white;
  padding: 8px 20px;
  border-radius: 6px;
  font-family: 'Poppins', sans-serif;
  font-weight: 700;
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.brand-by {
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 14px;
  color: rgba(255, 255, 255, 0.8);
  margin-left: 12px;
}
```

### Google Fonts Import
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@700&family=Montserrat:wght@400&display=swap" rel="stylesheet">
```

---

## 📦 DELIVERABLES

### What Claude Code Should Produce:
1. **index.html** - Complete game in single file (or modular)
2. **styles.css** - All styles, organized by component
3. **game.js** - All game logic, well-commented
4. **article-questions.json** - Placeholder with 10 example questions
5. **README.md** - How to play, how to add questions, tech stack

### What We Provide to Claude Code:
1. This GDD (complete game design)
2. Example questions (10 from GPT-generated bank)
3. JSON format specification
4. Technical requirements
5. Phase-by-phase implementation plan

---

**END OF GAME DESIGN DOCUMENT**

This document should contain everything needed to implement Article Slingshot. Any questions or clarifications should be added to this document before development begins.

**Version History:**
- v1.0 (2025-11-20): Initial complete GDD
