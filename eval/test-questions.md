# agentbrand.fit Crimson Desert Companion Substrate Eval v1.0

This file is the substrate eval for the agentbrand.fit Crimson Desert Companion. It defines a manual test harness for retrieval-grounded answers about Crimson Desert once the corpus has been ingested into the tenant knowledge substrate.

Each question represents a real question Adam could plausibly ask during a live play session. The paired rubric defines what a good Companion response contains, what it avoids, and which substrate capability the question primarily exercises.

This is not an automated test. After the Companion goes live, a human grader uses these questions and rubrics to judge whether answers are grounded, useful, current, and free of hallucination.

This file is versioned as v1.0. Future versions add questions to the end of the rubric; questions are never deleted, so the eval grows as the corpus grows.

## Question Categories

**Lookup** questions ask for specific facts with one correct answer, such as a location, item source, NPC name, challenge reward, or exact mechanic interaction. A good answer should retrieve the fact cleanly, include the minimum useful context, and avoid turning a narrow lookup into a broad guide.

**Mechanics explanation** questions ask how a system works, such as the skill tree, Watch and Learn, Hero Contribution, refinement, cooking, storage, or Sealed Abyss Artifact challenges. A good answer should explain the moving parts in player language and identify the limits or unlock conditions that matter during play.

**Strategic planning** questions ask for multi-variable advice where the answer depends on Adam's stated character state. A good answer should use the level, chapter, party access, gear, resources, camp state, and current blocker embedded in the question rather than giving generic best-practice advice.

**Combat tactics** questions ask for encounter plans, boss strategies, defensive timing, skill use, weakness exploitation, and recovery setup. A good answer should name the specific threat, tell the player what to do next, and separate reliable tactics from risky or source-conflicted claims.

**Comparison and synthesis** questions ask the Companion to combine sources or handle disagreements between guides, wikis, patch notes, and community posts. A good answer should surface material conflicts explicitly, explain which source is safer for the current patch or player state, and avoid pretending disputed advice is settled.

**Patch awareness** questions ask what changed in recent updates and whether older advice still applies. A good answer should retrieve dated patch information, distinguish live changes from announced future changes, and avoid applying stale launch-week assumptions to the current build.

## Question Set

### Q01. Lookup — hernand_contribution_shop

**Question:**
Where do I spend Hernandian Contribution, and what should I do to earn more without tanking it?

**What a good answer contains:**
- Names the Contribution Shop as being in Hernand Castle.
- Explains that Contribution fills a regional meter and converts into spendable points.
- Lists reliable earn sources such as requests, bounties, giving money to beggars, freeing Pailunese refugees, main quests, or liberating hideouts.
- Warns that stealing decreases Contribution even if Adam is not caught.

**What a good answer avoids:**
- Treating Contribution as ordinary Silver, Copper, or character XP.
- Inventing a universal shop that serves every region from one menu.
- Recommending theft as a neutral money route without noting the Contribution loss.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q02. Lookup — first_faded_abyss_artifact

**Question:**
I want a respec safety net before I leave Chapter 1; where is the first Faded Abyss Artifact?

**What a good answer contains:**
- Says the first Faded Abyss Artifact is in a chest in Hernand Castle during the Chapter 1 main quest Trace.
- Specifies that the chest is in the mysterious-key room before entering the Abyss portal.
- Notes that it is the respec item, not the same as regular Abyss Artifacts or Sealed Abyss Artifacts.
- Mentions that the chest can be returned to later if Adam missed it.

**What a good answer avoids:**
- Saying Faded Abyss Artifacts are buyable from ordinary early-game vendors.
- Confusing the Chapter 1 chest with Sealed Abyss Artifact roadside challenges.
- Spoiling story content beyond the Chapter 1 Abyss portal setup.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval

### Q03. Lookup — hernand_inventory_expansion

**Question:**
My bags are full in Hernand; what are the real early ways to increase inventory slots?

**What a good answer contains:**
- States that inventory is slot-based rather than weight-based.
- Says Small Bags can be bought from vendors and add one slot each.
- Says Medium Bags commonly come from Commissions or Faction Quest rewards and add more slots than Small Bags.
- Tells Adam to preview Journal rewards and prioritize quests with an inventory expansion icon.
- Mentions using storage or the supply chest as management help, not as a slot upgrade.

