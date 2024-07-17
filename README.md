# Setting Up My Foundry Project

## Folder Setup

I made sure I was in the folder we created in the previous lesson. As a reminder, I ran the following commands:
```bash
mkdir foundry-f23
cd foundry-f23
```

Then, I typed the following commands:
```bash
mkdir foundry-simple-storage-f23
cd foundry-simple-storage-f23
```

**Tip:** I could speed up the `cd` command by pressing the Tab key after typing the first couple of letters of the destination name. The Tab key autocompletes commands/paths.

To open a new instance of VS Code with `foundry-simple-storage-f23` as the default path, I typed:
```bash
code .
```
I could then see the contents of this folder on the left sidebar.

I tried the following command to create a file:
```bash
touch randomFile.txt
```
To delete the file, I typed:
```bash
rm randomFile.txt
```
I found the terminal efficient for moving/opening/creating directories/files, changing paths, and generally running commands. I recommend going through a tutorial if you want to learn how to move extra fast.

## Creating a New Project

To create a new Foundry project, I ran:
```bash
forge init
```
This created a new Foundry project in my current working directory. If I wanted Foundry to create the new project in a new folder, I would type:
```bash
forge init nameOfNewFolder
```
I kept in mind that `forge init` expects an empty folder by default. If my folder was not empty, I had to run:
```bash
forge init --force
```
I made sure to configure my username and email if I encountered errors related to Git configuration:
```bash
git config --global user.email "yourEmail@provider.com"
git config --global user.name "yourUsername"
```
And that was it! My folder looked as follows:

- `lib` was the folder where all my dependencies were installed, such as:
  - `forge-std` (the Forge library used for testing and scripting)
  - `openzeppelin-contracts` (the most battle-tested library of smart contracts)
  - And many more, depending on what I needed/installed.
- `scripts` was a folder that housed all my scripts.
- `src` was the folder where I put all my smart contracts.
- `test` was the folder that housed all my tests.
- `foundry.toml` gave configuration parameters for Foundry.

There was more on these folders and files later. I right-clicked `src`, clicked on `New File`, and named it `SimpleStorage.sol`. I copied the code available [here](#).

One last thing, I deleted `Counter.s.sol`, `Counter.sol`, and `Counter.t.sol`. These files were a set of basic smart contracts that Foundry provided as a default when I created a new Foundry project.

## Improving Code Format in Visual Studio Code

When I first started, my code appeared as plain, dull, white text. This was easily fixed by using a Solidity extension.

### Recommended Solidity Extension
1. **Solidity by Nomic Foundation**

### Enabling Code Highlighting
If the code remained unhighlighted after installing the extension:
1. I pressed `Command + Shift + P` (macOS) or `Control + Shift + P` (Windows) to open the command bar.
2. I typed "Settings" and selected "Preferences: Open User Settings (JSON)".
3. I added the following setting:
   ```json
   { "editor.defaultFormatter": "NomicFoundation.hardhat" }
   ```
   For other extensions, I used:
   ```json
   "editor.defaultFormatter": "tintinweb.solidity-visual-auditor"
   ```
   or
   ```json
   "editor.defaultFormatter": "JuanBlanco.solidity"
   ```

### Other Useful Extensions
- **Even Better TOML**: Formatted the `foundry.toml` file to make it easier to read.
- **Inline Bookmarks**: Facilitated bookmarking the actual code for document review, auditing, log analysis, and keeping track of development notes and to-do lists. Notes and bookmarks were saved with my files and could be shared easily.

#### Default Trigger Words/Tags for Inline Bookmarks
```plaintext
@todo - (blue) General ToDo remark.
@note - (blue) General remark.
@remind - (blue) General remark.
@follow-up - (blue) General remark.
@audit - (red) General bookmark for potential issues.
@audit-info - (blue) General bookmark for information to be noted for later use.
@audit-ok - (green) Note that a specific line is not an issue even though it might look like one.
@audit-issue - (purple) Reference a code location where an issue was filed.
```
These tags were customizable and very handy for developing and auditing projects.

## Compiling Smart Contracts: A Guide to the Foundry Console Compilation Process

### Steps to Compile Smart Contracts
1. I opened a new terminal.
2. I typed `forge build` or `forge compile` to compile the smart contracts in my project.

### Post-Compilation
Once the compilation finished, I saw some new folders in the Explorer tab on the left side, including:
- **`out` Folder**: Contained the ABI of the smart contract along with the Bytecode and other useful information.
- **`cache` Folder**: Generally used to store temporary system files that facilitated the compilation process. For this course, I could safely ignore it.

### Terminal Efficiency Tips
Throughout my Solidity development/audit journey, I typed many terminal commands. To test changes, I probably had to rerun commands like `forge build`, `forge test`, or `forge script`. Typing these repeatedly was inefficient and time-consuming.

**Tip:** I used the up and down arrow keys to cycle through previously typed commands.
