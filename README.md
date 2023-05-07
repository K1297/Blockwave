# BLOCKWAVE
# Decentralized Social Media Dapp  

Blockwave is a decentralized social media dapp where users can share their posts and followers can
pay directly to their favorite influencers using their wallet addresses. The dapp uses a decentralized
architecture and integrates with user-friendly UI, and sanity studio to store data like user profiles,
posts, comments, and wallet addresses. The dapp also allows users to mint NFTs and set their profile
picture, which will be associated with their account in sanity.

## Frontend Repository

The frontend repository for Blockwave, which includes the smart contracts, can be found at [https://github.com/blockwaveapp/blockwave-frontend](https://github.com/aryan877/blockwave-frontend).

## Backend Repository

The backend repository for Blockwave can be found at [https://github.com/blockwaveapp/blockwave-backend](https://github.com/aryan877/blockwave-backend).


# Features 
*  user authentication with Metamask Wallet.
*  Supports mantle testnet, shardeum sphinx and polygon testnet.
*  post upload and association with user's wallet address.
*  access to likes and commenting on posts.
*  Normal upload and nft minting for profile picture.
*  Tipping to your favourite Influncer.
*  event ticketing page to buy tickets for events.
*  creating,  selling and buying of event tickets using smart contracts.

# Architecture
![photo_2023-05-03_11-40-02](https://user-images.githubusercontent.com/125735215/235933332-f79eaa67-567e-4c92-bcb0-94eee86b50ee.jpg)


## Components
*  **Frontend:** This is the user interface that users interact with. It is responsible for displaying information and allowing users to interact with our Dapp.
*  **NFT Profile Smart Contract:** This is a smart contract that manages the creation, ownership, and transfer of non-fungible tokens (NFTs) that represent user profiles.
*  **Event Ticketing Smart Contract:** This is a smart contract that manages the creation, sale of event tickets as NFTs.
*  **Sign in with Ethereum:** This is a feature that allows users to sign in to the application using their Ethereum wallet address.
*  **Backend:** This is the server-side of the Dapp that handles data storage, processing, and communication with other components.
*  **Sanity Database:** This is a cloud-based database service that provides a scalable and flexible solution for storing and managing data of our users.
*  **IPFS Network:** This is a decentralized peer-to-peer network for storing and sharing files.
*  **Spheron SDK:** This is a software development kit (SDK) that provides tools for building decentralized applications.

# Installation
## Frontend (Next.js) Installation

**Clone the repository**
git clone https://github.com/blockwaveapp/blockwave-frontend.git

**Install dependencies**
cd blockwave-frontend
npm install

* Configure environment variables by creating a .env file in the root directory with the following variables:
* - SANITY_TOKEN
* - NEXT_PUBLIC_SANITY_ID
* - SPHERON_TOKEN
* - IRON_PASSWORD

## Backend (Sanity) Installation

**Clone the repository**

git clone https://github.com/blockwaveapp/blockwave-backend.git

**Install dependencies**
cd blockwave-backend
npm install

**Start the Sanity Studio server**
sanity dev

# Usage

*   sign in with ethereum wallet by clicking on the "sign in with ethereum " button.
*   upload a post picture by clicking on the "post" button and selecting a picture
 from your local file system. 
*  your post will be associated with your ethereum wallet address 
and in Sanity studio.
*  users can browse posts , make payments to influencers 
and mint NFTs associated with their account for their profile pictures, create event and sell tickets in form of NFTs.

# Smart Contract Documentation

## NFT profile smart contract

NftProfile is a Solidity smart contract for creating and managing non-fungible tokens (NFTs)
that represent profiles. It extends the ERC721URIStorage contract from the OpenZeppelin library
to provide the functionality for creating NFTs and storing their metadata. In addition, it defines a
custom function for setting the profile picture of a token.

**Usage**

To use the NftProfile contract, you can import it into your Solidity code as follows:
```bash
import "path/to/NftProfile.sol";
```
Then, you can create a new instance of the contract and call its functions as needed:
```bash
NftProfile nftProfile = new NftProfile(); // Create a new NFT uint256 tokenId = nftProfile
.createNFT("https://example.com/token-123", "https://example.com/image-123"); // Set the profile
picture for an NFT nftProfile.setProfilePicture(tokenId);
```
**Functionality**

The NftProfile contract inherits from ERC721URIStorage and adds the following functionality:
* Create NFTs
The **`createNFT`** function creates a new NFT with a given **`tokenURI`** and imageURI and returns its ID:
function createNFT(string memory tokenURI, string memory imageURI) public returns (uint256)
* Set Profile Picture
The **`setProfilePicture`** function sets the profile picture for an existing NFT with a given **`tokenId`**:
function setProfilePicture(uint256 tokenId) public

**Events**

The NftProfile contract emits the following events:

* ProfilePictureSet - emitted when the profile picture for an NFT is set.
* TokenImageURISet - emitted when the image URI for an NFT is set.

## Event Ticketing Smart Contract

This smart contract is used for creating events and issuing tickets on the Ethereum blockchain. It is
based on Solidity version 0.8.0 and uses two contracts from the OpenZeppelin library: ERC1155 for
creating tokens and Ownable for adding ownership and access control.

**Event Structure**

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

The Ownable contract is used to add ownership and access control to this contract. The contract
owner can create events, mint tickets, and perform other administrative functions.

**Base URI**

This contract uses a base URI for the metadata of the NFTs created by this contract. The URI is set
to "https://blockwave.com/tickets/{id}". The "{id}" part of the URI will be replaced with the actual
ID of the NFT, which provides more information about the NFTs and makes them easier to identify

# API Documentation 

## Authentication

**`POST /api/auth`**

This endpoint is used for user authentication. The user needs to sign a transaction in Metamask with
a nonce value generated by the server. Once the user signs the prompt, the backend server receives
the signature and checks if the signature is valid. If it is valid, the server sends back a JWT cookie to
the client. If it is not valid, the server rejects the login and sends back "not authenticated, invalid
request".

**Request**
```bash
{
  "nonce": "string"
}
```
```bash
{
  "token": "string"
}
```
**Posts**

**`POST /api/posts`**

This endpoint is used for uploading a post picture to the server. The user needs to send a valid JWT cookie that was generated during authentication. Before associating the picture with the user's account, the server checks if the user is the actual owner of the wallet address. If the JWT cookie is valid, the server uploads the image to IPFS using Spheron SDK and associates the image IPFS URL with the user wallet address in the Sanity DB. If the JWT cookie is invalid, the server rejects the upload request.

**Request**

```bash
{
  "image": "string",
  "token": "string"
}
```
**Response**

```bash
{
  "message": "string"
}
```
**Events**

**`POST /api/events`**

This endpoint is used for creating a new event. The user needs to send a valid JWT cookie that was generated during authentication. The server creates a new event in the Event Ticketing smart contract, and associates the event details with the user's wallet address in the Sanity DB. If the JWT cookie is invalid, the server rejects the event creation request.

**Request**

```bash
{
  "name": "string",
  "description": "string",
  "date": "string",
  "location": "string",
  "price": "number",
  "token": "string"
}
```
**Response**

```bash
{
  "message": "string"
}
```
# Troubleshooting

**Metamask Login Issue**

If you are unable to sign in with Metamask, make sure that your Metamask wallet is properly
configured and has sufficient funds to pay for the transaction fees. Also, make sure that you are
signed into Metamask and have granted permission for the dapp to access your wallet.

**Image Upload Issue**

If you are unable to upload an image, make sure that the image is in a supported format and within
the size limit. Also, make sure that you are sending a valid JWT cookie with the request.

**Event Creation Issue**

If you are unable to create an event, make sure that you are sending a valid JWT cookie with the
request and that the event details are valid.

**Ticket Purchase Issue**

If you are unable to purchase a ticket, make sure that you are sending a valid JWT cookie with the
request and that the event ID is valid. Also, make sure that you have sufficient funds in your wallet
to pay for the ticket.

# Contribution Guidelines

We welcome contributions from anyone who would like to help improve our decentralized content sharing dapp. 
To contribute , please follow the following steps: 

* fork the repository to your own github account 
* create a new branch from the main branch for your changes 
* make your changes and commit them with clear commit messages 
* push your changes to your forked repository 
* open a pull request to merge your changes into the main branch 

# Team Members

* Aryan Kumar
* Kushal Sapra 
* Barbra Kokonya
* Janhavi Chavada 

# Acknowledgements

we are very grateful for these organizations for their contributions to our decentralized content sharing dapp. 
 
*    **Sanity** for their content management system which stores our user profiles , posts,comments, wallet addresses etc.
*    **Spheron** for their SDK which is used to upload images to IPFS.
*    **Mantle, Shardeum and polygon** community for providing the blockchain networks and smart contract ecosystem that our dapp runs on.
 




