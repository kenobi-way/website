# Project Guide & Plan

## Dev environment + tools
   - [Cursor IDE](https://www.cursor.com/)
      - built in terminal is nice... need to install brew, npm etc. again here
   - [Warp](https://www.warp.dev/) terminal

## SvelteKit

https://svelte.dev/docs/kit/introduction

   - with [client side routing](https://svelte.dev/docs/kit/glossary#Routing), [service workers](https://svelte.dev/docs/kit/service-workers) for offline support, [preloading](https://svelte.dev/docs/kit/link-options#data-sveltekit-preload-data) pages for faster nav & responsiveness, [configurable page rendering](https://svelte.dev/docs/kit/link-options#data-sveltekit-preload-data) with server-side / client-side / pre-rendered options, and instant code updates via HMR (hot module replacement) with Vite
   - [`sv`](https://github.com/sveltejs/cli) CLI
   - `npm` for updates & dependencies, `eslint` is the standard linter

#### dev mode
```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

#### build prod
```bash
npm run build

# preview production build
npm run preview
```

## Vite

built into SveltKit projects by default

## Tailwind

[install](https://tailwindcss.com/docs/installation/framework-guides/sveltekit) Tailwind (with [JIT mode](https://v2.tailwindcss.com/docs/just-in-time-mode))

## Vercel

https://vercel.com/nates-projects-f92fca23

Deploy as a Vercel serverless app, prerendered with static site generation—see the [project types](https://svelte.dev/docs/kit/project-types)—with [automatic deployment](https://vercel.com/docs/git/vercel-for-github) on any github commit. Vercel features & optimizations to consider:
* [ISR](https://vercel.com/docs/frameworks/sveltekit#incremental-static-regeneration-isr) - Incremental Site Regeneration allows you to create or update content without redeploying your site, for better performance, improved security, and faster build times (sveltekit [docs](https://svelte.dev/docs/kit/adapter-vercel)
* [Deployment Configuration](https://svelte.dev/docs/kit/adapter-vercel#Deployment-configuration) - deploy as Edge or Serverless [Functions](https://vercel.com/docs/functions)
* [Image Optimization](https://vercel.com/docs/image-optimization/quickstart)
* [Fluid Compute](https://vercel.com/docs/functions/fluid-compute) - blend of serverless flexibility and server-like capabilities
* [Skew Protection](https://vercel.com/docs/skew-protection) - ensures that the client and server stay in sync

* use a faster/alternative package manager - pnpm, bun, yarn
* turn on caching

------

1. stand up a simple “hello world” static website locally
1. get the starter website into a github repo
    - and get on a feature branch
1. test and refine the local dev/test loop
1. test the production deploy workflow (CI/CD)
    - build / lint / minify the site, test, deploy to Vercel so that the site is lift
1. build the actual website
    - style sheet, fonts, visual language etc.
    - nav system / information architecture
    - page structure/layout with extensible content
    - collect interest via a very simple form — via FormSubmit or a simple serverless backend (could email me or add to a google sheet)
1. redirect the domain name I have reserved to the new site
1. setup analytics (vercel? google analytics?)
   - Vercel Web Analytics
1. setup site monitoring / alerts
1. to consider
   - homebrew, node / npm, bash, eslint, prettier
    - [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview#install-and-authenticate) ?
    - https://x.com/elie2222/status/1907768796900897077 - how to code with Cursor (maintain a project plan that the AI can read + update)    
   - maintain a shell script to update/recreate the environment at will (idempotent)

## GIT

Generate SSH key -- by default, the key will be saved in `~/.ssh/id_rsa`.

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

Add SSH Key to GitHub
* Go to GitHub SSH settings.
* Copy the contents of your public key (`~/.ssh/id_rsa.pub`).
* Add the key to GitHub by clicking New SSH key and pasting the contents.

Test SSH Connection

`ssh -T git@github.com`

Install GitHub CLI and sign in -- this actually allows for https rather than ssh access and authorizes via the browser, which seems simpler than using SSH keys... could revisit this for headless use cases, when we want more automation, etc.

```
brew install gh
gh --version

# Login to GitHub
gh auth login
```

Configure git user info.

```
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```
 
After authentication, you'll be able to:
* Clone repositories from your organization:
  * Press Ctrl+Shift+P (or Cmd+Shift+P on Mac)
  * Type "Git: Clone"
  * Enter the organization repo URL: https://github.com/your-org-name/repo-name.git
* Or use the GitHub extension:
  * Click on the GitHub icon in the Activity Bar
  * Browse your organizations and repositories
  * Clone directly from there

## VSCODE + CURSOR



## TAILWIND

## SVELTE

Tutorial: https://svelte.dev/tutorial/svelte/welcome-to-svelte

  * [Runes](https://svelte.dev/blog/runes) - also see https://svelte.dev/docs/svelte/what-are-runes
  * [$state](https://svelte.dev/docs/svelte/$state) - define reactive state... any binding or expression depending on reactive state is updated when the reactive state changes, including any dependent parts of the DOM
  * [$derived](https://svelte.dev/docs/svelte/$derived) - define derived (computed) state
  * [$inspect](https://svelte.dev/docs/svelte/$inspect) - log state changes
  * [$effect](https://svelte.dev/docs/svelte/$effect) - create a side effect for state changes
  * [$props](https://svelte.dev/docs/svelte/$props) - declare component properties

```
<script>
	let name='Nate';
    let str='<strong>!!!</strong>';
	let image='./image.jpg';

    // create a rune for reactive state synced
    // between the DOM and app; runes react to mutations and reassignments
    let count = $state(0);
    function increment() { count += 1; console.log($state.snapshot("count = " + count));}
    $inspect(count);
</script>

<p>Hello {name.toLowerCase()} {@html str}</p>
<img {image} />
<button onclick={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

{#if count > 10}
	<p>{count} is greater than 10</p>
{:else if count > 5}
	<p>{count} is greater than 5</p>	
{:else}
	<p>{count} is between 0 and 5</p>
{/if}

<style> p { font-size: 2em; } </style>
```

## SVELTKIT

Tutorial: https://svelte.dev/tutorial/kit/introducing-sveltekit


## VITE

https://vite.dev/guide/
