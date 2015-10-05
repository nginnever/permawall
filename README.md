# permawall

<h1>About</h1>

<p>This is an experiment in <a href="https://ipfs.io/">IPFS</a> - the InterPlanetary File System and the <a href="https://ipfs.io/">Ethereum</a> blockchain. This is a WIP. Adding posts will distribute the data p2p in an attempt to make something as simple as text (for now) persist.  Currently what you write here has no way of being censored or removed. As long as a computer has the app files and ethereum can resolve the current data state and assuming someone has it... and well I can't promise this will work and you will need a local ipfs and ethereum go client node running to use this.</a></p>



<h1>How This Works</h1>

<p>This site is built in Javascript with Angular MVC. All of the code here is either client side JS or browserified nodejs. This application is distributed by the IPFS protocol and connects to the Ethereum api to provide consensus on the current state of the posts on this wall.  The contents of this application are hashed and distributed with a DHT routing protocol. When a post is made you apend your post data to a json object and add the new object to ipfs making it ready to be requested via the DHT by other users. A transaction to a smart contract is then bundled to set the hash of the new object in the blockchain. Sending this transaction shouldn't cost too much but the contract will reject your post if you don't provide enough ether to pay the gas to set your data. All of the nodes running this application will then be able to resolve the same data from the last change to the wall from the blockchain and then download the data through the ipfs dht. </p>



<h1>Instuctions On Using</h1>

<p></p>



<h1>Caveats</h1>

<p>The data object will just continue to grow with every post.  This implies that every user has to download a copy of the database to use the application and DBs can get large. Solutions are needed. </p>

<h1>Bugs to fix</h1>

<p>Page doesn't reload data when refreshing on the wall. Long strings of text without spaces go out of bounds in the post box.</p>