

# BLOCKWAVE
## Decentralized Social Media and Event Booking Application (DApp)

Blockwave is a decentralized social media and event ticketing platform that allows users to share their posts, create and purchase event tickets, and pay directly to their favorite influencers using their wallet addresses. The platform utilizes a decentralized architecture and integrates with user-friendly UI and Sanity Studio to store data such as user profiles, posts, comments, wallet addresses, and ticket details. With Blockwave, users can mint their own NFTs and set their profile pictures to be associated with their account in Sanity.

Blockwave is available on three EVM-based blockchains: [Mantle Wadsley Testnet](https://explorer.testnet.mantle.xyz/), [Shardeum Sphinx Betanet](https://explorer-sphinx.shardeum.org/), and [Polygon Mumbai](https://mumbai.polygonscan.com/). Users can easily connect to their preferred blockchain network and start using the platform. 

They can buy and sell tickets using the native tokens of the respective blockchains, such as BIT on Mantle, SHM on Shardeum, and Matic on Polygon. With a seamless and secure user experience, Blockwave brings social media and event ticketing to the blockchain.

## Frontend Repository

The frontend repository for Blockwave, which includes the smart contracts, can be found at [https://github.com/aryan877/blockwave](https://github.com/aryan877/blockwave)

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

To use our decentralized content sharing dapp, follow these steps:

1.  Sign in with your Ethereum wallet by clicking on the **Sign in with Ethereum** button. Make sure your Metamask wallet is properly configured and has sufficient funds to pay for the transaction fees. 
2.  To upload a post, click on the **Post** button and select a picture from your local file system. The image should be in a supported format and should not exceed the size limit of 10MB.
3.  Your post will be associated with your Ethereum wallet address and stored in Sanity Studio.
4.  Browse posts, like, and comment on them. You can also make payments to influencers for their posts and mint NFTs associated with your account for your profile pictures.
5.  To create events and sell tickets in the form of NFTs, use the **Mint Event** button. Fill in the required details such as total supply, price, sale start, sale end, and metadata URI. The price should be in wei, and the sale start time must be in the future. The sale end time must be after the sale start time. 
6.  Users can also send native tokens like ETH, MATIC, or other tokens depending on the native token of the EVM chain that they are connected to (e.g. BIT on Mantle, Matic on Polygon Mumbai Chain, SHM on Shardeum Sphinx) and the same goes to purchase tickets.

# Smart Contract Documentation

Our decentralized content sharing dapp uses two different smart contracts to implement two different functionalities:

-   **ERC-1155 TicketFactory contract**: This contract allows the creation and management of multiple fungible tokens, each representing a ticket for a specific event. It is suitable for event ticketing as it allows the creation of a large number of identical tickets for an event and easy tracking of their distribution and sale.
    
-   **ERC-721 ProfileImage contract**: This contract allows the creation and management of unique, non-fungible tokens (NFTs), each representing a user's profile image. It is suitable for profile image uploads as it ensures that each user's profile image is unique and cannot be duplicated or replicated. This contract also allows for easy management and tracking of the ownership of each user's profile image.

## ERC-1155 TicketFactory Contract

We use the ERC-1155 TicketFactory contract for event ticketing. This contract allows the creation and management of multiple fungible tokens ( i.e. tokens that are interchangeable with one another ), each representing a ticket for a specific event. This contract is suitable for event ticketing as it allows us to:

-   Create a large number of identical tickets for an event
-   Easily track the distribution and sale of tickets
-   Keep track of the total number of tickets created, the number of tickets sold, the remaining available tickets, event start date and time, and event end date and time.
- 
The TicketFactory contract inherits from ERC1155 and adds the following functionality:

## Structs

**1. Ticket Struct**

The "Ticket" structure is a key component of our ERC-1155 TicketFactory smart contract. It represents an event hosted by the user and has the following properties:

    struct Ticket {
    uint256 id;
    address creator;
    uint256 totalSupply;
    uint256 availableSupply;
    uint256 price;
    uint256 saleStart;
    uint256 saleEnd;
    string metadataURI;
    }
    
This structure is used to define and keep track of different events and their ticket details within the contract. It allows us to easily create and manage multiple fungible tokens (i.e. tokens that are interchangeable with one another), each representing an event. With the help of this structure, we can keep track of the total number of events created, the number of tickets sold, the remaining available tickets, event start date and time, event end date and time, and other metadata associated with the event.

## Functions

**1. Create Ticket Function**

The "createTicket" function is a public function defined within our ERC-1155 TicketFactory smart contract. It allows users to create a new event ticket by specifying the following parameters:

-   "totalSupply": The total number of tickets available for the event.
-   "price": The price of each ticket in wei.
-   "saleStart": The start date and time of the ticket sale.
-   "saleEnd": The end date and time of the ticket sale.
-   "metadataURI": The URI of the metadata associated with the event.

The function performs various checks to ensure that the inputs provided are valid. For instance, it requires the total supply and price to be greater than 0 and the sale end time to be after the sale start time.

By calling this function, users can create and manage multiple fungible tokens, each representing a ticket for a specific event. This enables efficient tracking of ticket distribution and sale within the contract.

    function createTicket( uint256 totalSupply, uint256 price, uint256 saleStart, uint256 saleEnd, string  memory metadataURI ) {}
    
**2. Buy Ticket Function**

The "buyTicket" function is another public function defined within our ERC-1155 TicketFactory smart contract. It allows users to purchase event tickets by specifying the following parameters:

-   "ticketId": The ID of the ticket to be purchased.
-   "quantity": The number of tickets to be purchased.

By calling this function, users can buy tickets for events in a secure and efficient manner, with the smart contract ensuring that all conditions are met before executing the transaction.

       function buyTicket(uint256 ticketId, uint256 quantity) public payable {}

**3. Get Unsold Tickets Function**

The "getUnsoldTickets" function is a public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all unsold tickets available for purchase, by iterating through all tickets and identifying those that have available supply greater than zero. The function creates a new array to hold the unsold tickets, adds each unsold ticket to the array in reverse order, and returns the array to the user.

`function getUnsoldTickets() public view returns (Ticket[] memory) {}` 

**4. Get My Events Function**

The "getMyEvents" function is another public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all events they have created, by iterating through all tickets and identifying those whose "creator" address matches the caller's address. The function creates a new array to hold the user's events, adds each event to the array in reverse order, and returns the array to the user.

`function getMyEvents() public view returns (Ticket[] memory) {}` 

**5. Get My Tickets Function**

The "getMyTickets" function is also a public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all tickets they have purchased, by iterating through all tickets and identifying those that have been bought by the caller's address. The function creates a new array to hold the user's tickets, adds each ticket to the array in reverse order, and returns the array to the user.

`function getMyTickets() public view returns (Ticket[] memory) {}`

## Events

**1. TicketCreated** - emitted when a new event ticket is created.


`event TicketCreated( uint256 indexed ticketId,
    address indexed creator,
    uint256 totalSupply,
    uint256 price,
    uint256 saleStart,
    uint256 saleEnd,
    string metadataURI );` 

This event is emitted when a new event ticket is created, with the following parameters:

-   "ticketId": The ID of the new ticket.
-   "creator": The address of the creator of the ticket.
-   "totalSupply": The total supply of the ticket.
-   "price": The price of each ticket.
-   "saleStart": The timestamp of when the ticket sale begins.
-   "saleEnd": The timestamp of when the ticket sale ends.
-   "metadataURI": The URI of the metadata associated with the ticket.

**2. TicketBought** - emitted when a user buys an event ticket.

`event TicketBought( uint256 indexed ticketId,
    address indexed buyer,
    uint256 quantity,
    uint256 amount );` 

This event is emitted when a user buys an event ticket, with the following parameters:

-   "ticketId": The ID of the purchased ticket.
-   "buyer": The address of the buyer of the ticket.
-   "quantity": The number of tickets purchased.
-   "amount": The total amount paid for the tickets.

## ERC-721 ProfileImage Contract

We use the ERC-721 ProfileImage contract for profile image uploads for our users. This contract allows us to create and manage unique, non-fungible tokens (NFTs), each representing a user's profile image. This contract is suitable for profile image uploads as it ensures that:

-   Each user's profile image is unique and cannot be duplicated or replicated
-   We can easily manage and track the ownership of each user's profile image.

The ProfileImage contract inherits from ERC721 and adds the following functionality:

## Structs

**1. RenderToken struct**

    struct RenderToken {
    uint256 id;
    string uri;
    string space;
    }
    
## Functions

**1. Mint NFT Function**

The mint function mints a new NFT with a given _uri and assigns it to a given recipient. It returns the ID of the new NFT:

    function mint(address recipient, string memory _uri) public returns (uint256) {}

**2. Get All Tokens Function**

The getAlltoken function returns an array of RenderToken structs representing all the existing NFTs:

    function getAlltoken() public view returns (RenderToken[] memory) {}

## Events

**1. TokenMinted** - emitted when a new NFT is minted.

    event TokenMinted(uint256 tokenId);

We emit the TokenMinted event whenever a new Profile Image NFT is minted in our smart contract, which includes the newly minted token ID (tokenId). We extract this ID from the blockchain transaction log and store it in Sanity against the user's profile. To ensure additional security, we verify ownership of the NFT by calling the ownerOf(tokenId) function from the ERC-721 standard each time a user's profile page is loaded on the frontend.

# Troubleshooting

**Metamask Login Issue**

If you are unable to sign in with Metamask, please ensure that your Metamask wallet is properly configured and has sufficient funds to pay for the transaction fees. Additionally, ensure that you are signed into Metamask and have granted permission for the dapp to access your wallet.

**Image Upload Issue**

If you are unable to upload an image, please ensure that the image is in a supported format and within the size limit of 10MB. 

# Contribution Guidelines

We welcome contributions from anyone who would like to help improve our decentralized content sharing dapp.

To contribute, please follow the following steps:

1. Fork the repository to your own GitHub account: https://github.com/aryan877/blockwave.git
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

-   [Spheron](https://spheron.network/) for their SDK which is used to upload images and NFT metadata to IPFS.
-   [Mantle](https://www.mantle.xyz/) and [Shardeum](https://shardeum.org/) communities for providing the blockchain networks and smart contract ecosystem that Blockwave runs on.
-   [Sanity](https://www.sanity.io/) for their content management system which stores our user profiles, posts, comments, wallet public keys, and more.
-   [wagmi](https://wagmi.sh/) for their collection of React Hooks containing everything you need to start working with Ethereum, making it easy to "Connect Wallet," and display balance information, sign messages, interact with contracts, and much more — all with caching, request deduplication, and persistence.



