A FOOD RESTAURANT AND MARKET STORE E-COMMERCE
USING MEDUSA, NEXT.JS, PAYPAL, PAYSTACK INTEGRATION

Home Page And Landing page
MG food and market

aaa

MG food and market 2

Significant of this project
Food and Food items are one of the best lucrative businesses around the world. They get patronage on a daily basis without being much affected by a country economy because people depend on food for survival.

This gave the avenue to create a food and food products to be sell online, to solve a problem of helping seller sells online and buyers buy online.

In this blog, you will learn how to build a modern e-commerce storefront with Medusa and Next.js, using Paypal and Paystack integration. You will create the store’s backend using Medusa’s headless commerce engine and admin panel, and the store’s frontend with the Next.js framework and Tailwind CSS.

Inspiration behind the application
My inspiration came from a life experience, where people of the world are faced with virtual many challenges that distracts there daily life actives and of those are the issues of easy accessibility to food and food products. Sometimes ago people find it hard to go to the market store or get already made foods, unless they ave to visit restaurants and actual market place but such challenges can be so overwhelmed, imagine coming back from the office and realizing that you have no groceries at home and you need to make food cause you are hungry at that time you can’t have easy means to get a food or groceries.

So to solve such a problem, I got inspired to be innovative, and be part of those solving world problem by creating an application where people can be at the comfort of their home or offices or any place at a particular time and make orders online and get there food and groceries delivered to them at the comfort of their habit.

Overview
Medusa is composed of three different components: the headless backend, the storefront, and the admin dashboard.

It also provides bespoke commerce infrastructure for developers. Its composable commerce engine addresses the challenges of existing ecommerce platforms which APIs offer bad developer experiences, extension capabilities are insufficient, and results are hacky and hard to maintain.

Next.js is a JavaScript open source framework for building superfast and extremely user-friendly frontend websites using React. It is a server-rendered, lightweight, and flexible React framework that requires little or no configuration during usage.

Using Medusa commerce engine to build your online stores gives you the opportunity to work with Medusa Next.js storefront starter, which can be easily installed through CLI commands.

Medusa Next.js storefront is a 100% ready-to-use Medusa storefront template. It comes with all ecommerce storefront features such as product display, featured products, shopping cart, checking out, multiple payment processing, and more.

PayPal is a payment provider used by millions around the world. It allows customers to purchase orders from your website using their PayPal account rather than the need to enter their card details.

As a developer, you can use PayPal’s SDKs and APIs to integrate PayPal as a payment method into your ecommerce store. You can test out the payment method in sandbox mode before going live with it as a payment method.

Paystack is the #1 African payment gateway that helps businesses to accept online payments through their ecommerce stores, websites, and applications. Paystack provides other services such as point-of-sale (PoS), payment through an invoice, and more.

Algolia is a search engine service that allows developers to integrate advanced search functionalities into their websites including typo tolerance, recommended results, and quick responses.

Algolia can be used for a wide range of use cases, including ecommerce websites. By integrating Algolia into your ecommerce website, you can provide your customers with a better user experience and help them find what they’re looking for swifltly.

Through Medusa's flexible plugin system, it is possible to add a search engine to your Medusa backend and storefront using Algolia with just a few steps.

S3 To manage images in Medusa, you need a file service plugin responsible for hosting the images. Without a file service plugin, you will face issues while working with Medusa, such as when uploading images for products.

Medusa provides three different options to handle your file storage.

Prerequisites
To follow through this tutorial, make sure to have:

Node.js and NPM installed on your local machine. You can follow the instructions in this link to fully install Node.js and npm on your local computer.

Git installed locally with a GitHub account. Follow the instructions here to install git, and create a GitHub account here.

PayPal Account with API Secret and Public Key, on the developer dashboard here

Paystack Account with API Secret and Public Key, on the developer dashboard here

S3 Account with API Secret and Public Key here

