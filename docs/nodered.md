# Node-RED

## Node-RED Essentials

Resource Used: [Node-RED Essentials](https://youtube.com/playlist?list=PLyNBB9VCLmo1hyO-4fIZ08gqFcXBkHy-6)

1. [Introduction](https://youtu.be/ksGeUD26Mw0)
2. [Editor Components](https://youtu.be/veiNb6Y0ERg)
3. [Creating a Flow](https://youtu.be/46Ak61c_ymc)
4. [Wiring Node](https://youtu.be/_ST7fiBLlfw)
5. Editing Nodes
6. Deploying Flows
7. Information Sidebar
8. Debug Sidebar
9. Configuration Nodes Sidebar
10. Context Sidebar
11. Subflows
12. Working with Context
13. Introduction to Messages
14. Working with Messages
15. Message Sequences
16. Routing Messages
17. Managing Messages
18. Merging Flows
19. Grouping Nodes

### Introduction

* flow based programming tool
* browser based
* built on top of node.js

### Editor Components

* 4 areas of the editor

    * header (menu, deploy button)
    * sidebar (info, debug, context)
    * main workspace
    * palette

### Creating a Flow

* To create a flow, drag inject node on to the workspace.
* Then, add debug node to the workspace.
* Drag a line from the inject node _timestamp_ to debug node _msg.payload_.
* For something to happen, you need to click the Deploy button.
* Then, click on the button on the left hand side of the _timestamp_ node to inject the _timestamp_ into the _msg.payload_.
* Now, add _function_ node to add JavaScript code that gets run against each message passing through.

## Node-RED - Cellular Routers

### [Building Custom Nodes for Node.js or Node-RED](https://icr.advantech.cz/support/faq/detail/building-the-custom-nodes-for-node-js-node-red)

_Please Note_: The notes below are for building nodes written in JavaScript only.

- Using a Linux OS (I used Ubuntu 20.04 LTS)
- First, make sure your system is up-to-date via `sudo apt-get update`
- Next, install the Node Package Manager (`npm`) via `sudo apt-get install npm`
- Once, the install is finished, you should have a `.node-red` directory.
- You will need to run the install command for the desired node in the `.node-red` directory.
- _NOTE_: I have found that if you do not any dependencies will not install correctly.
- If you are not already in the `.node-red` directory, please `cd` into via `cd .node-red/`
- For this example, I wanted to install the `node-red-contrib-azure-iot-hub` node.
- I located the node I wanted [here](https://www.npmjs.com)
- Once you are at the site, just search for the node you are needing and click on the node name.
- More specifically, here is the link to [My Example](https://www.npmjs.com/package/node-red-contrib-azure-iot-hub)
- Once you are on the page, you will see a lot of information on the node, such as any dependencies.
- After ensuring this was the node I needed, I installed it via `npm --global-style install node-red-contrib-azure-iot-hub`
- Once the node was installed on my Ubuntu machine, I navigated to my `node_modules` folder.
- After doing a `ls`, I could see the `node-red-contrib-azure-iot-hub` folder.