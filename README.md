# Integrating Algolia SearchBox with Catalyst

You can integrate Algolia search into Catalyst storefronts to help shoppers search all products, categories, and more.

This guide demonstrates a basic integration and provides example code for global product search that you can add to the core code of your Catalyst storefront, or to `apps/core` in the Catalyst [monorepo](https://github.com/bigcommerce/catalyst/blob/main/docs/monorepo.md).

## Demo site

For a working demo of an Algolia integration with Catalyst, see the following example:

```shell copy
https://catalyst-with-algolia.vercel.app/
```

## Prerequisites

To follow this guide, you need the following:

- Node.js 20+
- A Node.js package manager, such as `npm`, `pnpm`, or `yarn`
- Working knowledge of [Next.js](https://nextjs.org)
- An [Algolia account](https://dashboard.algolia.com/users/sign_up)
- A [BigCommerce store](https://www.bigcommerce.com/start-your-trial/) or [sandbox store](https://start.bigcommerce.com/developer-sandbox/)

## Deploy Your Own

1. First, click the deploy button below to create a new Vercel project, add the BigCommerce integration, and return here for next steps (**Note:** You may have already gotten this far; if so, you can skip this first step.):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fmatthewvolk%2Fcatalyst-algolia&env=NEXT_PUBLIC_ALGOLIA_APP_ID,NEXT_PUBLIC_ALGOLIA_APP_KEY,NEXT_PUBLIC_ALGOLIA_INDEXNAME&envDescription=Click%20%22Learn%20More%22%20for%20instructions%20on%20how%20to%20obtain%20the%20Algolia%20environment%20variables%20above.&envLink=https%3A%2F%2Fgithub.com%2Fmatthewvolk%2Fcatalyst-algolia%3Ftab%3Dreadme-ov-file%23deploy-your-own&project-name=catalyst-with-algolia&repository-name=catalyst-with-algolia&integration-ids=oac_nsrwzogJLEFglVwt2060kB0y&external-id=catalyst)

2. If you do not yet have one, create a free [Algolia account](https://dashboard.algolia.com/users/sign_up).

3. At the top of your [Algolia dashboard](https://dashboard.algolia.com), create an Algolia app that you intend to associate exclusively with your Catalyst storefront channel.

4. Install the [BigCommerce Algolia app](https://www.bigcommerce.com/apps/algolia-search-discovery/) and associate it with your Catalyst channel. Detailed instructions on how to complete this can be found in the [Alogolia for BigCommerce documentation](https://www.algolia.com/doc/integration/bigcommerce/get-started/installation/#connect-bigcommerce-with-algolia).

> [!WARNING]
> You may run into indexing failures with the default BigCommerce sample product data if you chose Product level indexing, specifically with Product ID 77. If this occurs, you should be able to delete the product "[Sample] Fog Linen Chambray Towel - Beige Stripe" and trigger a reindex to proceed.

5. At this point, you should have enough configured to enter the following environment variables back in the Vercel new project creation screen:

| Environment variable            | Value                                                                                                                                                                                                                                                                                                                                                                                          |
| :------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `NEXT_PUBLIC_ALGOLIA_APP_ID`    | Your Algolia app ID (can be found in your BigCommerce Control Panel under Apps > Algolia AI Search & Discovery > Sources > the string inside parenthesis next to your index name. By default, the index name is BigCommerce.)                                                                                                                                                                  |
| `NEXT_PUBLIC_ALGOLIA_APP_KEY`   | Your Algolia Search Only API key. You can find this value in the **API keys > All API keys** section of your [Algolia account dashboard](https://dashboard.algolia.com/account/api-keys/restricted). If this is your first time using the new Algolia app, visit the **Search > Index** section of the Algolia dashboard and click the **Refresh index** button to generate your search index. |
| `NEXT_PUBLIC_ALGOLIA_INDEXNAME` | Your Algolia Search Index name. By Defualt the BigCommerce Algolia app uses the index name Bigcommerce.                                                                                                                                                                                                                                                                                        |

6. Enter values for each variable according to your own configuration, and click "Deploy" to deploy your Algolia-powered Catalyst storefront on Vercel.