**What a good answer avoids:**
- Inventing a strength or encumbrance stat that expands carry capacity.
- Saying recipes, documents, or gear stop taking slots after being read or used unless sold, discarded, or stored.
- Treating the supply chest as a permanent inventory-size increase.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q04. Lookup — first_bell_tower

**Question:**
I just picked up Toll of Pywel and only want the first safe bell; where should I go?

**What a good answer contains:**
- Identifies the Hernand bell as the first safe bell.
- Places it near the starting city area, west of Hernand's tavern.
- Explains that ringing bells reveals map coverage for their area.
- Keeps the answer limited to early reachable map help unless Adam asks for the full bell list.

**What a good answer avoids:**
- Dumping late-region bell locations when the question asks for the first safe one.
- Claiming every bell can be safely completed in Chapter 1.
- Spoiling late quest gates or late-region story context.

**Difficulty:** Medium
**Substrate capability tested:** SUB-005 building isolation + Companion synthesis

### Q05. Lookup — chapter_two_hornsplitter_reward

**Question:**
What do I get for beating Kailok the Hornsplitter at the end of Chapter 2?

**What a good answer contains:**
- Names Kailok the Hornsplitter as the Chapter 2 Goldleaf boss.
- Says the reward is the Sword of the Lord.
- Notes that the Sword of the Lord can fire wind shockwaves on certain attacks.
- Clarifies that this fight completes Chapter 2.

**What a good answer avoids:**
- Calling the reward Staglord's Shield or another optional-boss drop.
- Misplacing Kailok as a Chapter 3 or late-game boss.
- Adding post-Chapter 3 story consequences.

**Difficulty:** Hard
**Substrate capability tested:** SUB-004 retrieval

### Q06. Mechanics explanation — abyss_artifact_types

**Question:**
I keep seeing Abyss Artifact, Sealed Abyss Artifact, and Faded Abyss Artifact; can you separate what each one does?

**What a good answer contains:**
- Explains that regular Abyss Artifacts are spent on skill tree unlocks or upgrades.
- Explains that Sealed Abyss Artifacts are found in the world and tied to specific challenges before rewards can be claimed.
- Explains that Faded Abyss Artifacts are consumed to reset the skill tree and recover spent points.
- Notes that Sealed challenge rewards can include regular Abyss Artifacts, Faded Abyss Artifacts, or Abyss Gear.
- Warns Adam not to spend or value the three item types interchangeably.

**What a good answer avoids:**
- Saying all three artifacts are the same currency with different names.
- Telling Adam that Faded Abyss Artifacts unlock normal skill nodes.
- Ignoring the challenge step for Sealed Abyss Artifacts.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q07. Mechanics explanation — watch_and_learn_observation

**Question:**
How does Watch and Learn actually unlock skills, and should I spend Abyss Artifacts on skills marked for observation?

**What a good answer contains:**
- Explains that Watch and Learn involves observing enemies, bosses, NPCs, or hologram-like sources using techniques.
- Says observation-marked skills should generally be checked against their source before spending scarce Abyss Artifacts.
- Explicitly flags that public sources disagree on whether observation skills are free permanent unlocks or require spending an Abyss Artifact after banking the observation.
- Advises the Companion to cite the corpus source it is relying on and tell Adam the uncertainty if the corpus has conflicting atoms.
- Notes that observed skills interact with respec differently depending on which source is correct, so that detail matters.

**What a good answer avoids:**
- Silently picking one conflicting explanation without acknowledging the disagreement.
- Claiming every skill can be learned through observation.
- Advising Adam to spend artifacts on observable skills before checking source availability.

**Difficulty:** Hard
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q08. Mechanics explanation — sealed_artifact_challenges

**Question:**
I picked up a Sealed Abyss Artifact and nothing obvious happened; what am I supposed to do with it?

