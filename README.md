# BLOCKWAVE
## Decentralized Content Sharing Dapp 

Blockwave is a decentralized content sharing dapp where users can share their posts and followers can
pay directly to their favorite influencers using their wallet addresses. The dapp uses a decentralized
architecture and integrates with user-friendly UI, and sanity studio to store data like user profiles,
posts, comments, and wallet addresses. The dapp also allows users to mint NFTs and set their profile
picture, which will be associated with their account in sanity.


## Features 
*  user authentication with Metamask Wallet.
*  nft minting for profile picture.
*  event ticketing page to buy tickets for events.
*  post upload and association with user's wallet address. 
*  access to likes/dislikes/ commenting on posts.
*  creating,  selling and buying of event tickets using smart contracts.


## Architecture
![blockwave 2 drawio](https://user-images.githubusercontent.com/125735215/235324349-34ca0594-d35d-4d6f-a2f0-6d0e04525053.png)

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

**NFT profile smart contract**

NftProfile is a Solidity smart contract for creating and managing non-fungible tokens (NFTs)
that represent profiles. It extends the ERC721URIStorage contract from the OpenZeppelin library
to provide the functionality for creating NFTs and storing their metadata. In addition, it defines a
custom function for setting the profile picture of a token.
Usage
To use the NftProfile contract, you can import it into your Solidity code as follows:
import "path/to/NftProfile.sol";
Then, you can create a new instance of the contract and call its functions as needed:
NftProfile nftProfile = new NftProfile(); // Create a new NFT uint256 tokenId = nftProfile
.createNFT("https://example.com/token-123", "https://example.com/image-123"); // Set the profile
picture for an NFT nftProfile.setProfilePicture(tokenId);
Functionality
The NftProfile contract inherits from ERC721URIStorage and adds the following functionality:
• Create NFTs
The createNFT function creates a new NFT with a given tokenURI and imageURI and returns its ID:
function createNFT(string memory tokenURI, string memory imageURI) public returns (uint256)
• Set Profile Picture
The setProfilePicture function sets the profile picture for an existing NFT with a given tokenId:
function setProfilePicture(uint256 tokenId) public
Events
The NftProfile contract emits the following events:

• ProfilePictureSet - emitted when the profile picture for an NFT is set.
• TokenImageURISet - emitted when the image URI for an NFT is set.

**Event Ticketing Smart Contract**

This smart contract is used for creating events and issuing tickets on the Ethereum blockchain. It is
based on Solidity version 0.8.17 and uses two contracts from the OpenZeppelin library: ERC1155 for
creating tokens and Ownable for adding ownership and access control.
Event Structure
Within this contract, there is a structure called "Event" that has the following properties:
• totalSupply: total number of tickets available for the event
• remainingSupply: number of tickets still available for the event
• price: the price of each ticket
• startDate: the start date of the event
• endDate: the end date of the event
This structure is used to define and keep track of different events and their ticket details within the
contract.
Creating Events
To create a new event, the contract owner can call the createEvent function. This function takes the
following parameters:
• _eventId: the ID of the event to be created
• _totalTickets: the total number of tickets available for the event
• _ticketPrice: the price of each ticket
• _startDate: the start date of the event
• _endDate: the end date of the event
Before creating the event, several "require" statements are included which are conditions that must
be met for the event to be created:
1. The total number of tickets must be greater than zero
2. The ticket price must be greater than zero
3. The start date of the event must be in the future
4. The end date of the event must be after the start date

If all the conditions are met, the function will create a new event with the specified details and store
it in the _events mapping defined earlier.
Event Ticket Minting
After an event is created, the contract owner can mint tickets for that event by calling the _mint
function. This function takes the following parameters:
• to: the address of the recipient of the minted tickets
• id: the ID of the event for which the tickets are being minted
• amount: the number of tickets to be minted
• data: optional data to be included with the ticket minting
This function will create and mint the specified number of tickets for the given event ID and
transfer them to the recipient address.
Access Control
The Ownable contract is used to add ownership and access control to this contract. The contract
owner can create events, mint tickets, and perform other administrative functions.
Base URI
This contract uses a base URI for the metadata of the NFTs created by this contract. The URI is set
to "https://blockwave.com/tickets/{id}". The "{id}" part of the URI will be replaced with the actual
ID of the NFT, which provides more information about the NFTs and makes them easier to identify



