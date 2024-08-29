<div align="center">
  <a href="https://github.com/Phala-Network/ai-agent-template-redpill">
    <h1>AI Agent Contract Template with RedPill</h1>
    <img height="320" src="./public/AI-Agent-Contract.jpg" />
    <br />
  </a>

  <p align="center">
    Host your AI Agent Contract on Phala's decentralized serverless cloud.
    <br />
    <a href="https://github.com/Phala-Network/ai-agent-template-redpill"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://wapo-testnet.phala.network/ipfs/Qmc7EDq1X8rfYGGfHyXZ6xsmcSUWQcqsDoeRMfmvFujih3?key=51f265212c26086c&chatQuery=When%20did%20humans%20land%20on%20the%20moon">View Demo</a>
    ·
    <a href="https://github.com/Phala-Network/ai-agent-template-redpill/issues">Report Bug</a>
    ·
    <a href="https://discord.gg/phala-network">Discord</a>
  </p>

  <h3>Architecure Overview</h3>
  <img height="320" src="./public/ai-agent-architecture.jpg" />
</div>

## 🤖 What Is This?!

<div align="center">
  <img height="240" src="https://www.jlwranglerforums.com/forum/attachments/zoolander-gif.325299/">
</div>

The RedPill AI Agent template is a **MINIMAL** template to build an AI Agent that can be hosted on Phala Network's decentralized hosting protocol. Unlike Vercel or other FaaS, it allows you to publish your AI Agent compiled code to IPFS and hosts it on a fully decentralized FaaS cloud with the following benefits:

- 💨 Ship Fast: Build and ship with familiar toolchain in minutes
- ⛑️ Secure: Execution guarded by rock solid TEE / Intel SGX
- 🔒 Private: Host API keys and user privacy at ease
- 💎 Unstoppable: Powered by IPFS and Phala's 35k+ decentralized TEE workers

