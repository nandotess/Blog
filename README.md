# Blog

## Production Site (frontend)

- [blog-nandotess.vercel.app](https://blog-nandotess.vercel.app/)

## Production CMS (backend)

- [admin-nandotess.vercel.app](https://admin-nandotess.vercel.app/)

## Database Project

- Repository: https://github.com/nandotess/blog-database
- [Sanity.io](https://www.sanity.io/) (headless database)
- [Node.js](https://www.sanity.io/docs/content-modelling) (content modelling)

## Backend Project (CMS)

- Repository: https://github.com/nandotess/blog-backend
- [Vercel](https://vercel.com/) (cloud hosting)
- [Node.js](https://www.sanity.io/docs/content-modelling) (communication with the database and SSR)
- [React](https://reactjs.org/)
- [Next.js](https://nextjs.org/) (React Framework)
  - [GROQ](https://www.sanity.io/docs/groq) (communication with the database - GET)
  - [REST API](https://www.sanity.io/docs/http-api) (communication with the database - POST, PUT and DELETE)
  - [SSR](https://vercel.com/blog/nextjs-server-side-rendering-vs-static-generation) (Server Side Rendering)
- [Material-UI](https://material-ui.com/) (React UI framework)

## Frontend Project (Blog)

- Repository: https://github.com/nandotess/blog-frontend
- [Vercel](https://vercel.com/) (cloud hosting)
- [React](https://reactjs.org/)
- [Next.js](https://nextjs.org/) (React Framework)
  - [GROQ](https://www.sanity.io/docs/groq) (communication with the database - GET)
  - [SSG](https://vercel.com/blog/nextjs-server-side-rendering-vs-static-generation) (Incremental Static Generation)

## Notes

- The main benefit to having the 3 applications running in different servers with different URLs is the possibility to restrict access (improving security). On the backend application (CMS), we could restrict access to it using a VPN, for example. For now, we are using SSO (Google). On the frontend application (Site/Blog), the database is currently only accessible on the server, so the URL and any other sensitive data are already hidden from the final user.

- [Sanity.io](https://www.sanity.io/) is used as the database source for a few reasons:

  - It's a cloud solution with a generous free tier.
  - Easy to create new datasets and models with no UI, only using JavaScript and terminal.
  - They offer a query language (GROQ) similar to GraphQL but with more resources. The main benefit from GROQ (as well as GraphQL) is the possibility to get data with relationships in one single query (different from the REST API specification).
  - All the images stored in their servers have CDN ready to go.
  - It's possible to have custom tokens for each application. Currently, there is a token for the site/blog (READ) and a token for the CSM (READ + WRITE).

- [Next.js](https://nextjs.org/) + [Vercel](https://vercel.com/) was the combination chosen for the frontend application (Site/Blog), among other things, because it delivers a powerful combination of Server Side Rendering and Static Generation. With the [Incremental Static Generation](https://vercel.com/blog/nextjs-server-side-rendering-vs-static-generation), it's possible to have the static pages generated with a revalidation of the content pretty generous (the current configuration is set to one minute, **that means all the content updated on the CMS will be live to the user, not more than 1 minute later**). On top of that, all this static content is stored in Vercel's CDN.

- [Next.js](https://nextjs.org/) + [Vercel](https://vercel.com/) + [Material-UI](https://material-ui.com/) was the combination chosen for the backend application (CMS), among other things, because it delivers a powerful set of components ready to go. **Authentication**, **Grids**, **Forms**, ... there are many resources that make the creation of a CRUD system easy, so we can focus only on the business rules and not standards already defined by the industry.
