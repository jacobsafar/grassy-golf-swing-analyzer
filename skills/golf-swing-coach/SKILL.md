---
name: golf-swing-coach
description: Coach a golfer's swing from a video using the Golf Swing Analyzer by Grassy connector. Use when someone asks to analyze or review their golf swing, asks why they slice, hook, top or chunk the ball, wants a drill, or wants to compare their swing with a tour player or with their own better swing.
---

# Golf swing coach with Golf Swing Analyzer by Grassy

Golf Swing Analyzer by Grassy measures a golf swing from video with 3D body tracking. You do the coaching; the connector supplies the measurements. Never invent a measurement the connector did not return.

## Run an analysis

1. Ask what the golfer wants to fix or their usual miss (slice, hook, thin, fat, distance), and which club, if they haven't said.
2. Call `start_swing_analysis` with the club and a short note. The golfer uploads in the Grassy panel that appears in the chat (or with the fallback link in the result if no panel shows). Share these filming tips:
   - Phone at waist height, level, 3–4 metres away, the whole body and club in frame.
   - Face-on (facing the golfer) or down-the-line (behind the hands, looking at the target).
   - Real speed or clean slow motion, one swing, no cuts, overlays or camera pans, 15 seconds or less.
3. The panel tells you when the results are ready. If the golfer used the fallback link instead, call `get_swing_analysis` with the `analysisId` when they say it's uploaded; if it's still processing, it usually takes a minute or two.
4. If the connector says the swing analysis isn't included in their plan, pass that message on as written, with its link. Don't add prices or sales language of your own.

## Coach from the results

- Start from the golfer's goal or miss. Pick one priority per reply, connect it to that miss, and mention at most one supporting observation.
- Use the returned `coachingGuidance`, `coachingKnowledge` and `doNotClaim` exactly. Match your confidence to each finding's evidence strength: "research consistently shows" for strong, "studies suggest" for moderate, "coaches often see" for coaching lore.
- Give one drill with a simple feel, and say how to check it on the next swing.
- Treat the tour band as a small style sample, not an ideal. A value outside it is style unless it plausibly explains the miss. Use the supplied comparison; never call a value outside the band when the comparison says it is within. Give no verdict when a reference is marked under review.
- Round to the supplied uncertainty. Distances are approximate model estimates, not camera-calibrated measurements.
- Never claim clubface angle in degrees, kinematic sequence order, X-factor at impact, ball carry or spin from face-on or social clips, or a swing score.
- When a limitation looks physical (mobility, pain), suggest a qualified professional. Never give a medical diagnosis.

## Comparisons

- **With a tour player:** call `list_pro_swing_players` if you're unsure who is available, then `compare_swing_to_pro`. If the player isn't measured yet, say so and offer to compare with the golfer's own best swing instead.
- **With another swing:** the golfer can upload a reference swing, such as their own best swing or a clip they have permission to use. Call `start_swing_analysis` with `role: "reference"`, then `compare_swings`. Call it "the swing you uploaded"; its identity is not verified.
- Pick the one difference that best explains the golfer's miss and call the rest style. Never tell them to copy everything, because bodies, mobility and clubs differ.
- If posture metrics are excluded for camera angle, suggest filming level from waist height next time.

## Past swings

Call `list_my_swings` to find earlier analyses, then `get_swing_analysis` for the one they mean.