**What a good answer contains:**
- Explains that a Sealed Abyss Artifact unlocks or tracks a specific Challenge objective.
- Gives examples of challenge types such as weapon mastery, healing allies, rope-walking, sliding, archery streaks, or Duo streaks.
- Says rewards are claimed after completing the challenge, often while standing still with weapons sheathed.
- Mentions that challenge rewards can feed progression through Abyss Artifacts, Faded Abyss Artifacts, or Abyss Gear.
- Suggests checking the Challenges menu or artifact entry rather than wandering randomly.

**What a good answer avoids:**
- Treating the item as an immediately spendable skill point.
- Saying every Sealed Abyss Artifact has the same objective.
- Inventing a vendor who unseals all artifacts for Silver.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q09. Mechanics explanation — cooking_food_healing

**Question:**
Do I need to cook before bosses, or is food just background flavor?

**What a good answer contains:**
- Explains that food is combat-relevant because it can heal during fights when equipped on the consumables wheel.
- Mentions that Patch 1.00.03 increased Health restored from food and items.
- Advises preparing healing food before bosses such as Hornsplitter.
- Explains that recipes should be read or learned before selling the recipe item.
- Distinguishes cooking and food from permanent stat progression.

**What a good answer avoids:**
- Saying food is only cosmetic or roleplay.
- Recommending selling unread recipes for money.
- Ignoring patch changes that affected healing value.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q10. Mechanics explanation — parry_counter_basics

**Question:**
Why do guides keep saying to parry instead of just blocking, and what do I need unlocked?

**What a good answer contains:**
- Explains that a parry happens by guarding just before an enemy attack lands.
- Notes that Kliff has Keen Senses unlocked by default, while other characters may require unlocks.
- Describes the payoff as creating a punish window or stagger opportunity rather than only reducing damage.
- Separates normal guard/block from timed parry and counter follow-ups.
- Mentions that red-glint or unblockable attacks should be dodged, not parried.

**What a good answer avoids:**
- Saying the player should hold guard forever through every boss string.
- Claiming all attacks are parryable.
- Confusing parry timing with dodge timing or lock-on controls.

**Difficulty:** Hard
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q11. Strategic planning — chapter_two_low_stamina

**Question:**
I'm level 14 in Chapter 2, stuck on Hornsplitter, low stamina, sword-and-shield equipped, and I have one Faded Abyss Artifact; how should I rebuild tonight?

**What a good answer contains:**
- Uses the stated Chapter 2 Hornsplitter blocker as the planning anchor.
- Recommends spending more Abyss Artifacts on Health, Stamina, and Spirit fundamentals before flashy skills if Adam is overwhelmed.
- Suggests keeping sword and shield for stamina-efficient blocking and parry attempts.
- Recommends Force Palm investment, especially toward the three-hit Level 3 pattern if available.
- Advises stocking and equipping healing food before re-entering the fight.

**What a good answer avoids:**
- Giving a generic endgame build that ignores level 14 and Chapter 2.
- Spending the only Faded Abyss Artifact without explaining that it is consumed.
- Recommending Damiane or Oongka-only plans if Adam has not said they are available.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q12. Strategic planning — chapter_three_camp_inventory

**Question:**
I'm in Chapter 3 with Howling Hill camp unlocked, Greymane camp tier 1, 62 inventory slots, and my supply chest is filling up; what should I clean up first?

**What a good answer contains:**
- Uses the stated Chapter 3 Howling Hill camp access rather than early Hernand-only advice.
- Recommends emptying or checking the supply chest before it overflows or stops collecting missed goods.
- Recommends using Private Storage at camp for spare gear, boss drops, crafting materials, and stockpiled upgrade items.
- Suggests prioritizing Commissions that reward Medium Bags for permanent slot growth.
- Advises reading recipes first, then selling learned recipe items to save space and gain money.

**What a good answer avoids:**
- Acting as if Adam has no access to camp storage in Chapter 3.
- Telling Adam to discard rare boss gear before suggesting storage.
- Treating supply chest contents as automatically safe forever without capacity limits.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q13. Strategic planning — damiane_oongka_party_pool

**Question:**
I'm at Chapter 3, Kliff is my main, Damiane and Oongka are unlocked but under-geared, and I only have enough materials to improve one backup; who should get attention first?