Why Medusa?
Open source — Medusa is an open-source software that can be used as a commerce backend for your webshop and with a large support community behind it which you can access here.

Headless architecture — Medusa’s headless architecture makes it easy to build with any type of frontend (e.g. next.js, react) and integrate with your favorite CMS, payment, fulfillment solutions, etc.

Multi-market support — Medusa natively supports multiple currencies and allows you to set use local shipping and payment providers for a global setup.

Fully customizable — There extendible architecture makes it easy to customize for any type of advanced use case and makes it easy to build in custom logic and integrations.

Set up Your Food Restaurant and Market Store E-commerce with Medusa
Medusa backend installation and setup using Medusa CLI
Medusa CLI tool can be installed either using npm or yarn, but this tutorial is based on npm. Use the command below to install Medusa CLI:

npm install @medusajs/medusa-cli -g
Then create a new project with the installed CLI

medusa new <mg-food-and-market-store> --seed
mg-food-and-market-store will be your project name, but you can change this to your preferred choice of name.

Change to the preferred name of your project directory.

cd mg-food-and-market-store
Finally, start up the created server.

medusa develop
The server can be accessed at http://localhost:9000.

Installing PayPal Medusa Plugin

In the root of your project, run this command to install Medusa PayPal plugin:

npm install medusa-payment-paypal
Configure the PayPal Plugin

Next, you need to add configurations for your PayPal plugin.

In the .env file add the following new environment variables:

1. PAYPAL_SANDBOX=true
2. PAYPAL_CLIENT_ID=<CLIENT_ID>
3. PAYPAL_CLIENT_SECRET=<CLIENT_SECRET>
4. PAYPAL_AUTH_WEBHOOK_ID=<WEBHOOK_ID>
Where <CLIENT_ID>, <CLIENT_SECRET>, and <WEBHOOK_ID> are the keys you retrieved from the PayPal Developer dashboard as explained in the Prerequisites section.

Notice that during development it’s highly recommended to set PAYPAL_SANDBOX to true and ensure you have sandbox accounts set up in PayPal.

Then, in medusa-config.js, add the PayPal plugin to the plugins array with the configurations necessary:

# medusa-config.js

const plugins = [
  // other plugins...
  {
    resolve: `medusa-payment-paypal`,
    options: {
      sandbox: process.env.PAYPAL_SANDBOX,
      client_id: process.env.PAYPAL_CLIENT_ID,
      client_secret: process.env.PAYPAL_CLIENT_SECRET,
      auth_webhook_id: process.env.PAYPAL_AUTH_WEBHOOK_ID,
    },
  },
]
NOTE On how to setup a PayPal WEBHOOK click here

That’s all you need to install PayPal on your Medusa backend!

Installing Paystack Medusa Plugin

In the root of your project, run this command to install Medusa Paystack plugin:

npm install medusa-payment-paystack
Next, you need to configure your Paystack plugin in your project. To do this, first, add PAYSTACK SECRET KEY to your .env file:

PAYSTACK_SECRET_KEY=example_key_xxxxx
In the above, replace example_key_xxxxx with the secret key gotten from your Paystack API Key.

In medusa-config.js, add the following at the end of the plugins array:

{
    resolve: `medusa-payment-paystack`,
    options: {
      secret_key: process.env.PAYSTACK_SECRET_KEY,
    },
 },
The above code snippet adds Medusa Paystack plugin to your project configurations.

Installing Algolia Medusa Plugin

Through Medusa's flexible plugin system, it is possible to add a search engine to your Medusa backend and storefront using Algolia with just a few steps.

Create an Algolia App

The first step is to create an Algolia app for your Medusa backend. To create one, open the Applications page or, on your dashboard, go to Settings then choose Applications.

On the Applications page, click on the New application button at the top right.

image

In the new page that opens, optionally enter a name for the application and choose a subscription plan. You can choose the Free plan for now, but it’s recommended to switch to the Pay-as-you-go plan as your business grows.

