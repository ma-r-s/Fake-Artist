# Fake Artist

A digital companion for the party game **A Fake Artist Goes to New York**, by
Oink Games. Use it on a single shared device passed around the table, or as a
local-network host with phones for each player.

**Live:** [fake-artist.ma-r-s.com](https://fake-artist.ma-r-s.com)

## How the game works

- One topic, one secret answer (e.g. topic: _ANIMAL_, answer: _Pig_).
- Every player except one ("the question master") learns the answer.
- One of the players who learns the answer is secretly the **Fake Artist**.
  The Fake Artist sees the topic but not the answer.
- Players take turns drawing exactly one short line on a shared canvas, two
  rounds total.
- After drawing, players vote on who they think the Fake Artist is.
- The Fake Artist wins if they survive the vote and can guess the answer.
  Everyone else wins by identifying the Fake.

This app handles topic selection, secret distribution, the drawing surface,
voting, and reveal — all of the bookkeeping the analog version makes you do
manually with paper.

## Tech stack

- [SvelteKit](https://svelte.dev/) 1 with Svelte 3
- [Threlte](https://threlte.xyz/) + Rapier for any 3D / physics elements
- [Tailwind CSS](https://tailwindcss.com/) with [DaisyUI](https://daisyui.com/)
  (cyberpunk theme)
- [Capacitor](https://capacitorjs.com/) configuration for Android / iOS
- [Tauri](https://tauri.app/) configuration for desktop
- Deployed on [Vercel](https://vercel.com/) via `adapter-static`

## Local development

```bash
npm install --legacy-peer-deps
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173).

## Build

```bash
npm run build       # static site build into ./build
npm run preview     # preview locally
```

## Routes

```
src/routes/
├── +page.svelte         # Landing / new-game setup
├── topics/+page.svelte  # Topic selection
├── draw/+page.svelte    # Drawing canvas
├── show/+page.svelte    # Display the completed canvas
├── vote/+page.svelte    # Voting
└── reveal/+page.svelte  # Final reveal
```

## Acknowledgments

A Fake Artist Goes to New York is © Oink Games. This app is a non-commercial
companion tool. Buy the physical game from Oink Games.

## License

MIT for the code in this repository.
