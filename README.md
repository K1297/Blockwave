
# BLOCKWAVE
## Decentralized Social Media and Event Booking Application (DApp)

Blockwave is a decentralized social media and event ticketing dapp where users can share their posts, create and buy event tickets using ERC-1155 tokens, and followers can pay directly to their favorite influencers using their wallet addresses. The dapp uses a decentralized architecture and integrates with user-friendly UI, and sanity studio to store data like user profiles, posts, comments, wallet addresses, and ticket details. The dapp also allows users to mint NFTs and set their profile picture, which will be associated with their account in sanity.

## Frontend Repository

The frontend repository for Blockwave, which includes the smart contracts, can be found at [https://github.com/aryan877/blockwave](https://github.com/aryan877/blockwave).

## Serverless Functions

The serverless functions for Blockwave can be found in the `/src/pages/api` directory of the frontend repository.

## Smart Contracts

The smart contracts for Blockwave can be found in the `/contracts` directory of the frontend repository.

## Sanity Repository

The sanity studio repository for Blockwave can be found at [https://github.com/aryan877/blockwave-sanity](https://github.com/aryan877/blockwave-sanity).



# Features 

- User authentication to the backend is done through wallet integration, utilizing the **Sign in with Ethereum** (SIWE) feature.
-  Supports *Mantle Wadsley testnet, Shardeum 1.X Sphinx and Polygon Mumbai testnet*.
-   The dapp leverages [Spheron Storage SDK](https://github.com/spheronFdn/sdk/blob/main/packages/storage/README.md) to enable the uploading of metadata for ERC-721 NFTs used for profile images and ERC-1155 NFTs used for event ticketing, as well as any type of media like posts.
-   Users can engage with content by liking and commenting on posts.
-   The platform supports both standard image uploads and NFT minting for profile pictures.
-   Users can tip their favorite influencers directly using wallet addresses.
-   There is an event ticketing page that allows users to purchase tickets for events.
-   The platform facilitates the creation, sale, and purchase of event tickets using smart contracts.

# Architecture
![photo_2023-05-03_11-40-02](https://user-images.githubusercontent.com/38075578/236750639-5ec91396-0ce1-46bd-b7f9-49f6b66a1bf5.jpg)


## Components
*  **Frontend:** This is the user interface that users interact with. It is responsible for displaying information and allowing users to interact with our Dapp.
*  **NFT Profile Smart Contract:** This is a smart contract that manages the creation, ownership, and transfer of non-fungible tokens (NFTs) that represent user profiles.
*  **Event Ticketing Smart Contract:** This is a smart contract that manages the creation, sale of event tickets as NFTs.
*  **Sign in with Ethereum:** This is a feature that allows users to sign in to the application using their Ethereum wallet address.
*  **Backend:** This is the server-side of the Dapp that handles data storage, processing, and communication with other components.
*  **Sanity Database:** This is a cloud-based database service that provides a scalable and flexible solution for storing and managing data of our users.
*  **IPFS Network:** This is a decentralized peer-to-peer network for storing and sharing files.
*  **Spheron SDK:** This is a software development kit (SDK) that provides tools for building decentralized applications.

# Local Installation

To get started with the Blockwave app on your local machine, please follow the steps below:

**Clone the repository**

Clone the Blockwave repository to your local machine by running the following command:

    git clone https://github.com/aryan877/blockwave

**Install dependencies**

Navigate into the cloned repository and install the dependencies by running the following command:

    cd blockwave
    npm install
    
**Configure Environment Variables**

Configure the environment variables required for the app by creating a `.env.local` file in the root directory of the cloned repository. The `.env.local` file should contain the following variables:

-   `SANITY_TOKEN`: This is an authentication token required for accessing the Sanity database. It allows the application to read and write data to the database.
-   `NEXT_PUBLIC_SANITY_ID`: This is the project ID for the Sanity database. It is used to identify which database the application should connect to.
-   `SPHERON_TOKEN`: This is a token required for accessing the Spheron SDK, which is used for decentralized content distribution.
-   `IRON_PASSWORD`: This is a password required for encrypting and decrypting sensitive data, such as user wallet addresses. It is used for secure storage and transfer of data within the application.

# Usage

To use this application:

1. Sign in with your Ethereum wallet by clicking on the **Sign in with Ethereum** button.
2. Upload a post picture by clicking on the **Post** button and selecting a picture from your local file system.
3. Your post will be associated with your Ethereum wallet address and stored in Sanity Studio.
4. Browse posts, make payments to influencers, and mint NFTs associated with your account for your profile pictures.
5. Create events and sell tickets in the form of NFTs.



# Smart Contract Documentation

Our decentralized content sharing dapp uses two different smart contracts to implement two different functionalities:

-   **ERC-1155 TicketFactory contract**: This contract allows the creation and management of multiple fungible tokens, each representing a ticket for a specific event. It is suitable for event ticketing as it allows the creation of a large number of identical tickets for an event and easy tracking of their distribution and sale.
    
-   **ERC-721 ProfileImage contract**: This contract allows the creation and management of unique, non-fungible tokens (NFTs), each representing a user's profile image. It is suitable for profile image uploads as it ensures that each user's profile image is unique and cannot be duplicated or replicated. This contract also allows for easy management and tracking of the ownership of each user's profile image.

## ERC-1155 TicketFactory Contract

We use the ERC-1155 TicketFactory contract for event ticketing. This contract allows the creation and management of multiple fungible tokens (i.e. tokens that are interchangeable with one another), each representing a ticket for a specific event. This contract is suitable for event ticketing as it allows us to:

-   Create a large number of identical tickets for an event
-   Easily track the distribution and sale of tickets
-   Keep track of the total number of tickets created, the number of tickets sold, the remaining available tickets, event start date and time, and event end date and time.

**Event Struct**

Within this contract, there is a structure called "Event" that has the following properties:
* totalSupply: total number of tickets available for the event
* remainingSupply: number of tickets still available for the event
* price: the price of each ticket
* startDate: the start date of the event
* endDate: the end date of the event
This structure is used to define and keep track of different events and their ticket details within the
contract.

**Creating Events**

To create a new event, the contract owner can call the **`createEvent function`**. This function takes the
following parameters:
* _eventId: the ID of the event to be created
* _totalTickets: the total number of tickets available for the event
* _ticketPrice: the price of each ticket
* _startDate: the start date of the event
* _endDate: the end date of the event
Before creating the event, several "require" statements are included which are conditions that must
be met for the event to be created:
1. The total number of tickets must be greater than zero
2. The ticket price must be greater than zero
3. The start date of the event must be in the future
4. The end date of the event must be after the start date

If all the conditions are met, the function will create a new event with the specified details and store
it in the _events mapping defined earlier.

**Event Ticket Minting**

After an event is created, the contract owner can mint tickets for that event by calling **`the _mint`**
function. This function takes the following parameters:
* to: the address of the recipient of the minted tickets
* id: the ID of the event for which the tickets are being minted
* amount: the number of tickets to be minted
* data: optional data to be included with the ticket minting
This function will create and mint the specified number of tickets for the given event ID and
transfer them to the recipient address.

**Access Control**

The Ownable contract is used to add ownership and access control to this contract. The contract owner can create events, mint tickets, and perform other administrative functions.

## ERC-721 ProfileImage Contract

We use the ERC-721 ProfileImage contract for profile image uploads for our users. This contract allows us to create and manage unique, non-fungible tokens (NFTs), each representing a user's profile image. This contract is suitable for profile image uploads as it ensures that:

-   Each user's profile image is unique and cannot be duplicated or replicated
-   We can easily manage and track the ownership of each user's profile image.

The ProfileImage contract inherits from ERC721 and adds the following functionality:

**Mint NFTs**

The mint function mints a new NFT with a given _uri and assigns it to a given recipient. It returns the ID of the new NFT:

    function mint(address recipient, string memory _uri) public returns (uint256)

**Get All Tokens**

The getAlltoken function returns an array of RenderToken structs representing all the existing NFTs:

    function getAlltoken() public view returns (RenderToken[] memory)

**RenderToken struct**

    id - the ID of the NFT
    uri - the URI of the NFT
    space - an empty string used for formatting purposes

**Events**

TokenMinted - emitted when a new NFT is minted.

    event TokenMinted(uint256 tokenId);

By using both ERC-1155 and ERC-721 contracts, we are able to implement two distinct functionalities in our dapp with the appropriate level of tokenization for each use case.

# Troubleshooting

**Metamask Login Issue**

If you are unable to sign in with Metamask, please ensure that your Metamask wallet is properly configured and has sufficient funds to pay for the transaction fees. Additionally, ensure that you are signed into Metamask and have granted permission for the dapp to access your wallet.

**Image Upload Issue**

If you are unable to upload an image, please ensure that the image is in a supported format and within the size limit of 10MB. 

# Contribution Guidelines

We welcome contributions from anyone who would like to help improve our decentralized content sharing dapp.

To contribute, please follow the following steps:

1. Fork the repository to your own GitHub account: https://github.com/blockwaveapp/blockwave.git
2. Create a new branch from the main branch for your changes.
3. Make your changes and commit them with clear commit messages.
4. Push your changes to your forked repository.
5. Open a pull request to merge your changes into the main branch.

# Team Members

- Aryan Kumar
- Kushal Sapra 
- Barbra Kokonya
- Janhavi Chavada 

# Acknowledgements


We are very grateful for these organizations for their contributions to our decentralized content sharing dapp:

* **Spheron** for their SDK which is used to upload images and NFT metadata to IPFS.
* **Mantle**, **Shardeum**, and **Polygon** community for providing the blockchain networks and smart contract ecosystem that Blockwave runs on.
* **Sanity** for their content management system which stores our user profiles, posts, comments, wallet public keys, and more.