[//]: # (<img width="320" src="https://media1.tenor.com/m/NBtFH5F9QTgAAAAd/what-is-my-purpose-butter.gif" />)

## Getting Started
### Prepare
Install dependencies
```shell
npm install
```

### Testing Locally
Create `.env` file and add your RedPill API Key
```shell
cp .env.example .env
```
Get an API Key from Redpill
> **Note**
> 
> There is a default RedPill API Key provided in the .env.example file. This API key is rate limited and if you run into an error that displays `Insufficient funds`, reach out to the Phala Team on [discord](https://discord.gg/phala-network).

- Go to https://red-pill.ai/dashboard and claim your API Key by swapping some ETH for wGPT at https://app.uniswap.org/explore/tokens/base/0x74F62Bc1961028C22b8080961c6534f4eDD49D6C
- Video Tutorial: https://youtu.be/ZoJwbLNhbWE

In `.env` file replace `YOUR_API_KEY` with your API Key
```text
REDPILL_API_KEY="YOUR_API_KEY"
```

Build your Agent
```shell
npm run build
```

Test your Agent locally
```shell
npm run test
```

Expected Test Results
```shell
INPUT: {"method":"GET","path":"/ipfs/CID","queries":{"chatQuery":["Who are you?"],"model":["gpt-4o"]},"secret":{"apiKey":"sk-D3rWzPAe16RIB8r8GptK9vi6ozuYEnHY4Lpg2L2lap465ROo"},"headers":{}}
{"apiKey":"sk-D3rWzPAe16RIB8r8GptK9vi6ozuYEnHY4Lpg2L2lap465ROo"}
GET RESULT: {
  status: 200,
  body: `{"message":"I'm an AI language model created by OpenAI, here to help answer your questions and provide information on a wide range of topics. How can I assist you today?"}`,
  headers: {
    'Content-Type': 'application/json',
    'Access-Control-Allow-Origin': '*'
  }
}
Now you are ready to publish your agent, add secrets, and interact with your agent in the following steps:
- Execute: 'npm run publish-agent'
- Set secrets: 'npm run set-secrets'
- Go to the url produced by setting the secrets (e.g. https://wapo-testnet.phala.network/ipfs/QmPQJD5zv3cYDRM25uGAVjLvXGNyQf9Vonz7rqkQB52Jae?key=b092532592cbd0cf)
```

### Publish Your AI Agent

Upload your compiled AI Agent code to IPFS.
```shell
npm run publish-agent
```

Upon a successful upload, the command should show the URL to access your AI Agent.
```shell
✓ Compiled successfully.
  1.51 KB  dist/index.js
Running command: npx thirdweb upload dist/index.js
This may require you to log into thirdweb and will take some time to publish to IPFS...

    $$\     $$\       $$\                 $$\                         $$\       
    $$ |    $$ |      \__|                $$ |                        $$ |      
  $$$$$$\   $$$$$$$\  $$\  $$$$$$\   $$$$$$$ |$$\  $$\  $$\  $$$$$$\  $$$$$$$\  
  \_$$  _|  $$  __$$\ $$ |$$  __$$\ $$  __$$ |$$ | $$ | $$ |$$  __$$\ $$  __$$\ 
    $$ |    $$ |  $$ |$$ |$$ |  \__|$$ /  $$ |$$ | $$ | $$ |$$$$$$$$ |$$ |  $$ |
    $$ |$$\ $$ |  $$ |$$ |$$ |      $$ |  $$ |$$ | $$ | $$ |$$   ____|$$ |  $$ |
    \$$$$  |$$ |  $$ |$$ |$$ |      \$$$$$$$ |\$$$$$\$$$$  |\$$$$$$$\ $$$$$$$  |
     \____/ \__|  \__|\__|\__|       \_______| \_____\____/  \_______|\_______/ 

 💎 thirdweb v0.14.12 💎

- Uploading file to IPFS. This may take a while depending on file sizes.

✔ Successfully uploaded file to IPFS.
✔ Files stored at the following IPFS URI: ipfs://QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc
✔ Open this link to view your upload: https://b805a9b72767504353244e0422c2b5f9.ipfscdn.io/ipfs/bafybeifukvkuyztltpq2gi55nswzvwkpgrwrogwykm4ymoqeymh2pxoukm/

Agent Contract deployed at: https://wapo-testnet.phala.network/ipfs/QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc

If your agent requires secrets, ensure to do the following:
1) Edit the ./secrets/default.json file or create a new JSON file in the ./secrets folder and add your secrets to it.
2) Run command: 'npm run set-secrets' or 'npm run set-secrets [path-to-json-file]'
Logs folder created.
Deployment information updated in ./logs/latestDeployment.json
```


> :information_source: Note that your latest deployment information will be logged to in file [`./logs/latestDeployment.json`](./logs/latestDeployment.json). This file is updated every time you publish a new Agent Contract to IPFS. This file is also used to get the IPFS CID of your Agent Contract when setting secrets for your Agent Contract.
>
> Here is an example:
> ```json
> {
>   "date": "2024-08-29T18:47:55.108Z",
>   "cid": "QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc",
>   "url": "https://wapo-testnet.phala.network/ipfs/QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc"
> }
> ```

<details>
<summary>New to Thirdweb?</summary>
We use <a href="https://thirdweb.com/dashboard/infrastructure/storage">thirdweb Storage</a> to host IPFS contents. If you are new to thirdweb, the command will guide you to create your account or login to your existing account from the browser.
</details>

> **Did Thirdweb fail to publish?**
>
> If ThirdWeb fails to publish, please signup for your own ThirdWeb account to publish your Agent Contract to IPFS. Signup or login at https://thirdweb.com/dashboard/
>
> Whenever you log into ThirdWeb, create a new API key and replace the default API Key with yours in the [.env](./.env) file.
>
> ```
> THIRDWEB_API_KEY="YOUR_THIRDWEB_API_KEY"
> ```


### Access the Published AI Agent

Once published, your AI Agent is available at the URL: `https://wapo-testnet.phala.network/ipfs/<your-cid>`. You can get it from the "Publish to IPFS" step.

You can test it with `curl`.

```bash
curl https://wapo-testnet.phala.network/ipfs/<your-cid>
```

### Add Secrets

By default, all the compiled JS code is visible for anyone to view if they look at IPFS CID. This makes private info like API keys, signer keys, etc. vulnerable to be stolen. To protect devs from leaking keys, we have added a field called `secret` in the `Request` object. It allows you to store secrets in a vault for your AI Agent to access.

To add your secrets,
1) Edit the [default.json](./secrets/default.json) file or create a new JSON file in the `./secrets` folder and add your secrets to it.
```json
{
  "apiKey": "YOUR_REDPILL_API_KEY"
}
```
2) Run command to set the secrets
```shell
npm run set-secrets
# or if you have a custom JSON file
npm run set-secrets <path-to-json-file>
```
Expected output:
```shell
Use default secrets...
Storing secrets...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   199    0    68  100   131    121    234 --:--:-- --:--:-- --:--:--   356
{"token":"5d9faaed6be5414a","key":"a3a8a4ef2c057d5c","succeed":true}

Secrets set successfully. Go to the URL below to interact with your agent:
https://wapo-testnet.phala.network/ipfs/QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc?key=a3a8a4ef2c057d5c
Log entry added to secrets.log
```

