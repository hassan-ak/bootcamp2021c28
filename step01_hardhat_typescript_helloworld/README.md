# Step01 - Hardhat typescript helloworld

## Reading Material

## Steps to code (Method 01)

1. Create new directory using `mkdir step01_hardhat_typescript_helloworld`
2. Navigate to the newly created directory using `cd step01_hardhat_typescript_helloworld`
3. Initiate a npm package using `npm init --yes`
4. Install hardhat using `npm install --save-dev hardhat`
5. Create a advance hardhat typescript project using `npx hardhat`
6. Install required dependancies using ` npm install --save-dev "hardhat@^2.8.0" "@nomiclabs/hardhat-waffle@^2.0.0" "ethereum-waffle@^3.0.0" "chai@^4.2.0" "@nomiclabs/hardhat-ethers@^2.0.0" "ethers@^5.0.0" "@nomiclabs/hardhat-etherscan@^2.1.3" "dotenv@^10.0.0" "eslint@^7.29.0" "eslint-config-prettier@^8.3.0" "eslint-config-standard@^16.0.3" "eslint-plugin-import@^2.23.4" "eslint-plugin-node@^11.1.0" "eslint-plugin-prettier@^3.4.0" "eslint-plugin-promise@^5.1.0" "hardhat-gas-reporter@^1.0.4" "prettier@^2.3.2" "prettier-plugin-solidity@^1.0.0-beta.13" "solhint@^3.3.6" "solidity-coverage@^0.7.16" "@typechain/ethers-v5@^7.0.1" "@typechain/hardhat@^2.3.0" "@typescript-eslint/eslint-plugin@^4.29.1" "@typescript-eslint/parser@^4.29.1" "@types/chai@^4.2.21" "@types/node@^12.0.0" "@types/mocha@^9.0.0" "ts-node@^10.1.0" "typechain@^5.1.2" "typescript@^4.5.2"`
7. Complie the app using `npx hardhat compile` it will compile the solidity code and genrate its byte code in abi.
8. Test the app using `npx hardhat test`
9. Deploy the app using `npx hardhat run scripts/deploy.ts` this will deploy the app to temp local blockchain which can't be accessed just deployment success message will be recieved.
10. Use `npx hardhat node` to create a local blockchain and it will list multiple coounts
11. Use `npx hardhat run scripts/deploy.ts --network localhost` to deploy on the blockchain created by above step.
12. Update "scripts/deploy.ts" to test the app

    ```js
    console.log('Get Data = ', await greeter.greet());
    const txt = await greeter.setGreeting('Hello Hassan');
    await txt.wait();
    console.log('After = ', await greeter.greet());
    ```
