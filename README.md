<img src="logo.png" alt="Distributed Ledger Consulting" height="50px">

# Committed Solutions

- [Tackling Blockchain Dilemmas (TBD)](https://github.com/Distributed-Ledger-Consulting/TBD-MCART)
- [James Bond(s)](https://github.com/niklasb/st)

# Smart Contract Conference: Talking Coders

"It's very attractive to the libertarian viewpoint if we can explain it properly. I'm better with code than with words though." While Nakamoto's code enabled a new world, we are reaching the point where we need words again. Not everybody is a coder. And even less are solidity developers. If we do not want (solidity) coders to be a new middleman we need to translate smart contracts into everyday English. We do not want to enable an elite group for the new world. Therefore this Hackathon will focus on 1) building together with lawyers and regulators and 2) present the results in a non-coder friendly way. Because it's time to talk. The code does not speak for itself. It only gets executed. But we are dealing with values beyond integers. It's not just a number anymore. It's a new type of value. And this value must be communicated not just transmitted.

## Expected Results and Restrictions

- Your solution should run on a local network on a single computer and it does not need to interact with the other solutions.
- The presentation of the solution should be non-coder friendly. You are not presenting for other coders but lawyers and regulators. Expect a restricted understanding of the possibilities and limitations of smart contracts and a basic understanding of blockchain technology.
- While we are keen to see the differences in your solutions, we are also interested in the limitations of the Ethereum blockchain to solve the challenge (if there are any). 
- You should be aware of the [ST-20](https://github.com/PolymathNetwork/polymath-core#st-20-interface-overview) standard and [ERC-1400](https://github.com/SecurityTokenStandard/EIP-Spec) standards by Polymath, but you are not enforced to use them. We want to focus on modeling a solution for the given problem and explaining the solution in a way that is reasonable for a lawyer and a regulator.
- Record the problems you have to face when working on a task without any standard solution and explain it in your presentation.
- We don't expect your smart contracts to be fully secure (though please do not create a public self-destruct function...I might use it), but you should be able to explain the security risks involved. 
- Your smart contracts do not have to be feature complete. You do not need to handle every single edge case that is implied in the challenge. Specifications might slightly change during the hackathon.
- Please pay special attention to problems that can not be solved on-chain and provide a suggestion for a solution without any implementation (or a dummy solution if necessary).
- Your source code and presentation material should live in a public GitHub repository and will be linked to this repository. 

## Organization

- One or two members of each team must present the solution on the last day
- Each team gets a lawyer to better understand the implications of the task
- While not mandatory we recommend defining responsibilities in your team
- The event is planned for three days, while the first day is reserved for understanding the task and its challenges. The second day is there for implementing a solution which should be presented on the last day.

# Challenge: A non-standard world

The basic idea of a Security Token is to represent ownership interests in assets. Since the asset market is highly regulated a Security Tokens must be able to deal with different kinds of restrictions and limitations (e.g. only known identities can transfer/receive tokens and you must apply rules based on the jurisdiction of the sender/receiver). Therefore we have to use a blockchain that allows enforcing a custom set of rules (smart contracts on Ethereum in our case) while we have to think about the problem of how to bridge the off-chain world (identities and their properties) to the on-chain world.

There are different kinds of securities but we want to focus on the most simple form: a bearer bond. Usually, you would face a prospectus describing the financial security for potential buyers. This written document is rather extensive, therefore we decided to extract the most interesting points that need explanation and discussion. In the end, we want to answer one question: What is stopping us from issuing securities on a blockchain?

While we recommend using the [OpenZeppelin](https://github.com/openzeppelin/openzeppelin-contracts) library for tasks like adding up numbers you do not have to use any STOs standards. We are interested in the problems arising without any clear standards. The resulting chaos is a feature, not a bug. It enables discussions and raises problem awareness. Welcome to a non-standard world. 

# Bearer Bonds: A brief overview

A bearer bond is a security used by companies to raise capital. It is a securitization of a claim of a creditor (the investor) to the debtor (the company/issuer). It is, therefore, a form of debenture bond. If a certificate (=security) is issued for a claim (e.g. interest and repayment claim), the holder of the certificate can request payment of due claims. "The right in the paper follows the right to the paper". This is important because § [793 BGB](https://www.gesetze-im-internet.de/bgb/__793.html) stipulates: 

"If someone has issued a deed in which he promises the holder of the deed to make a payment (debenture to the bearer), the holder may demand payment from him in accordance with the promise, unless he is not entitled to dispose of the deed. However, the issuer is also released by the payment to a holder who is not entitled to dispose of the document."

The debtor/issuer can therefore in principle make debt discharging payments to the holder of the document, even if the claim has already been transferred to a new creditor. At present, the deed must exist in paper form for this purpose (see § 793 (2) BGB: signature required). Therefore, a token cannot produce the legal effects described. Linking the claim with the token can only be made by contractual agreement, but (unlike with the deed) does not currently result from the law. This contractual link may be broken or ineffective or may not be transferred to the new creditor. This means that the ownership of the claim and the token may fall to different persons. The legal linking of the claim and the token is therefore absolutely necessary in order to benefit from the advantages of a digital version of the bearer bond. Without this legal linkage, there could potentially be situations where token holder and the owner of the claim are different persons, which is why these token would no longer be traded without the need for constant verification, because it cannot be assured that the tokenholder is still entitled to enforce the claim(s) at all.

The debtor can make debt discharging payments to the owner of the deed. The issuer of the bond undertakes to redeem the security after a fixed term.

# Task: Build your own STO

Your company (think of a nice name) wants to raise money for the best product in the world (name it). You discuss and decide that bearer bonds are a good idea. This means an investor pays your company the face value and gets a paper (security) in return. In the case of this STO, the investors waive the issue of a paper and accept a token instead. By the contractual conditions, the token has to perform the same function as the paper normally does.

## Requirements

- MUST use an ERC-20 compatible token for your STO
- MUST return the investment of an investor at the end of the term (after 10 years)
- MUST pay annual interest rates (4%)
- MUST be able to perform forced transfers for legal actions
- MUST use an on-chain whitelist for investors
- MUST offer an on-chain solution to purchase (and sell back) tokens
- MUST offer an on-chain voting/proposal mechanism (to update the contract, to change specific values)
- MUST enable to mint/burn tokens
- MUST be able to destroy (self-destruct) all your smart contracts
- MUST allow updating all contracts (functions as well as certain variables)
- MUST allow the possibility to be executed only through a specific interface (no implementation required)

## Bonus

- Enable confidential transactions and obfuscate the balance of accounts
- Attach the prospectus document as a .pdf to the token contract
- Pay your taxes on-chain (ask organizers for details)
- Transactions costs may be paid by the issuer of the STO

## Limits

- Only investors from Germany are allowed to invest (KYC)
- You are not allowed to raise more than 50,000,000 € (= 50,000,000 token)
- Minimal buy-in is 1000 tokens (only relevant for initial buy)
- Off-chains solution shall not be implemented but be assumed (offer a solution)
- Smart Contracts do not need to be feature complete, dummy functions are allowed, certain edge cases can be ignored (discuss with the organizers)

## Scenarios to handle

The following scenarios must all be handled by your solution. 

### Investor(s)

- [ ] There are 200 investors. Each of them wants to purchase 1000 tokens. The investors will use ETH (or a stablecoin) to purchase your token. All of this should work on-chain (you are allowed to use oracles).
- [ ] Once you bougt your tokens you have 14 days for a withdrawal. An investor decides to return his/her token after 2 days of keeping them. The issuer must pay the interest (3%) for these two days as well as get the investor the initial funds back.
- [ ] An investor wants to sell 50% of its token to a new investor that is not a token holder yet.
- [ ] An investor wants to sell 20% of its stack to another investor that is a token holder.
- [ ] An investor was forced to initiate a transaction. Burn the old tokens and mint new ones for the new address. Revert (this can be a mint/burn or a transfer) all transactions (hint: all deadlines stay the same (e.g. payout for interests)).
- [ ] A token holder has to pay all of his tokens to another investor (court order), but s/he resists/can't to sign the transaction. Enforce the transaction.
- [ ] An investor duly terminates the term and tries to sell his/her tokens after that to another token holder.
- [ ] An Investor tries to sell tokens but is not allowed to do so before holding it X days (these days should be a variable that you can update). Asset freezing.
- [ ] An investor wants to buy more tokens than the maximal limit. Buy as many as possible and return the rest of the ether to the investor.
- [ ] An investor wants to buy only 500 tokens but must buy at least 1000 tokens.
- [ ] If the issuer fails to pay an investor until the defined due date an investor can make a request (on-chain) which gives the issuer 3 days to react and pay the debt. If the issuer does not react every investor has the right to terminate the contract within 14 days. 

### Issuer

- [ ] Issuer duly terminates the term (3 months). Inform the investors and prepare the last payments and redemption.
- [ ] Issuer decides to update the interest rate and due date. A proposal is required and 75% of the issued supply must agree as well as the issuer itself. The first proposal fails the second one succeeds. The update can't be executed without a confirmation by the notary.
- [ ] The issuer found a critical security bug and wants to update the smart contract. No proposal required. The change must be documented.
- [ ] The issuer mints/burns tokens based on the investments.
- [ ] There are three different accounts with the highest privileges. One key is lost. Remove that account from the list of privileged accounts and a new privilged account.
- [ ] You have to distrubte 200,000 € (in Ether) to your investors. Buy ether and distribute the ether based on the tokens each account holds. Make sure to exclude accounts that are not able to receive funds (e.g. lost key or inactive account).

### Misc

- [ ] The STO failed because laws were broken. Since there is a right attached to the tokens you decide to delete all smart contracts associated with your STO. Your solution should resolve the dependencies between the contracts and allow a self-destruct only after all (final) payments were made.
- [ ] The price of a token should use Euro as a reference. Create a (simple) oracle like process to query the curent price of Ether in Euro to calculate the ether price per token.
- [ ] Extraordinary termination. Your company must face insolvency. Make a public announcement on the blockchain. (Could be also something else the main point is to do public signaling. This could be used for different cases.)
- [ ] An investor/group of investors proposes (they must own at least 5% of the issued supply) to update the due date. The majority of the investors (75%), as well as the issuer, has to support this proposal. (If all token holders and the issuer approve the whole contract can be updated)

## Further problems to consider

- How do you define deadlines? Based on block height? But the law refers to a calendar. 
- Imagine each country implements its standard. Would it still be possible to trade securities? Can we think of a bridge contract?
- The payout must be made in a legal tender currency (e.g. Euro). Can a stablecoin (e.g. DAI) be used here?
- There might be a legal need to erase or restrict access to written transaction data. 1) Is your solution able to delete data afterwords? Are you able to adjust the visibility of the amount of tokens per address?  

## Special cases

- The Ethereum protocol was hacked. it's not secure anymore. What is your backup system?
- Ethereum hard forked (again). Reason: Reverting a big hack. Which fork do you choose?
- Someone hacked your smart contract(s). How do you deal with/stop/control ongoing payments? The next payment should happen in a day.