image

Once you’re done, click on the Next Step button. If you picked Pay as you go service, you’ll need to enter billing details before you proceed.

Then, you’ll be asked to pick a region for your application. Once you’re done, click on Review Application Details.

image

In the last step, you’ll see a summary of your order. If all looks good, check the checkboxes at the end of the form to indicate that you agree to the terms and conditions. Then, click on the Create Application button.

image

Retrieve API Keys

To retrieve the API keys that you’ll use in the next sections, go to Settings, then choose API Keys in the Team and Access section.

image

On this page, you’ll find the Application ID, Search-Only API Key, and Admin API Key. You’ll need the Application ID and Admin API Key for the Medusa backend. As for the storefront, you’ll need the Application ID and Search-Only API Key.

image

install the Algolia Plugin

In the directory of your Medusa backend, run the following command to install the Algolia plugin:

npm install medusa-plugin-algolia
Then, add the following environment variables .env to your Medusa backend:

1. ALGOLIA_APP_ID=<YOUR_APP_ID>
2. ALGOLIA_ADMIN_API_KEY=<YOUR_ADMIN_API_KEY>
Where <YOUR_APP_ID> and <YOUR_ADMIN_API_KEY> are respectively the Application ID and Admin API Key found on the API Keys page.

Finally, in medusa-config.js add the following item into the plugins array:

const plugins = [
  // ...
  {
    resolve: `medusa-plugin-algolia`,
    options: {
      application_id: process.env.ALGOLIA_APP_ID,
      admin_api_key: process.env.ALGOLIA_ADMIN_API_KEY,
      settings: {
        products: {
          searchableAttributes: ["title", "description"],
          attributesToRetrieve: [
            "id",
            "title",
            "description",
            "handle",
            "thumbnail",
            "variants",
            "variant_sku",
            "options",
            "collection_title",
            "collection_handle",
            "images",
          ],
        },
      },
    },
  },
]
The above code snippet adds Medusa Paystack plugin to your project configurations.

Add to Next.js Storefront

The Next.js storefront has the Algolia integration available out of the box. To get it working, you just need to follow three steps.

First, ensure that the search feature is enabled in store.config.json:

# store.config.json

{
  "features": {
    "search": true
  }
}
Then, add the necessary environment variables .env:

1. NEXT_PUBLIC_SEARCH_APP_ID=<YOUR_APP_ID>
2. NEXT_PUBLIC_SEARCH_API_KEY=<YOUR_SEARCH_API_KEY>
3. NEXT_PUBLIC_SEARCH_INDEX_NAME=products
Where <YOUR_APP_ID> and <YOUR_SEARCH_API_KEY> are respectively the Application ID and Search-Only API Key on the API Keys page.

Finally, change the code in src/lib/search-client.ts to the following:

# src/lib/search-client.ts

1 import algoliasearch from "algoliasearch/lite"
2
3 const appId = process.env.NEXT_PUBLIC_SEARCH_APP_ID || ""
4
5 const apiKey = 
6   process.env.NEXT_PUBLIC_SEARCH_API_KEY || "test_key"
7
8 export const searchClient = algoliasearch(appId, apiKey)
9
10 export const SEARCH_INDEX_NAME =
11   process.env.NEXT_PUBLIC_INDEX_NAME || "products"
With this you can run Next.js storefront now while the Medusa backend is running, the search functionality will be available in your storefront.

ab

Installing S3 Medusa Plugin

To manage images in Medusa, you need a file service plugin responsible for hosting the images. Without a file service plugin, you will face issues while working with Medusa, such as when uploading images for products.

Medusa provides three different options to handle your file storage. This document focuses on using S3 to store images and files uploaded to the Medusa backend.

You need to create an AWS account to follow along with this documentation.

Create S3 Bucket

On your AWS Console, search for S3 in the search box at the top. Then, choose the first result you see which should be S3 under the Services category.

image

