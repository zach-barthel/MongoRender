# MongoRender
Code for testing Mongo DB by deploying to Render. Needs DB access keys. It can be used to deploy a working app but it cannot access a Mongo DB without proper keys. This wassmade for a class demo and assumes that the steps for building the database have been followed exacty as instructed in class.
<p>The (alternative) MongoTest repository (private) is an exact copy of this but with access keys so that it can be used to deploy a working app which can access a Mongo DB.
<p>This code should work with the correct URI assuming that on the DB side there is an item <font color=red>partID: '12345'</font>. If your database does not have any item with that key-value pair then you will not get any return (it will be null). So:
<p>
Make sure that the URI you are using is correct. It has to have the user-password of the user you have created for Mongo as well as the rest of the URI which is produced by Mongo for you. Just changing the user-password part on "my" URI is not going to work; you have to use your own DB URI.
<p>
The database name and collection are hardwired in my code:
<br>
const database = client.db('ckmdb');
<br>
const parts = database.collection('cmps415');
<br>
at lines 38,39. If you have named your database and collections differently, then you need to update these lines as well.

<p>The query in the code is also hardwired to
const query = { partID: req.params.item };
If you are not using a "partID" field then make sure to update this in the code accordingly. Or, create an entry in your DB which has a partID:xyz pair so that there is something to find when looking for xyz.

<p>Make sure that you have added the IP address which your service is using for DB network access (or 0.0.0.0 for universal access) so that requests from any address will not be bounced.

<p>Test your setup from Codespaces first before going to Render. Codespaces is only for testing but it is faster and you have console access.
