# BLOCKWAVE
## Decentralized Content Sharing Dapp 

* **BLOCKWAVE** is a a decentralized content sharing platform that allows users to create, upload, and share content with others.
* The platform incentivizes creators and influencers to generate **high-quality** content by offering them the ability to monetize their content through making *Payment*, *event ticketing*, and *NFT profile pictures*.
* The platform is made up of several components such the front-end, back-end, and various smart contracts.
* Front-end is responsible for providing a user-friendly interface for users to interact with the platform while the back-end consists of several smart contracts that handle various aspects of the platform, such as nft profile picture & Event Ticketing.
* It is Integrated with **_Spheron Storage IPFS_**, **_Hosting_**& **_UI_** to ensure that content is stored in a decentralized manner.
* The NFT smart contract allows users to mint NFTs for their profile pictures, which are associated with their account in sanity studio.
* Sanity studio is used to store various user-related data, such as likes, dislikes, posts, comments, and IPFS hashes for the post.
* Overall, **BlockWave** provides a decentralized content sharing platform that incentivizes creators and influencers to generate **_high-quality_** content while providing users with a seamless and **_user-friendly_** experience.

## Features 
*  user authentication with Metamask Wallet.
*  nft minting .
*  event ticketing page to buy tickets for events.
*  post upload and association with user's wallet address. 
*  access to likes/dislikes/ commenting on posts.
*  creating,  selling and buying of event tickets using smart contracts.


## Architecture
![blockwave drawio (1)](https://user-images.githubusercontent.com/125735215/235243199-bc37420b-a38f-46a2-a926-cd322413eeda.png)

**Components**
*  **User's Browser:** This is where the user interacts with the frontend UI.
*  **Vercel Hosting Platform:** This is where the frontend app is hosted and serves as a CDN fordelivering static assets.
*  **Next.js Frontend App:** This is the frontend application that the user interacts with, built using the Next.js framework.
*  **Sanity Studio:** This is where data like user profiles, posts, comments, and wallet addresses are stored.
*  **Wagmi:** This is a user-friendly interface for managing Ethereum wallets and interacting with smart contracts.
*  **Event Ticketing Smart Contract:** This is a smart contract that manages the creation, selling, and buying of event tickets.
*  **IPFS Network:** This is a decentralized peer-to-peer network for storing and sharing files.
*  **Polygon Test Network:** This is the blockchain network where the dapp's smart contracts are deployed.
*  **Backend Server:** This is where server-side logic like post uploads are handled.
*  **Metamask Wallet:** This is a browser extension for interacting with wallets and signing transactions.
   
## Installation
```bash
1. Clone the repository:
```
gitclone[(https://github.com/username/repo.git)]
```bash
2. Install dependencies:
```
```bash
3.  Configure environment variables by creating a .env file in the root directory with the following
variables:
```
```bash
4.  Start the development server:
```
```bash
5.  Deploy the app to Vercel:
```
```bash
6.  This will deploy the app to Vercel, and you will be provided with a URL where you can access the app:
```
## Usage

*   sign in with ethereum wallet by clicking on the "sign in with ethereum " button.
*   upload a post picture by clicking on the "post" button and selecting a picture
 from your local file system. 
*  your post will be associated with your ethereum wallet address 
and in **Sanity studio.**
*  users can browse posts , make payments to influencers 
and **mint NFTs** associated with their account for their profile pictures.

## Smart Contract Documentation



