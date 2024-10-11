# CatSignet: An OP_CAT Enabled Bitcoin Signet

### **What is CatSignet?**

CatSignet is an open-source, OP_CAT-enabled Bitcoin signet network designed as a public good for the Bitcoin community. It serves as a testing environment where developers and builders can experiment with innovative protocols and scripts without incurring real transaction fees. CatSignet empowers anyone to build, test, and contribute to the evolving landscape of Bitcoin development.

### **Why CatSignet?**

- **Public Good Project**: CatSignet is developed for the community, by the community. It's an open platform where anyone can contribute, collaborate, and build upon.
- **Testing Environment**: As an OP_CAT-enabled testnet, CatSignet allows developers to run innovative tests and experiments on the network. This is especially valuable for testing new features or protocols that utilize OP_CAT before deploying them on mainnets like Fractal or even for testing Non OP_Cat specific features before deploying them on Bitcoin mainnet.
- **Cost-Effective Development**: By providing a sandbox environment, CatSignet enables developers to test their ideas without spending real fees. This reduces barriers to experimentation and accelerates innovation.
- **Bug Detection and Security**: Testing on CatSignet helps identify and fix bugs before deployment on mainnets, enhancing the security and reliability of new protocols and applications.

### **Who Can Contribute?**

**Everyone!** CatSignet is an open-source project, and we welcome contributions from developers, researchers, and enthusiasts across the globe. Whether you're an experienced Bitcoin developer or just starting out, your input and collaboration are valuable.

### **Features of CatSignet**

- **OP_CAT Enabled**: CatSignet supports the OP_CAT operation, unlocking advanced scripting capabilities and enabling complex protocols like BitVM and more.
- **Community Collaboration**: We foster a collaborative environment where ideas can be shared, discussed, and implemented collectively.
- **Faucet for Users**: To facilitate testing, we are deploying a faucet that provides testnet coins to users, making it easy to get started without any cost.

### **Use Cases**

- **Protocol Development**: Test new protocols and smart contracts that leverage OP_CAT functionality.
- **Application Testing**: Developers can run their applications on CatSignet to ensure they work correctly before deploying to mainnets.
- **Education and Learning**: CatSignet is an excellent resource for those looking to learn about Bitcoin scripting, OP_CAT, and blockchain development in a risk-free environment.

### **Get Involved**

- **Join the Community**: Connect with us on our [GitHub](https://github.com/Cat-Signet), or [Telegram](https://t.me/catsignet) channels to collaborate and stay updated.
- **Contribute to the Codebase**: Explore our open-source repositories and contribute code, documentation, or report issues.
- **Use the Faucet**: Access our faucet to obtain testnet coins and start experimenting on CatSignet.

## Joining the CatSignet

### Prerequisites

- Basic command-line interface skills
- Administrative permissions on your machine
- An internet connection

## Joining the CatSignet

### Prerequisites

- Basic command-line interface skills
- Administrative permissions on your machine
- An internet connection

### Step 1: Download and Install Bitcoin Core

You have two options to download and install Bitcoin Core:

- **Download the pre-built binaries**: You can download the pre-built binaries from the Bitcoin Inquisition release and use them directly.
- **Build from source**: You can build Bitcoin Inquisition from source code ([this release](https://github.com/bitcoin-inquisition/bitcoin/releases/tag/v27.0-inq)).

First, you need to download the appropriate Bitcoin Core binaries for your system. Below are links for commonly used systems:

- **Linux (aarch64)**: [Download v27.0 for aarch64](https://github.com/bitcoin-inquisition/bitcoin/releases/download/v27.0-inq/bitcoin-27.0-inq-aarch64-linux-gnu.tar.gz)
- **macOS (arm64)**: [Download v27.0 for arm64](https://github.com/bitcoin-inquisition/bitcoin/releases/download/v27.0-inq/bitcoin-27.0-inq-arm64-apple-darwin.tar.gz)

You can find links for other systems [here](https://github.com/bitcoin-inquisition/bitcoin/releases/tag/v27.0-inq).

After downloading the tar.gz file for your system, extract it using the following command:

```bash
tar -xzf bitcoin-27.0-inq-<platform>.tar.gz
```

Navigate to the extracted directory:

```bash
cd bitcoin-27.0-inq/bin
```

### Step 2: Configuration

Before starting your node, you need to create a configuration file to properly join the CatSignet.

1. **Create a new directory for your Bitcoin data:**

    ```bash
    mkdir -p ~/.bitcoin/catsignet
    ```

2. **Create the `bitcoin.conf` file:**

    ```bash
    nano ~/.bitcoin/catsignet/bitcoin.conf
    ```

3. **Add the following configuration to the file:**

    ```ini
    # General settings
    signet=1
    txindex=1
    server=1
    daemon=1
    deprecatedrpc=create_bdb

    # Signet settings
    [signet]
    # Custom signet challenge
    signetchallenge=5121027be9dab7dfc2d1b9aac03f883b9a229fc9c298770dec626b2acbf39e9b6e0e0c51ae
    # Add the seed node
    addnode=n.catsignet.com

    # RPC settings
    rpcbind=127.0.0.1
    rpcallowip=127.0.0.0/8
    rpcport=26657
    rpcuser=XXX
    rpcpassword=XXX
    ```

    Save and close the file. Replace `rpcuser` and `rpcpassword` with your desired credentials.

### Step 3: Start Your Node

Using `bitcoind`:
Run the following command in the terminal from the `bin` directory of your Bitcoin Core installation:

```bash
./bitcoind -datadir=~/.bitcoin/catsignet
```

This command will start your Bitcoin node and connect it to the CatSignet.

OR

Using `bitcoin-qt`: Run the following command in the terminal from the `bin` directory of your Bitcoin Core installation:

```bash
./bitcoin-qt -datadir=~/.bitcoin/catsignet
```

### Step 4: Verifying the Connection

After your node starts, you can verify it's properly connecting to the network by checking the peer information:

```bash
./bitcoin-cli -rpcport=26657 -rpcuser=XXX -rpcpassword=XXX getpeerinfo
```

You should see the CatSignet node `34.135.222.112` listed among the peers.

### Step 5: Create a Wallet

You can create a new wallet to interact with the CatSignet using the following command:

```bash
./bitcoin-cli -rpcport=26657 -rpcuser=XXX -rpcpassword=XXX -named createwallet wallet_name="test" descriptors=false
```

### Step 6: Generate a New Address

You can generate a new address to receive funds on the CatSignet:

```bash
./bitcoin-cli -rpcport=26657 -rpcuser=XXX -rpcpassword=XXX getnewaddress
```

### **Vision**

Empowering the Bitcoin community by providing the tools and platforms necessary for innovation. CatSignet aims to be the cornerstone for developers to push the boundaries of what's possible on Bitcoin, fostering an ecosystem of collaboration, learning, and advancement.
