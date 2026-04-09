# You probably don't need NgRx

Slidev deck for a 25 minute talk about Angular state management.

The core message of the talk is simple:

> NgRx is valuable, but it should be a deliberate trade-off, not the default answer to every kind of state.

The presentation argues for clearer state boundaries first:

- keep local state local
- keep feature state inside the feature
- do not confuse server state with app state
- reach for NgRx when the coordination cost is real

## Talk flow

The current deck is structured around:

1. why teams default to NgRx
2. a concrete search/filter example
3. the different kinds of state
4. smaller defaults available in modern Angular
5. when NgRx earns its cost
6. a more complex checkout example
7. a quick decision framework

## Development

Install dependencies:

```bash
pnpm install
```

Start the deck locally:

```bash
pnpm dev
```

Slidev will open the presentation in your browser. If it does not open automatically, check the local URL shown in the terminal.

## Scripts

- `pnpm dev` starts the Slidev dev server
- `pnpm build` builds the static presentation into `dist/`
- `pnpm build:github-pages` builds the presentation for `https://thomastoledo.github.io/you-probably-dont-need-ngrx/`
- `pnpm export` exports the slides using Slidev's export workflow

## Deploy to GitHub Pages

The Slidev build uses root-relative asset URLs by default, for example `/assets/...`.
That works when the presentation is hosted at the site root, but it breaks when the deck
is copied into a subfolder of a Jekyll blog such as `/you-probably-dont-need-ngrx/`.

Build the deck for your GitHub Pages subpath:

```bash
pnpm build:github-pages
```

Then copy the contents of `dist-gh-pages/` into the `you-probably-dont-need-ngrx/`
folder of your `thomastoledo.github.io` repository and push the change.

The final URL should be:

```text
https://thomastoledo.github.io/you-probably-dont-need-ngrx/
```

If you want to publish the talk under a different folder, change the `--base` value in
`package.json` so it matches the public URL exactly.

## Project files

- `slides.md` is the current working deck
- `slides.early-example-backup.md` is a backup variant of the deck
- `public/pptx-assets/` contains images used in the presentation
- `dist/` contains the generated output

## Tech

- [Slidev](https://sli.dev/)
- `@slidev/theme-seriph`
- Vue 3
- pnpm
