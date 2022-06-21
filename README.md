**This is implemented by [Verite](https://github.com/centrehq/verite).**

# Demo Issuer

This is a simple example of how to issue a credential to a self-custodied identity wallet.

The page first prompts a compatible mobile wallet to scan a QR code. The data encoded includes a JWT to help tie the mobile wallet to the current authenticated browser session.

The returned [Credential Manifest](https://identity.foundation/credential-manifest/) can be processed and show the user what is being requested.

Finally, we use [Presentation Exchange](https://identity.foundation/presentation-exchange) to request the credential.

## Getting Started

### Installation

```sh
npm install
```

### Starting the app

```sh
npm run dev
```

### Folder Structure

This app is built with [next.js](https://nextjs.org/). Next.js is a development framework for React which has automatic routing (based on folder structure), server-side rendering, and other optimizations. Next.js maintains a folder structure which maps directly to app routes. For example, the file `pages/hello.tsx` would map to the route `/hello`.

The folder structure is as follows:

```
pages/       Contains top-level React components which are treated as "pages" mapped to an HTTP route
pages/api    Contains Server-Side API routes
```

The root `App` React component is located in `pages/_app.tsx`. This demo contains only a single page, located at `pages/index.tsx`.

You can read more about the Next.js folder structure in [their documentation](https://nextjs.org/docs/basic-features/pages).

## Issuance to a hosted wallet

Issuance to a hosted wallet would look the same, but the mechanism for sharing the `challengeTokenUrl` would be different. In this demo, we have the mobile wallet scan the QR Code. In a hosted solution, we might have the user copy-paste the data, which is otherwise unweildy between devices. Then, the hosted wallet could behave just as a mobile wallet and continue requesting the credential.

## Issuance to metamask

Issuance to metamask, or some browser-based extension wallet, is very similar. Since the issuing service is likely a web application, it could interact with MM as if it were a dApp. Additionally, MM being a wallet, it already has a set of keypairs that can be used to identify the user, however it could create its own for holding identity.
