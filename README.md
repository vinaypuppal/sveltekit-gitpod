# Sveltekit App Template With Gitpod Setup

Everything you need to build a Sveltekut project in [Gitpod](https://www.gitpod.io/);

## Special config for Gitpod to make HMR work

Sveltekit needs to know how to reach the HMR endpoint. To configure that we need to do two things in our config:

1. Set an environment variable

```
 export WS_URL=$(gp url 24678 | sed 's/https\?:\/\///')
```

2. Configure the env value in `svelte.config.js`

```js
		kit: {
		// ... other config
		vite: {
            // ... other config
			server: {
				hmr: {
					host: process.env.WS_URL,
					clientPort: process.env.WS_URL ? 443 : null
				}
			}
		}
	}
```

This will set HMR URL with the workspace url of `24678` (default port for HMR).

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.
