# JavaScript DApp Template

This is a template for JavaScript Cartesi DApps. It uses node to execute the backend application.
The application entrypoint is the `src/index.js` file. It is bundled with [esbuild](https://esbuild.github.io), but any bundler can be used.


This DApp template implements a simple voting system. Here's what it does:

It maintains a proposals object to store all proposals.
It uses a hasVoted object to keep track of who has voted on which proposals.
The handle_advance function processes two types of actions:

create_proposal: Allows users to create new proposals.
vote: Allows users to vote "yes" or "no" on existing proposals.


The handle_inspect function supports three routes:

proposals: Returns all proposals.
proposal:<id>: Returns details of a specific proposal.
voter:<address>: Returns the voting history of a specific address.


The main loop remains the same, continuously checking for new requests from the rollup server.

This DApp simulates a basic blockchain-based voting system. Users can create proposals, vote on them, and query the state of proposals and votes. It includes features like preventing double voting and maintaining a record of all proposals and votes.
To use this DApp:

To create a proposal, send an "advance" request with a payload like: {"type": "create_proposal", "name": "Proposal Name", "description": "Proposal Description"}.
To vote on a proposal, send an "advance" request with a payload like: {"type": "vote", "proposalId": 0, "vote": "yes"}.
To query information, send an "inspect" request with a payload of "proposals", "proposal:0", or "voter:address".

This system could be extended to include features like proposal deadlines, vote weight based on token holdings, or more complex voting mechanisms. In a real blockchain application, you'd also need to consider security measures, such as signature verification for votes.