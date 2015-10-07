#permachan

<h1>About</h1>
<p>This is a chan style message board. Unlike other sites, this application does not have a mod, an owner, or a server. This is an experiment in <a href="https://ipfs.io/">IPFS</a> - the InterPlanetary File System and the <a href="https://ipfs.io/">Ethereum</a> blockchain and a WIP. Adding posts will distribute the data p2p in an attempt to make something as simple as text (for now) persist.  Currently what you write here has no way of being censored or removed. As long as a computer has the app files and ethereum can resolve the current data state and assuming someone has it... and well I can't promise this will work and you will need a local ipfs and ethereum go client node running to use this. <a href="#/boards">Try it here!</a></p>

<h1>How This Works</h1>
<p>This site is built in Javascript with Angular MVC. All of the code here is either client side JS or browserified nodejs. This application is distributed by the IPFS protocol and connects to the Ethereum api to provide consensus on the current state of the posts on any given wall.  The contents of this application are hashed and distributed with a DHT routing protocol. When a post is made you apend your post data to a json object and add the new object to ipfs making it ready to be requested via the DHT by other users. A transaction to a smart contract is then bundled to set the hash of the new object in the blockchain. Sending this transaction shouldn't cost too much (~0.002 Ether currently) but the contract will reject your post if you don't provide enough ether to pay the gas to set your data (currently hard coded to 70,000 gas per TX). All of the nodes running this application will then be able to resolve the same data from the last change to the wall from the blockchain and then download the data through the ipfs dht. Check out the source at <a href="https://github.com/nginnever/permawall">github</a>.</p>

<h1>Instuctions On Using</h1>
<p><b>Run Locally</b>
<br>
<br>
Good News! Currently, if you are reading this it means that you are running ipfs!...(unles you are viewing this through a gateway) so just boot up an ethereum geth client with a small amount of ether on it and you're set. This currently default to account 0 or your primary account, should probably build a drop down menu to select different accounts. Just remember to add origins to the CORS accept in both ipfs and ethereum if you get resource sharing problems. 
<br>
<br>
In ipfs:
<code>export API_ORIGIN="http://localhost:8080"</code>
<br>
<br>
In geth:
<code>geth --rpc --rpccorsdomain "*"</code>
<br>
<br>
<b>Run on a hosted node</b>
<br>
<br>
Coming soon! <---- link goes here, something like client.voxelot.us... but not that... or anything .us probably :)
</p>

<h1>Anon</h1>
<p>IPFS does not guarentee any anonimty. IPFS and Ethereum are inhereintly public when it comes to sharing your connection info. In the future IPFS could have ways of dialing into the TOR network and Ethereum could develop some mixing service similiar to Darkcoin.</p>

<h1>In progress</h1>
<p>In the future we may have an IPFS/IPNS implementation that can connect browsers p2p so that gateways or IPFS installations would not be needed. Very interested in making this as easy as possible to use.  I have experimented with creating a server to host the nodes for people who do not know how to run one of their own. I need to fix a lot of bugs and build out more features. Would be cool if there was some ipfs connect info by the ether balance like number of peers etc. Just making text posts is boring... should probably add images and video soon. Getting a user system set up would be interesting, but probably not applicable for this site. Spread the data out to multiple objects and perhaps just allow old walls to fall off into obscurety while still maintaing the option to index any old data that has ever been posted to this application. Setting the scope variable by watching new blocks coming in and resolving the new data on the fly would be nice as well. Consider using mini mongo to store values in memory if ipfs local storage is too slow. I would also like to add a way for people to earn ether to fund their posts, maybe a tipping system? Still need to build client side pagination and sub threads like a normal chan site.</p>

<h1>Caveats</h1>
<p>The data object will just continue to grow with every post.  This implies that every user has to download a copy of the database to use the application and DBs can get large. Also everytime someone posts the new data hash to the blockchain they will be the only ones with that data on their ipfs node limiting the ability for others to connect to the current state of the data if they can't resolve that node in the routing. Might want to build in a system where the app tries to resolve the last N number of revisions to the data objects. Or maybe a federation of gateways that will be auto queried when a new hash is made. Solutions are needed. Feel free to comment or PR the <a href="https://github.com/nginnever/permawall">github!</a></p>

