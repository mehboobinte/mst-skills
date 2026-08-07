---
name: google-flow
description: Write production-ready Google Flow / Veo video prompts and matching Urdu voice-over scripts for Mehboob Steel Traders (and any business video). Use this skill whenever the user mentions Google Flow, Flow, Veo, Veo 3, Veo 3.1, "AI video", "video banao", a Reel / Short / YouTube clip, a product or godown or delivery-truck video, wants to extend or continue an existing AI clip, needs scene continuity across shots, needs an Urdu narration script for a video, or asks for ad creative in video form — even if they never say the word "prompt". Also use it when they upload godown/product/truck photos and want a video made from them.
---

# Google Flow / Veo Video Prompts

Google Flow (labs.google/fx/tools/flow) is Google's AI filmmaking workspace. It runs
Veo for video, Imagen/Nano Banana for stills, and Gemini for prompt help. This skill
turns a rough business idea into prompts that actually work in Flow, plus the Urdu
narration to lay over them.

## Non-negotiable facts about the tool

Get these wrong and the output is wasted credits:

- **One generation = ~8 seconds max.** Any video longer than that is built as a chain
  of clips using **Extend** (Flow's scene builder), never as one giant prompt.
- **4–6 seconds** for complex action (hands working, machinery, many moving people);
  **8 seconds** for slow, atmospheric or single-move shots. Long action in 8s = warped
  limbs and melting objects.
- **Aspect ratio is chosen in Flow's settings, not in the prompt.** 9:16 for
  Reels/Shorts/WhatsApp status, 16:9 for YouTube and the website.
- **Veo does not reliably render text**, and it renders **Urdu/Arabic script as
  gibberish, always**. Never ask for Urdu text, signboards, or captions inside the
  video. Even English brand text and phone numbers come out misspelled roughly half
  the time — plan to add them in editing (Canva/CapCut) instead. If a prompt does ask
  for on-screen English text, tell the user to check every character before publishing.
- **Native audio** (Veo 3 / 3.1) is good for ambient sound and English dialogue. It is
  **not good for Urdu dialogue**. Default plan: generate with ambient sound only, then
  record or synthesise the Urdu voice-over separately and lay it on top.
- **Ingredients** = up to 3 reference images per prompt (a character, a product, a
  truck, a style reference) that keep the look consistent across clips. Uploading the
  user's own godown/product photos as ingredients is almost always better than
  describing them in words.
- **Frames to Video**: give a start frame (and optionally an end frame) to control
  exactly where a shot begins and ends — the reliable way to make two clips join.
- 1080p when the clip is final; 720p while iterating to save credits/time.

## Workflow

1. **Get the brief straight.** Purpose (ad / brand trust / how-we-work / product
   feature), platform + aspect ratio, total length, whether real photos exist, and
   whether narration is wanted. Ask only what's missing — don't re-ask what the
   conversation already says.
2. **Break the length into 8-second beats.** Write out the shot list first, one line
   per beat, and show it to the user before writing full prompts. A 20-second video is
   3 beats; a 30-second video is 4. Getting sign-off on the beats is cheaper than
   regenerating clips.
3. **Write the prompts in English**, one per beat, using the structure below. Veo's
   prompt adherence is tuned for English; writing the prompt in Urdu degrades output.
   (Explain the prompt to the user in Urdu — just don't feed Urdu to Veo.)
4. **Add a continuity block** to every prompt after the first (see below). This is the
   single most common failure: the worker's clothes change, the truck changes colour,
   the light jumps from morning to evening.
5. **Write the Urdu narration** separately: word count matched to duration
   (~2.2 Urdu words per second of finished video — 20s ≈ 40–45 words). Keep sentences
   short enough to breathe between shots.
6. **Deliver** the beat list, the copy-paste prompts, the narration script, and the
   Flow settings to select (model, aspect ratio, resolution, audio on/off).

## Prompt structure

Every prompt is one flowing paragraph — not a bullet list, not key:value pairs. Cover
these elements in roughly this order, and drop any that don't matter for the shot:

1. **Shot type + camera move** — "slow dolly-in", "low-angle tracking shot",
   "handheld medium shot", "static wide", "overhead crane shot descending"
2. **Subject, described concretely** — age, build, clothing, what the hands are doing
3. **Action, one action only** — one verb per clip; two actions in 8 seconds is a mess
4. **Environment** — location, depth cues, background activity
5. **Light + time of day** — "golden hour, warm side light, dust in the air",
   "overcast midday, flat light", "bare bulb overhead, hard shadows"
6. **Lens + film look** — "shot on 35mm, shallow depth of field, natural colour grade,
   slight film grain"
7. **Audio line** (if audio on) — "Audio: ambient market noise, distant traffic,
   metal pipes clanking. No music, no dialogue."
8. **Negatives** — what to keep out (see below)

### Negatives worth adding almost every time

`no on-screen text, no captions, no logos, no watermark, no glossy CGI look, no
plastic-looking skin, no slow-motion, no lens flares, natural imperfect surfaces,
no crowd of identical faces`

For MST specifically also add: `pipes must look like real mill-finish steel with
surface marks and dust, not chrome or mirror-polished`. Veo's default instinct is to
make everything showroom-shiny, which reads as fake to a steel buyer.

### Continuity block (for clip 2 onward)

Repeat the *whole* description, don't refer back — Veo has no memory of the previous
clip. Then append:

> Continuity: same man as previous shot — mid-30s, grey shalwar kameez, blue hard hat,
> dusty hands; same location, same warm late-afternoon light and camera height; same
> colour grade. Continue the action from where it left off.

Better still, use the last frame of the previous clip as the start frame via
**Frames to Video**, and tell the user to do that.

## Reference files

- **`references/mst-recipes.md`** — Ready-made prompt sets for Mehboob Steel Traders:
  daily rate list promo, godown process explainer, delivery truck, product close-ups,
  customer-trust shots, plus matching Urdu narration. Read this whenever the video is
  for MST or any steel/pipe/wholesale business.
- **`references/flow-mechanics.md`** — Step-by-step Flow interface workflow: ingredients,
  scene builder, extend, frames-to-video, credits discipline, export and what to fix in
  editing afterwards. Read this when the user is unsure *how* to drive Flow itself, not
  just what to type.

## Output format

Give the user, in this order:

1. **بیٹ لسٹ** — numbered shots with durations, in Urdu, one line each.
2. **Flow settings** — model, aspect ratio, resolution, audio on/off.
3. **Prompts** — each in its own fenced code block, labelled `Clip 1`, `Clip 2`…, in
   English, ready to copy. Never mix Urdu into the prompt block.
4. **اردو نریشن** — the voice-over script with per-shot timing.
5. **بعد کا کام** — what to add in editing (brand name, phone number, Urdu captions,
   music) with a note that these must not be asked of Veo.

Explain and discuss everything in Urdu script; keep only the prompts themselves in
English.

## Common failures and the fix

| Symptom | Cause | Fix |
|---|---|---|
| Text/phone number garbled | Veo can't render text reliably | Remove from prompt; add in Canva/CapCut |
| Urdu writing looks like scribble | Veo cannot do Urdu script | Never request it; overlay in editing |
| Person's face/clothes change between clips | No continuity block | Repeat full description + use last frame as start frame |
| Pipes look like chrome toys | Veo's default polish | Add the mill-finish/dust negative |
| Hands melt, count wrong | Too much action in 8s | Cut to 4–6s, one action per clip |
| Dialogue doesn't appear | Line too long for 8s clip | Shorten drastically or do VO separately |
| Every clip feels different | Style drifting | Reuse the same lens/light/grade sentence verbatim in all prompts, or use a style ingredient |