Then, on the new page that opens, click on Create Bucket button at the top right of the Buckets table.

image

The Create Bucket form will open. In the General Configuration section enter a name for the bucket and choose a region for the bucket. Both of the values of these fields are important as you’ll use them throughout the documentation.

AWS S3 Create Bucket

Next, in the Object Ownership section, choose ACLs enabled. Then, two radio buttons will show below it. Choose Bucket owner preferred.

image

Then, in the “Block Public Access settings for this bucket” section, uncheck the “Block all public access” checkbox. This shows a warning message at the bottom of the section with another checkbox. Check the checkbox to ensure you understand that objects in the bucket are publicly accessible.

image

You can leave the rest of the fields in the form as is and scroll down to the end of the page. Then, click on the Create Bucket button.

Manage Bucket Policies

On the page of the bucket you just created, click on the Permissions tab. Then, scroll down until you find the Bucket policy section. Click on Edit in that section.

image

In the Edit Bucket Policy page, enter the following in the field:

{
  "Version": "2012-10-17",
  "Id": "Policy1397632521960",
  "Statement": [
    {
      "Sid": "Stmt1397633323327",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::<YOUR_BUCKET_NAME>/*"
    }
  ]
}
Make sure to replace <YOUR_BUCKET_NAME> with the name of the bucket you created.

Once you’re done, scroll down and click on the Save changes button.

Obtain Access Keys

You must obtain access keys for your user as you’ll use them to integrate the S3 plugin in Medusa with your bucket. To obtain the Access Key ID and the Secret Access Key, open your accout details and benit it click on security credentials.

AWS S3 Secure Access

The Access Key credentials will looks like the below:

AWS S3 Access Key

Install the S3 Plugin

In the directory of your Medusa backend, run the following command to install the S3 Plugin:

npm install medusa-file-s3
Then, add the following environment variables .env:

1. S3_URL=<YOUR_BUCKET_URL>
2. S3_BUCKET=<YOUR_BUCKET_NAME>
3. S3_REGION=<YOUR_BUCKET_REGION>
4. S3_ACCESS_KEY_ID=<YOUR_ACCESS_KEY_ID>
5. S3_SECRET_ACCESS_KEY=<YOUR_SECRET_ACCESS_KEY>
Where:

<YOUR_BUCKET_URL> is the URL to your bucket. It’s in the form https://<BUCKET_NAME>.s3.<REGION>.amazonaws.com, where <BUCKET_NAME> is the name of the bucket and the <REGION> is the region the bucket is created in. If you’re not sure which region, on your bucket’s page on S3 click on Properties. You can then find the region under AWS Region. Make sure to only copy the code (for example, us-west-1).
<YOUR_BUCKET_NAME> is the name of the bucket you created.
<YOUR_BUCKET_REGION> is the region code of your bucket. For example, us-west-1.
<YOUR_ACCESS_KEY_ID> is the Access Key ID that you created for your user.
<YOUR_SECRET_ACCESS_KEY> is the Secret Access Key that you created for your user.
Finally, in medusa-config.js, add to the plugins array the following new item:

# medusa-config.js

const plugins = [
  // ...
  {
    resolve: `medusa-file-s3`,
    options: {
        s3_url: process.env.S3_URL,
        bucket: process.env.S3_BUCKET,
        region: process.env.S3_REGION,
        access_key_id: process.env.S3_ACCESS_KEY_ID,
        secret_access_key: process.env.S3_SECRET_ACCESS_KEY,
    },
  },
]
Next.js Storefront Configuration

If you’re using a Next.js storefront, you need to add an additional configuration that adds the S3 bucket domain name into the configured images’ domain names. This is because all URLs of product images will be from the S3 bucket.

If this configuration is not added, you’ll receive the error "next/image Un-configured Host”.

In next.config.js add the following option in the exported object:

# next.config.js

1. const { withStoreConfig } = require("./store-config")
2.
3. // ...
4.
5. module.exports = withStoreConfig({
6. // ...
7. images: {
8.   domains: [
9.     // ...
10.    "<BUCKET_NAME>.s3.amazonaws.com",
11.   ],
12.   },
13. })
Where <BUCKET_NAME> is the name of the S3 bucket you’re using.

Creating Medusa Admin for MG Food Restaurant And Market Store

Medusa provides an admin panel that makes it easy to configure and manage our store. To set up the admin panel you should first clone the admin repository from GitHub.

git clone https://github.com/medusajs/admin admin
cd admin
Then, install the dependencies:

npm install
Due to the model of my laptop (Dell-Inspiron) the capacity won't allow the dependencies to install so instead use:

npm intsall --legacy-peer-deps
The above enable it to install without no errors.

Test it Out

Before running your Medusa admin, make sure that your Medusa backend is running.

npm run start
By default, Medusa Admin runs on port 7000. You can go to localhost:7000 on your browser to access your admin page.

image

Medusa Server comes with admin login details, which are admin@medusa-test.com as the email address and supersecret as the password. This demo data is a result of --seed added while creating your store server.

Adding PayPal and Paystack Payment Provider to your Regions

You can choose the payment and fulfillment providers available in each region. This allows you to provide customers in specific regions the providers that are available in their country or region.

When a payment or fulfillment provider is added to a region, it means a customer is able to select that payment or fulfillment provider during checkout to complete their purchase.

To add PayPal and Paystack to your regions, follow the steps below to set your store currency;

image

Go to Settings → Regions.
Select a region to edit.
Click on the three dots icon at the top right of the first section on the right.
Click on Edit Region Details from the dropdown.
Under the providers section, select the payment providers you want to add to the region.
Unselect the payment providers you want to remove from the region.
Click Save.
image

To add or remove a fulfillment provider in a region:

Go to Settings → Regions.
Select a region to edit.
Click on the three dots icon at the top right of the first section on the right.
Click on Edit Region Details from the dropdown.
Under the providers section, select the fulfillment providers you want to add to the region.
Unselect the fulfillment providers you want to remove from the region.
Click Save.
Visit Medusa PayPal guide on more on how to integrate it into your Medusa Storefront.

Adding Food Products to your Admin

Medusa Admin supports product management which includes adding new products, editing, publishing, unpublishing, duplicating, and deleting products.

By default, the Medusa store server comes with a few products. You’ll delete them and add new products according to your restaurant's food menu.

bb

Visit Medusa Products Overview for a complete user guide on how to manage products in your store.

Creating Medusa Next.js Storefront

In this tutorial, you will use the Medusa Next.js Storefront Template to build your storefront.

Medusa Next.js Storefront Template already has every feature you may need in your storefront in it; this helps to quicken your development process when you choose to work with Medusa as your commerce engine.

npx create-next-app -e https://github.com/medusajs/nextjs-starter-medusa storefront
Change to the newly created directory storefront and rename the template environment variable file to use environment variables in development:

1. cd my-medusa-storefront
2. mv .env.template .env.local
Make sure the Medusa backend is running, then run the local Next.js server:

npm run dev
Your Next.js storefront is now running at localhost:8000!

Customizing the Storefront

Since you have successfully created your storefront, you can customize your storefront to your taste.

You can find all images used for this project in the GitHub repository.

Modify Your Homepage Banner: To do so, locate src/modules/home/components/hero/index.tsx and replace its contents with the code below:

import UnderlineLink from "@modules/common/components/underline-link"
import Image from "next/image"

const Hero = () => {
  return (
    <div className="h-[90vh] w-full relative">
      <div className="text-white absolute inset-0 z-10 flex flex-col justify-center items-center text-center small:text-left small:justify-end small:items-start small:p-32">
        <h1 className="text-2xl-semi mb-4 drop-shadow-md shadow-black">
          Eat Healthy Foods!!!
        </h1>
        <p className="text-base-regular max-w-[32rem] mb-6 drop-shadow-md shadow-black">
          At Mg Foods and Market store, our Foods are world class cuisine prepared from natural ingregient and farm products. Our market place is known with fresh grown and natural finished products.
          deliver all over the world cause we care for what you live to eat.
        </p>
        <UnderlineLink href="/store">Explore Foods and Market products</UnderlineLink>
      </div>
      <Image
        src="/mg food and market store.webp"
        layout="fill"
        loading="eager"
        priority={true}
        quality={90}
        objectFit="cover"
        alt="Photo by @thevoncomplex https://unsplash.com/@thevoncomplex"
        className="absolute inset-0"
        draggable="false"
      />
    </div>
  )
}

export default Hero
The above code block will change the banner image and change the text.

Secondly, modify your Featured Product section. To do so, locate src/modules/home/components/featured-products/index.tsx and replace its contents with the code below:

import { useFeaturedProductsQuery } from "@lib/hooks/use-layout-data"
import UnderlineLink from "@modules/common/components/underline-link"
import ProductPreview from "@modules/products/components/product-preview"
import SkeletonProductPreview from "@modules/skeletons/components/skeleton-product-preview"

const FeaturedProducts = () => {
  const { data } = useFeaturedProductsQuery()

  return (
    <div className="py-12">
      <div className="content-container py-12">
        <div className="flex flex-col items-center text-center mb-16">
          <span className="text-base-regular text-gray-600 mb-6">
            Latest products
          </span>
          <p className="text-2xl-regular text-gray-900 max-w-lg mb-4">
            Our special features are here to help you look.
          </p>
          <UnderlineLink href="/store">Food products</UnderlineLink>
        </div>
        <ul className="grid grid-cols-2 small:grid-cols-4 gap-x-4 gap-y-8">
          {data
            ? data.map((product) => (
                <li key={product.id}>
                  <ProductPreview {...product} />
                </li>
              ))
            : Array.from(Array(4).keys()).map((i) => (
                <li key={i}>
                  <SkeletonProductPreview />
                </li>
              ))}
        </ul>
      </div>
    </div>
  )
}

export default FeaturedProducts
The above code snippet will change the default texts to match what you are building the store for.

Third, modify your part of the footer section. To do so, locate your src/modules/**layout**/components/footer-cta/index.tsx and replace its content with the code below:

import UnderlineLink from "@modules/common/components/underline-link"
import Image from "next/image"

const FooterCTA = () => {
  return (
    <div className="bg-amber-100 w-full">
      <div className="content-container flex flex-col-reverse gap-y-8 small:flex-row small:items-center justify-between py-16 relative">
        <div>
          <h3 className="text-2xl-semi">Shop your market products</h3>
          <div className="mt-6">
            <UnderlineLink href="/store">Explore products</UnderlineLink>
          </div>
        </div>

        <div className="relative w-full aspect-square small:w-[35%] small:aspect-[28/36]">
          <Image
            src="/Food-market.jpg"
            alt=""
            layout="fill"
            objectFit="cover"
            quality={70}
            className="absolute inset-0"
          />
        </div>
      </div>
    </div>
  )
}

export default FooterCTA
The above code block will change the background image and text.

PayPal Payment Integration

Then, in your Next.js storefront, set the environment variable necessary for the PayPal integration:

NEXT_PUBLIC_PAYPAL_CLIENT_ID=<YOUR_CLIENT_ID>
Make sure to replace <YOUR_CLIENT_ID> with your PayPal client ID. You can retrieve it from the PayPal developer dashboard.

If you restart your Next.js backend you should be able to pay with PayPal on checkout.

image

Customization

To customize the pages of the storefront, you can customize the files under the src/pages directory.

To customize the components used in the storefront, you can customize the files under the src/modules directory.

To customize the styles of the storefront, you can customize the src/styles directory.

Full checkout workflow.

image

You can confirm the orders from your Medusa Admin panel for this project.