> :information_source: Note that all your secrets will be logged in file [`./logs/secrets.log`](./logs/secrets.log). This file is updated every time you add new secrets to your Agent Contract. If you have not published an Agent Contract, yet, this command will fail since there is not a CID to map the secrets to.
>
> Here is an example:
> ```text
> 2024-08-29T18:54:16.643Z, CID: [QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc], Token: [5d9faaed6be5414a], Key: [a3a8a4ef2c057d5c], URL: [https://wapo-testnet.phala.network/ipfs/QmaUbZgNz9dZ5eGm87DDqegRtcBV7RdosxizYQcfe2bHRc?key=a3a8a4ef2c057d5c]
> ```

The API returns a `token` and a `key`. The `key` is the id of your secret. It can be used to specify which secret you are going to pass to your frame. The `token` can be used by the developer to access the raw secret. You should never leak the `token`.

To verify the secret, run the following command where `key` and `token` are replaced with the values from adding your `secret` to the vault.
```shell
curl https://wapo-testnet.phala.network/vaults/<key>/<token>
```

Expected output:
```shell
{"data":{"apiKey":"<REDPILL_API_KEY>"},"succeed":true}
```

### Access Queries
To help create custom logic, we have an array variable named `queries` that can be accessed in the `Request` class. To access the `queries` array variable `chatQuery` value at index `0`, the syntax will look as follows:
```typescript
const query = req.queries.chatQuery[0] as string;
```
The example at https://wapo-testnet.phala.network/ipfs/Qmc7EDq1X8rfYGGfHyXZ6xsmcSUWQcqsDoeRMfmvFujih3?key=51f265212c26086c&chatQuery=When%20did%20humans%20land%20on%20the%20moon will have a value of `When did humans land on the moon`. `queries` can have any field name, so `chatQuery` is just an example of a field name and not a mandatory name, but remember to update your `index.ts` file logic to use your expected field name.

## FAQ

<details>
<summary><b>What packages can I use in the AI Agent server?</b></summary>
<ul>
  <li>Most of the npm packages are supported: viem, onchainkit, ….</li>
  <li>Some packages with some advanced features are not supported:</li>
  <ul>
    <li>Memory usage over 100MB</li>
    <li>Web Assembly</li>
    <li>Browser only features: local storage, service workers, etc</li>
  </ul>
</ul>
</details>

<details>
<summary><b>What’s the spec of the Javascript runtime?</b></summary>
<ul>
  <li>The code runs inside a tailored <a href="https://bellard.org/quickjs/">QuickJS engine</a></li>
  <li>Available features: ES2023, async, fetch, setTimeout, setInterval, bigint</li>
  <li> <a href="https://docs.phala.network/tech-specs/ai-agent-contract#wapojs/">Tech spec doc</a></li>
</ul>
</details>

<details>
<summary><b>Why is the serverless platform secure?</b></summary>
<ul>
  <li>Your AI Agent code on is fully secure, private, and permissionless. Nobody can manipulate your program, steal any data from it, or censor it.</li>
  <li>Security: The code is executed in the decentralized TEE network running on Phala Network. It runs code inside a secure blackbox (called enclave) created by the CPU. It generates cryptographic proofs verifiable on Phala blockchain. It proves that the hosted code is exactly the one you deployed.</li>
  <li>Privacy: You can safely put secrets like API keys or user privacy on Phala Network. The code runs inside TEE hardware blackboxs. The memory of the program is fully encrypted by the TEE. It blocks any unauthorized access to your data.</li>
  <li>Learn more at <a href="https://phala.network">Phala Network Homepage</a></li>
</details>

<details>
<summary><b>What's TEE / Intel SGX?</b></summary>
<ul>
  <li><a href="https://collective.flashbots.net/t/tee-sgx-wiki/2019">TEE/SGX wiki</a></li>
  <li><a href="https://collective.flashbots.net/t/debunking-tee-fud-a-brief-defense-of-the-use-of-tees-in-crypto/2931">Debunking TEE FUD: A Brief Defense of The Use of TEEs in Crypto</a></li>
</details>
