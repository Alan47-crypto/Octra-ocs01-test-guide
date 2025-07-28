# How to Set Up and Run Octra's ocs01-test

This guide provides step-by-step instructions for installing, configuring, and running the **ocs01-test** CLI tool on an Ubuntu system. This tool is designed to interact with the OCS01 smart contract located at the address:  
`octBUHw585BrAMPMLQvGuWx4vqEsybYH9N7a3WNj1WBwrDn`.

---

## Prerequisites

You must have Rust installed on your system. If you don't, open your terminal and run:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

---

## 🚀 Step-by-Step Installation and Setup

Follow these steps in order. Each command is designed to be run from your terminal.

### **Step 1: Get the Source Code**

First, download the source code from GitHub and navigate into the project's directory.

```bash
git clone https://github.com/octra-labs/ocs01-test.git
cd ocs01-test
```

---

### **Step 2: Build the Executable**

From inside the `ocs01-test` directory, compile the project. This will create a production-ready binary file.

```bash
cargo build --release
```

---

### **Step 3: Create a Secure Runtime Directory**

Next, create a clean, separate folder in your home directory to run the tool. This keeps your sensitive wallet file separate from the Git repository.

While still inside the `ocs01-test` directory, run:

```bash
# Create a new directory named 'octra-cli-test' in your home folder
mkdir ~/octra-cli-test

# Copy the compiled binary into the new directory
cp ./target/release/ocs01-test ~/octra-cli-test/

# Copy the required contract interface file into the new directory
cp ./EI/exec_interface.json ~/octra-cli-test/
```

---

### **Step 4: Navigate to Your New Runtime Directory**

Move into the clean directory you just created. All remaining steps will take place here.

```bash
cd ~/octra-cli-test
```

---

### **Step 5: Create the Wallet Configuration File**

Run the command below to create the `wallet.json` file with the necessary template.

```bash
cat <<EOF > wallet.json
{
  "priv": "YOUR_B64_PRIVATE_KEYS",
  "addr": "YOUR_OCT_ADDRESS",
  "rpc": "https://octra.network"
}
EOF
```

---

### **Step 6: Add Your Credentials**

You must now securely edit the file to add your wallet details. We'll use the nano text editor.

```bash
nano wallet.json
```

Inside the editor, make the following changes:

- Replace `YOUR_B64_PRIVATE_KEYS` with your Base64 encoded private key.
- Replace `YOUR_OCT_ADDRESS` with your Octra wallet address.
- **Do not change** the `rpc` value.

To save and exit, press `Ctrl + X`, then `Y` to confirm, and finally `Enter`.

---

## ▶️ Running the Tool

Congratulations! Your setup is complete. To run the application, simply execute the following command from your `~/octra-cli-test` directory:

```bash
./ocs01-test
```

An interactive menu will appear, allowing you to test the smart contract. Test all 14 parameters by writting choice (eg. 1 for greeting) and enter then follow on screen instructions.
![Interactive Menu](https://github.com/Alan47-crypto/Octra-ocs01-test-guide/blob/main/Screenshot%202025-07-28%20at%2016.09.52.png)
