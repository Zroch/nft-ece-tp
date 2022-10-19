# NFT CTP ECE

- Clone the repo
- run `npm install`
- change you ABI if it's not the same we coded in class (in `src/contracts/ABI.json`)
- change the contract address in `src/App.js` line 6
- run `npm run start`
- enjoy!

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.4;

import "@openzeppelin/contracts@4.7.3/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts@4.7.3/access/Ownable.sol";
import "@openzeppelin/contracts@4.7.3/utils/Counters.sol";

contract TPE_CE is ERC721, Ownable {
    using Counters for Counters.Counter;

    Counters.Counter private _tokenIdCounter;

    constructor() ERC721("TPE_CE", "ECE") {
        _tokenIdCounter.increment();
    }

    function _baseURI() internal pure override returns (string memory) {
        return "https://ipfs.io/ipfs/Qma1mxm3py8JsWEmZJx6cv8UKSpGBMcQYpbDbHju2VRqjP/";
    }

    function safeMint() public {
        uint256 tokenId = _tokenIdCounter.current();
        _tokenIdCounter.increment();
        _safeMint(msg.sender, tokenId);
    }
}
