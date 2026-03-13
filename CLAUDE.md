# Abdul's Contributions - Milestone 4: Alpha (Week 09, Mar 12, 2026)

## Level Design & Programming

### Wave System (WaveManager.cs)
- Designed 3-wave progression for Level 2 with escalating difficulty:
  - Wave 1: 5 enemies, 2s spawn interval, random lanes
  - Wave 2: 10 enemies, 1.5s spawn interval, random lanes
  - Wave 3: 10 enemies, 1.2s spawn interval, random lanes
- Built the game state machine: Idle → SpawningWave → WaveInProgress → WaveComplete → Victory/GameOver
- Integrated narrative beats at key moments (first scroll damage, wave completion, final wave start)
- Tuned spark pickup drops to occur every 3-7 enemy kills

### Enemy Mechanics (Enemy.cs, EnemyAttackBehavior.cs, EnemySpawner.cs)
- Lane-locked enemy movement with configurable speed
- Enemy attack state machine: Moving → Attacking → Lunging → Returning
- Lunge animation (0.3 units forward over 0.15s) for visual attack feedback
- Hit flash effect (white tint for 0.12s) on damage
- Ink shield integration where enemies gain a 1-HP shield on ink trails left by other enemies (InkShield.cs)
- Shield cooldown system (2s) to prevent constant shielding
- Auto-configured spawn positions from GridGenerator across 3 lanes

### Tower Systems (TowerAttack.cs, TowerDrag.cs, TowerHealth.cs, Tower.cs)
- Tower placement via drag-to-grid with snap-to-tile positioning
- Range visualization during placement:
  - Pencil: 4 tiles to the right (stops at mug obstacles)
  - Compass: All tiles to the right
- Placement validation: tile occupancy, spark cost, ink restrictions
- Attack system with lane-matched enemy detection (10f radius) and nearest-target selection
- Fire rate of 1 attack/second, 25 damage per projectile
- Tower health by type: StickyNote 4 HP, all others 2 HP
- Eraser as consumable tower that cleans ink and self-destructs

### Projectile Systems (Projectile.cs, ArcProjectile.cs)
- Standard projectile: tracks target at 10 units/second with 3s lifetime
- Arc projectile for Compass: parabolic flight (arcHeight 5, 1s duration) with 1.5-unit splash damage radius

### Grid & Environment (GridGenerator.cs, GridTile.cs)
- 8x3 procedural checkerboard grid with configurable tile sizing
- Ink tile system: enemies convert tiles to ink as they pass, blocking tower placement
- Ink immunity timer (4s) prevents rapid re-inking after cleaning
- Tile highlight overlays for placement feedback

### Economy (SparkManager.cs, SparkPickup.cs)
- 10 starting sparks, 5 sparks per tower placement
- Spark generation scales inversely with active SparkTower count (6s base interval / tower count)
- Clickable spark pickups (+2 sparks) spawn at enemy death positions with 5s lifetime

### Narrative & UI (NarrativeEventUI.cs, ScrollHealth.cs, KillQuipDisplay.cs, GameOverlay.cs)
- Story popups that freeze gameplay until dismissed
- Progressive scroll damage sprites (clean → damage1 → damage2 → destroyed at 3 HP)
- Tower kill quips system with 5 unique quips per tower type (Pencil, Compass, StickyNote, SparkTower)
- StickyNote defensive quips triggered after 2-4 hits
- Victory/defeat overlay with game pause

## Playtesting
- Partnered with Kate to test mechanics and gameplay flow
- Validated difficulty progression, tower balance, and enemy behavior

## Video Recording
- Captured and narrated gameplay footage for the alpha demo presentation
