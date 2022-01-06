# Step01 - Hardhat TypeScript HelloWorld Manual

## Reading Material

- [Etherem Developmentdocumentation](https://ethereum.org/en/developers/docs/)
- [Hardhat documentation](https://hardhat.org/getting-started/)

## Steps to code

1. Create new directory using `mkdir step01_hardhat_typescript_helloworld_manual`
2. Navigate to the newly created directory using `cd step01_hardhat_typescript_helloworld_manual`
3. Initiate a npm package using `npm init --yes`
4. Install hardhat using `npm install --save-dev hardhat`
5. Create a simple hardhat project using `npx hardhat`
6. Install required dependancies using `npm install --save-dev "hardhat@^2.8.0" "@nomiclabs/hardhat-waffle@^2.0.0" "ethereum-waffle@^3.0.0" "chai@^4.2.0" "@nomiclabs/hardhat-ethers@^2.0.0" "ethers@^5.0.0"`
7. Install required dependancies using `npm install --save-dev ts-node typescript` and `npm install --save-dev chai @types/node @types/mocha @types/chai`
8. Update "hardhat.config.js" to "hardhat.config.js"

   - Plugins must be loaded with import instead of require.
   - You need to explicitly import the Hardhat config functions, like task.
   - If you are defining tasks, they need to access the Hardhat Runtime Environment explicitly, as a parameter.

   ```ts
   import { task } from 'hardhat/config';
   import '@nomiclabs/hardhat-waffle';

   import '@typechain/hardhat';
   import '@nomiclabs/hardhat-ethers';

   // This is a sample Hardhat task. To learn how to create your own go to
   // https://hardhat.org/guides/create-task.html
   task('accounts', 'Prints the list of accounts', async (args, hre) => {
     const accounts = await hre.ethers.getSigners();

     for (const account of accounts) {
       console.log(await account.address);
     }
   });

   // You need to export an object to set up your config
   // Go to https://hardhat.org/config/ to learn more

   /**
    * @type import('hardhat/config').HardhatUserConfig
    */
   module.exports = {
     solidity: '0.8.4',
   };
   ```

9. Create "tsconfig.json"

   ```json
   {
     "compilerOptions": {
       "target": "es2018",
       "module": "commonjs",
       "strict": true,
       "esModuleInterop": true,
       "outDir": "dist",
       "resolveJsonModule": true
     },
     "include": ["./scripts", "./test", "./typechain"],
     "files": ["./hardhat.config.ts"]
   }
   ```

10. Update "scripts/sample-script.js" to "scripts/sample-script.ts"

    ```ts
    import { run, ethers } from 'hardhat';
    async function main() {
      const Greeter = await ethers.getContractFactory('Greeter');
      const greeter = await Greeter.deploy('Hello, Hardhat!');
      await greeter.deployed();
      console.log('Greeter deployed to:', greeter.address);
    }
    main()
      .then(() => process.exit(0))
      .catch((error) => {
        console.error(error);
        process.exit(1);
      });
    ```

11. Update "test/sample-test.js" to "test/sample-test.ts"

    ```js
    import { ethers, waffle } from 'hardhat';
    import { expect } from 'chai';
    describe('Greeter', function () {
      it("Should return the new greeting once it's changed", async function () {
        const Greeter = await ethers.getContractFactory('Greeter');
        const greeter = await Greeter.deploy('Hello, world!');
        await greeter.deployed();
        expect(await greeter.greet()).to.equal('Hello, world!');
        const setGreetingTx = await greeter.setGreeting('Hola, mundo!');
        await setGreetingTx.wait();
        expect(await greeter.greet()).to.equal('Hola, mundo!');
      });
    });
    ```

12. Install dependencies using `npm install --save-dev typechain @typechain/hardhat @typechain/ethers-v5`

13. `tsc`

14. Complie the app using `npx hardhat compile` it will compile the solidity code and genrate its byte code in abi.
15. Test the app using `npx hardhat test`
16. Deploy the app using `npx hardhat run scripts/sample-script.js` this will deploy the app to temp local blockchain which can't be accessed just deployment success message will be recieved.
17. Use `npx hardhat node` to create a local blockchain and it will list multiple coounts
18. Use `npx hardhat run scripts/sample-script.js --network localhost` to deploy on the blockchain created by above step.
19. Update "scripts/sample-scripts.js" to test the app

    ```js
    console.log('Get Data = ', await greeter.greet());
    const txt = await greeter.setGreeting('Hello Hassan');
    await txt.wait();
    console.log('After = ', await greeter.greet());
    ```