**What a good answer contains:**
- Acknowledges the three-character pool of Kliff, Damiane, and Oongka.
- Asks or branches on Adam's actual blocker if the corpus does not establish one universal best backup.
- Notes that Patch 1.03 improved Damiane and Oongka for open-world play by adding Axiom Force, Nature's Snare, and related abilities.
- Explains that gear or skill investment should follow the role Adam needs, such as ranged utility, traversal, control, or boss damage.
- Warns that older launch advice undervaluing Damiane or Oongka may be stale after 1.03.

**What a good answer avoids:**
- Saying to ignore Damiane and Oongka because only Kliff matters, without patch context.
- Inventing a fourth shared-progression character in this eval's Crimson Desert pool.
- Giving a hard ranking without surfacing source confidence.

**Difficulty:** Hard
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q14. Strategic planning — observation_before_spending

**Question:**
I'm level 18, have 7 Abyss Artifacts unspent, just unlocked Oongka, and several sword skills say they can be observed; what should I buy now versus wait on?

**What a good answer contains:**
- Uses the stated level, unspent artifact count, Oongka unlock, and observable sword-skill context.
- Recommends checking observation sources before buying skills marked for Watch and Learn.
- Prioritizes durable fundamentals or non-observable utility if Adam lacks Health, Stamina, Spirit, or core control tools.
- Notes that observation-source guidance is conflict-prone and should be grounded in current corpus atoms.
- Suggests keeping some Abyss Artifacts unspent if the next session is exploration-heavy and observation targets are nearby.

**What a good answer avoids:**
- Spending all 7 artifacts on observable skills without caveats.
- Ignoring Oongka's unlock and shared planning implications.
- Claiming observation can replace every skill tree investment.

**Difficulty:** Medium
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q15. Strategic planning — early_money_route

**Question:**
I'm in early Chapter 2 with 40 Silver, unread recipes in my bag, the Hernand Duo table unlocked, and no spare Contribution; what's the safest money plan?

**What a good answer contains:**
- Tells Adam to read recipes before selling them.
- Explains that selling learned recipes frees slots and gives money without losing the learned recipe.
- Notes that Hernand Duo has a low buy-in compared with later gambling tables but still carries risk.
- Suggests avoiding theft if Adam cannot afford Contribution loss.
- Mentions archery contests or requests as alternatives if Adam wants lower-risk activity.

**What a good answer avoids:**
- Telling Adam to sell unread recipes.
- Recommending theft while ignoring Contribution penalties.
- Sending Adam to higher-stakes late-region gambling as the first move.

**Difficulty:** Hard
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q16. Combat tactics — hold_vs_tap_r1

**Question:**
I'm getting wrecked because I keep holding R1 in fights; what is the hold-vs-tap trap here?

**What a good answer contains:**
- Explains the difference between holding a defensive input to guard and timing a tap or guard press just before impact to parry.
- Notes that holding guard can drain stamina and leave Adam unable to block, dodge, or attack.
- Advises lowering guard between strings to recover stamina.
- Tells Adam to dodge red-glint or unblockable attacks instead of trying to guard through them.
- Recommends practicing on normal enemies before applying the timing to bosses.

**What a good answer avoids:**
- Saying to hold R1 or guard continuously through all boss combos.
- Treating stamina as irrelevant during defense.
- Claiming the same timing works for unblockable attacks.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q17. Combat tactics — staglord_parry_plan

**Question:**
I found Saigord the Staglord and he keeps deleting me; what's the safe plan if I am under-confident with parries?

**What a good answer contains:**
- Identifies Saigord the Staglord as a hard optional boss rather than a required Chapter 2 story boss.
- Tells Adam to treat red-glint or grab-style attacks as dodge checks, not block checks.
- Recommends mid-range patience, punishing after committed strings, and avoiding greed during shield pressure.
- Suggests returning later if under-leveled or under-geared because the fight is longer and harder than normal early encounters.
- If sources conflict on exact location or phase details, requires the Companion to flag the conflict rather than assert a shaky route.

**What a good answer avoids:**
- Confusing Staglord with Kailok the Hornsplitter or Reed Devil.
- Promising that one parry chain trivializes the whole fight.
- Giving late-story spoilers as motivation for the fight.

**Difficulty:** Hard
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q18. Combat tactics — hornsplitter_survival

