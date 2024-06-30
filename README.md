# Degen-Token-ERC-20-Unlocking-the-Future-of-Gaming
create a ERC20 token and deploy it on the Avalanche network for Degen Gaming
# DegenToken (ERC-20): Unlocking the Future of Gaming

DegenToken is an ERC-20 token deployed on the Avalanche network for Degen Gaming. This token can be earned by players in their game and exchanged for rewards in their in-game store, enhancing player loyalty and retention.

## Functionality

- **Minting new tokens**: The platform can create new tokens and distribute them to players as rewards. Only the owner can mint tokens.
- **Transferring tokens**: Players can transfer their tokens to others.
- **Redeeming tokens**: Players can redeem their tokens for items in the in-game store.
- **Checking token balance**: Players can check their token balance at any time.
- **Burning tokens**: Anyone can burn tokens that they own and no longer need.

## Smart Contract

The smart contract is implemented using Solidity and the OpenZeppelin library for secure and standard ERC-20 functionality.

### Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract DegenToken is ERC20, Ownable {

    constructor() ERC20("DegenToken", "DGN") {}

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function redeem(address from, uint256 amount) public onlyOwner {
        _burn(from, amount);
    }
}
