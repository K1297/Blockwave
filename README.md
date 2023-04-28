# BLOCKWAVE
## Project description
* **BLOCKWAVE** is a a decentralized content sharing platform that allows users to create, upload, and share content with others.
* The platform incentivizes creators and influencers to generate **high-quality** content by offering them the ability to monetize their content through making *Payment*, *event ticketing*, and *NFT profile pictures*.
* The platform is made up of several components such the front-end, back-end, and various smart contracts.
* Front-end is responsible for providing a user-friendly interface for users to interact with the platform while the back-end consists of several smart contracts that handle various aspects of the platform, such as nft profile picture & Event Ticketing.
* It is Integrated with **_Spheron Storage IPFS_**, **_Hosting_**& **_UI_** to ensure that content is stored in a decentralized manner.
* The NFT smart contract allows users to mint NFTs for their profile pictures, which are associated with their account in sanity studio.
* Sanity studio is used to store various user-related data, such as likes, dislikes, posts, comments, and IPFS hashes for the post.
* Overall, **BlockWave** provides a decentralized content sharing platform that incentivizes creators and influencers to generate **_high-quality_** content while providing users with a seamless and **_user-friendly_** experience.

## Architecture
![ARCHITECTURE DIAGRAM drawio](https://user-images.githubusercontent.com/125735215/235175483-909a742b-f8bb-4f13-a0e3-ab3cb506770b.png)

**Components**
* **Frontend**: This component will be responsible for providing a user-friendly interface for theusers to interact with the Dapp. It will be built using modern web development technologies such as Nextjs.
*  **Backend**: This component will handle the business logic and data storage of the Dapp. It will be built using Sanity, and will communicate with the Ethereum blockchain and other external services through smart contracts and APIs.
*  **Payment Processing Smart Contract**: This smart contract will handle the payment processing for the subscriptions of the followers and influencers on the platform. It will be responsible for verifying the validity of the subscription and transferring the payment to the respective wallets.The smart contract will be written in Solidity.
*  **Storage Smart Contract**: This smart contract will handle the storage of the uploaded content on the IPFS network through Spheron Storage. It will be responsible for creating and managing thecontent hashes, and ensuring the integrity and accessibility of the content. The smart contract will be written in Solidity.
*  **NFT Smart Contract**: This smart contract will allow users to mint NFTs for their profile pictures.It will be responsible for creating and managing the NFTs associated with the user's account, and ensuring their uniqueness and authenticity. The smart contract will be written in Solidity.
*  **Event Ticketing Smart Contract**: This smart contract will handle the ticketing system for the events hosted on the platform. It will be responsible for verifying the validity of the tickets and transferring the payment to the event organizers. The smart contract will be written in Solidity.
*   **Sanity Studio**: This component will provide a powerful yet user-friendly interface for managing the content and data of the Dapp. It will be used to store information such as user wallet addresses, IPFS hashes for the posts, comments, and likes/dislikes. Sanity Studio will communicate with the backend through APIs.
   
## Installation   
## Usage
## Smart Contract Documentation