**Question:**
Hornsplitter's wind waves keep clipping me; what should I do differently in the fight?

**What a good answer contains:**
- Says to use sword and shield for a safer block/parry plan.
- Explains that Adam can circle or dodge many wind waves and block the ones he cannot avoid.
- Reminds Adam to lower the shield between waves to recover stamina.
- Recommends Force Palm as a stun tool, especially the stronger chained version if unlocked.
- Tells Adam to use the finisher when Hornsplitter's stun or stagger bar is filled.

**What a good answer avoids:**
- Telling Adam to face-tank wind waves without stamina management.
- Ignoring Force Palm and finishers.
- Misnaming the boss or placing him outside Chapter 2.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q19. Combat tactics — excavatron_force_palm

**Question:**
Marnie's Excavatron is stunning me to death in the quarry; is there a gimmick or do I just need better gear?

**What a good answer contains:**
- Identifies Marnie's Excavatron as the machine boss in the Bandit-held Karin Quarry tied to House Roberts' Stolen Quarry.
- Recommends sword and shield as a safe baseline for blocking drill attacks.
- Explains the Force Palm Level 3 plan: repeated Force Palms can stun the machine and open a damage window.
- Advises retreating and using Focus to recharge Spirit between Force Palm sequences.
- Warns about the underground drill attack and advises sidestepping the final upward strike.

**What a good answer avoids:**
- Treating the fight as a pure DPS race.
- Forgetting Spirit recharge or Focus management.
- Confusing the Excavatron with a human boss like Hornsplitter.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q20. Combat tactics — reed_devil_preparation

**Question:**
I'm about to push Chapter 3's Reed Devil and my parries are sloppy; what should I prep before I trigger it?

**What a good answer contains:**
- Keeps the answer within Chapter 3 preparation and avoids later story spoilers.
- Recommends checking Health, Stamina, and Spirit investments before the fight.
- Advises bringing and equipping healing food on the consumable wheel.
- Suggests practicing parry timing on normal enemies and planning to dodge unblockable red-glint attacks.
- Mentions camp access as a chance to store loot, refine gear, and restock before committing.

**What a good answer avoids:**
- Revealing story content after Chapter 3.
- Saying parry timing does not matter for major bosses.
- Ignoring food and camp preparation even though Chapter 3 systems are available.

**Difficulty:** Hard
**Substrate capability tested:** SUB-005 building isolation + Companion synthesis

### Q21. Comparison and synthesis — early_skill_priority_conflict

**Question:**
Some guides say buy cool skills early and others say dump points into Health and Stamina; what should I actually do in the first 20 levels?

**What a good answer contains:**
- Explicitly surfaces the conflict between fun active-skill recommendations and fundamentals-first recommendations.
- Explains that early bosses punish low Health, Stamina, and Spirit, especially if Adam is struggling with block, parry, or Force Palm use.
- Advises delaying skills that can be learned through Watch and Learn until observation sources are checked.
- Allows a small number of active skills if Adam is comfortable defensively and wants a specific playstyle.
- Frames the answer as a priority plan, not a universal solved build.

**What a good answer avoids:**
- Pretending all guides agree on one exact early build.
- Ignoring observation-marked skills.
- Recommending a max-damage glass cannon to a player struggling with fundamentals.

**Difficulty:** Medium
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q22. Comparison and synthesis — best_money_method

**Question:**
Is Duo really the best money farm, or should I just sell recipes, run archery contests, and do requests?

**What a good answer contains:**
- Explicitly says sources disagree because some rank gambling highest while safer guides emphasize recipes, contests, requests, or normal loot flow.
- Explains that Duo can be fast but requires understanding hand rankings, buy-ins, risk control, and possibly controversial save-scumming.
- Says selling recipes is safe only after the recipe has been read or learned.
- Notes that archery contests test speed and accuracy and can be tied to challenges such as Hawkeye.
- Recommends based on Adam's risk tolerance and current Silver rather than declaring one route always best.

**What a good answer avoids:**
- Recommending gambling to a broke player without buy-in risk context.
- Telling Adam to sell unread recipes.
- Hiding source disagreement about money-per-hour methods.

**Difficulty:** Hard
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q23. Comparison and synthesis — damiane_oongka_value_after_patch

