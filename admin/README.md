Medusa Admin
Medusa is an open-source headless commerce engine that enables developers to create amazing digital commerce experiences.

Medusa is released under the MIT license. Current CircleCI build status. PRs welcome! Discord Chat Follow @medusajs

Quickstart
Follow our quickstart guide to learn how to set up a Medusa server.

Setting up Admin
Clone this repository
git clone https://github.com/medusajs/admin medusa-admin
cd medusa-admin
Install dependencies
yarn install
Start the development server
yarn start
Go to http://localhost:7000
Back in your Medusa engine installation directory, you can create your own user for the admin by running:

medusa user -e some@email.com -p some-password
Alternatively, if you've seeded your server with our dummy data, you can use the following credentials:

admin@medusa-test.com // supersecret
Features
You can learn about all of the ecommerce features that Medusa provides in our documentation.

Contributions
Please check our contribution guide for details about how to contribute to both our codebase and our documentation.

Repository structure
The Medusa repository is a mono-repository managed using Lerna. Lerna allows us to have all Medusa packages in one place, and still distribute them as separate NPM packages.
