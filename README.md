// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.8.0/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.8.0/contracts/access/Ownable.sol";

contract ReyesToken is ERC20, Ownable {
    uint256 private constant UNIT = 1;

    constructor(string memory tokenName, string memory tokenSymbol) ERC20(tokenName, tokenSymbol) {
        // Reyes initialization logic can go here
    }

    function generate(address recipient, uint256 quantity) external onlyOwner {
        _mint(recipient, quantity * UNIT);
    }

    function burn(address account, uint256 quantity) external onlyOwner {
        _burn(account, quantity * UNIT);
    }

    function transferAssets(address sender, address recipient, uint256 quantity) external onlyOwner {
        _transfer(sender, recipient, quantity * UNIT);
    }
}