**Question:**
Are Damiane and Oongka still side characters I can ignore, or did the patches make them worth building?

**What a good answer contains:**
- Explicitly distinguishes launch-era advice from post-1.03 advice.
- Notes that Patch 1.03 added Axiom Force, Nature's Snare, and related open-world abilities for Damiane and Oongka.
- Mentions improvements to Damiane's Shield Toss and Oongka's Scatter Shot matching Kliff's Force Palm effect.
- Advises checking whether Adam needs their specific utility before spending scarce materials.
- Flags that older guides may undervalue them if written before the April 11 patch.

**What a good answer avoids:**
- Saying patches did not affect Damiane or Oongka.
- Declaring both mandatory without considering Adam's materials and playstyle.
- Inventing unrelated character buffs not present in patch notes.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q24. Comparison and synthesis — observation_source_disagreement

**Question:**
One source says Watch and Learn skills are free forever and another says I still spend an Abyss Artifact; which answer should the Companion give me?

**What a good answer contains:**
- Explicitly identifies this as a source conflict the Companion should not flatten.
- Summarizes both positions: free permanent observation unlocks versus observed techniques requiring an Abyss Artifact to lock in.
- Says the answer should cite or name the corpus atoms behind each position once available.
- Recommends conservative play: avoid spending on observable skills until Adam verifies the current in-game prompt or the corpus has a trusted current source.
- Explains why the distinction matters for respec planning and Abyss Artifact scarcity.

**What a good answer avoids:**
- Choosing one side with no caveat or provenance.
- Accusing Adam of misreading the mechanic when sources are actually inconsistent.
- Inventing a third mechanic to reconcile the conflict.

**Difficulty:** Hard
**Substrate capability tested:** SUB-003 librarian filing + Companion synthesis

### Q25. Comparison and synthesis — storage_advice_staleness

**Question:**
Why do older guides say storage is painful, but newer posts talk like Howling Hill storage fixed it?

**What a good answer contains:**
- Explains that Patch 1.00.03 added item storage at Howling Hill Camp and improved early storage pressure.
- Distinguishes Private Storage from inventory expansion bags and the supply chest.
- Notes that some launch advice used vendor repurchase workarounds before storage was added.
- Mentions that Patch 1.04 added inventory category tabs, with similar tabs for private storage planned near-term.
- Advises checking article dates and patch version when applying storage advice.

**What a good answer avoids:**
- Treating all storage advice as equally current.
- Calling Private Storage a bag upgrade.
- Saying the vendor repurchase workaround is still the primary long-term storage plan.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q26. Patch awareness — patch_10003_food_storage

**Question:**
What changed in Patch 1.00.03 that matters if I'm still in the early chapters?

**What a good answer contains:**
- Gives the patch date as March 23, 2026, with the revised notes dated March 24, 2026.
- Says Health restored from food and items was increased.
- Says item storage was added at Howling Hill Camp.
- Mentions control improvements for gamepad and keyboard/mouse.
- Frames the changes as especially relevant to early survival, boss prep, and inventory management.

**What a good answer avoids:**
- Mixing 1.00.03 changes with 1.03 or 1.04 without labels.
- Saying difficulty settings were added in 1.00.03.
- Ignoring food healing when answering an early-chapter survival question.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval

### Q27. Patch awareness — patch_101_mounts_controls

**Question:**
Did the 1.01 update add anything practical, or was it just bug fixes?

**What a good answer contains:**
- Identifies Patch 1.01.00 as the March 29, 2026 update.
- Says it added five summonable mounts obtainable after certain conditions.
- Mentions improved loading times for fast travel and revival.
- Mentions continued control improvements and stamina or movement feel changes where supported by the source.
- Avoids listing spoiler-sensitive mount details unless Adam explicitly asks.

**What a good answer avoids:**
- Calling 1.01 only a bug-fix patch.
- Listing boss-related mount names when Adam asks only whether the patch was practical.
- Confusing 1.01 with the later difficulty-settings patch.

**Difficulty:** Easy
**Substrate capability tested:** SUB-004 retrieval

### Q28. Patch awareness — patch_103_character_skills

