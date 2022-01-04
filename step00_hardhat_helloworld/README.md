# Hardhat HelloWorld

## Reading Material

- [Etherem Developmentdocumentation](https://ethereum.org/en/developers/docs/)
- [Hardhat documentation](https://hardhat.org/getting-started/)

## Steps to code

1. Create new directory using `mkdir step00_hardhat_helloworld`
2. Navigate to the newly created directory using `cd step00_hardhat_helloworld`
3. Initiate a npm package using `npm init --yes`
4. Install hardhat using `npm install --save-dev hardhat`
5. Create a simple hardhat project using `npx hardhat`
6. Install required dependancies using `npm install --save-dev "hardhat@^2.8.0" "@nomiclabs/hardhat-waffle@^2.0.0" "ethereum-waffle@^3.0.0" "chai@^4.2.0" "@nomiclabs/hardhat-ethers@^2.0.0" "ethers@^5.0.0"`
7. Complie the app using `npx hardhat compile` it will compile the solidity code and genrate its byte code in abi.
8. Test the app using `npx hardhat test`
9. Deploy the app using `npx hardhat run scripts/sample-script.js` this will deploy the app to temp local blockchain which can't be accessed just deployment success message will be recieved.
10. Use `npx hardhat node` to create a local blockchain and it will list multiple coounts
11. Use `npx hardhat run scripts/sample-script.js --network localhost` to deploy on the blockchain created by above step.