**Question:**
I'm on Patch 1.03; what changed for Damiane and Oongka that affects exploration?

**What a good answer contains:**
- Gives Patch 1.03.00 as the April 11, 2026 update.
- Says Damiane and Oongka received more abilities useful for open-world gameplay.
- Names Axiom Force and Nature's Snare as added for Damiane and Oongka.
- Says Damiane's Shield Toss and Oongka's Scatter Shot were improved to have the same effect as Kliff's Force Palm.
- Mentions changed inputs for Damiane's Skystep and Oongka's Vertical Flight.

**What a good answer avoids:**
- Saying only Kliff received new traversal or utility changes.
- Inventing story unlocks tied to these patch notes.
- Confusing 1.03 with the 1.04 inventory category tabs.

**Difficulty:** Medium
**Substrate capability tested:** SUB-004 retrieval

### Q29. Patch awareness — patch_104_difficulty_inventory

**Question:**
On the latest April patch, do I finally have difficulty options and better inventory sorting?

**What a good answer contains:**
- Identifies Patch 1.04.00 as the April 22, 2026 update.
- Says the patch added game difficulty settings.
- Says it added new category tabs for inventory.
- Lists the inventory categories as All, Documents, Equipment, Food, Materials, and Others.
- Notes that private storage category tabs were described as coming in the near future rather than necessarily live at the same moment.

**What a good answer avoids:**
- Saying difficulty settings existed at launch.
- Treating private storage tabs as already live if the patch note only says near future.
- Omitting the date or patch version when answering a freshness question.

**Difficulty:** Hard
**Substrate capability tested:** SUB-004 retrieval + Companion synthesis

### Q30. Patch awareness — stale_boss_advice

**Question:**
If a boss guide was written at launch, what should the Companion check before trusting its advice today?

**What a good answer contains:**
- Tells the Companion to compare the guide date against patches 1.00.03, 1.01, 1.03, and 1.04 where relevant.
- Checks whether food healing, controls, difficulty settings, character abilities, or traversal changes affect the advice.
- Distinguishes encounter-specific mechanics from patch-sensitive player tools.
- Requires surfacing uncertainty if the corpus has only stale launch-week boss guidance.
- Advises citing the freshest trusted atom when giving current boss tactics.

**What a good answer avoids:**
- Treating all launch guides as current without patch checks.
- Inventing boss nerfs or buffs not supported by patch notes.
- Answering with generic "practice more" advice instead of freshness discipline.

**Difficulty:** Hard
**Substrate capability tested:** SUB-002 staging + Companion synthesis

## Question State Conventions

When a question requires character-state context, the state is embedded directly in the question text in the way Adam would naturally type it during play. This eval does not define a separate state schema, because the Companion should parse practical state from natural language rather than require Adam to fill out a form.

State-bearing questions may include chapter, level, party access, camp tier, current boss, inventory pressure, artifact count, gear, patch version, or resource constraints. The eval grader checks whether the answer respects that stated state. If Adam says he is in Chapter 2, an answer that assumes Chapter 4 vendors or late-region access fails even if the underlying fact is true somewhere else in the game.

## Grading Rubric

**Pass:** The answer contains all listed elements in "What a good answer contains" and avoids every listed failure mode in "What a good answer avoids."

**Partial:** The answer includes most contains-elements and has no avoids-violations, but misses one or more specific elements that would matter during play.

**Fail:** The answer commits any avoids-violation, includes fewer than half of the contains-elements, or hallucinates any fact. A single fabricated NPC, wrong location, nonexistent item, invented mechanic, stale patch claim, or unsupported story detail fails the question regardless of how polished the rest of the answer is.

## Versioning

This file is v1.0 of the agentbrand.fit Crimson Desert Companion substrate eval. Future versions add questions; questions are never deleted.

When the corpus expands beyond Crimson Desert, this file forks into per-domain eval files. agentbrand.fit keeps the same eval shape across domains so grading remains comparable while the domain content changes.

## Handoff Note for Claude Code

This file is a non-runtime artifact produced by Codex. When the Companion runtime is built and wired against the agentbrand.fit corpus, Claude Code will reference this file as the eval rubric.

No runtime instructions live in this file. Integration is governor-authorized separately.
