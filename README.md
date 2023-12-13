# Smart Contract Wrapper - Standard Provisions

## Problem

Smart contracts operate in the same world as nation state legal systems (**Legal Systems**).

It doesn't matter what people agree, Legal Systems will assert jurisdiction over the transactions run by many smart contracts.  This is frequently annoying because the Legal System isn't well adjusted to dealing with smart contracts.

## Solution

A lot of people don't know that parties in trad contracts can agree to the way that the Legal System works for _their contract only as part of their contract_.  A common example is to depart from the "default" of going to court if there's a dispute by agreeing to go to arbitration as the final process to resolve any dispute.

In this way, we can use a contractual wrapper to "contract out" of the "Legal System default config" so that it's better adjusted to handling smart contracts.

## Harmony With Separation

Here's a basic principle for creating a "separation of concerns" between smart contracts and Legal Systems so that they conflict less:

> Smart contract code is the canonical description of the rights and obligations of transaction parties except to the extent that relevant legal systems alter them compulsorily.

There's more detail on the idea here: https://querylaw.com/uk/articles/code_is_law

## Standard Wrapper Provisions

Apart from separating concerns, there are other matters you might want to clarify so that the Legal System is less likely to mess with your elegant smart contract.

The goal here is to define legal provisions for a smart contract wrapper that you'd want to have most of the time.

## Separation Provisions

For the purposes of the legal wrapper, the outcome of the code’s operation (as distinct from the intent expressed by the code in writing) is agreed to represent the intent of the parties unless a legal system intervenes unavoidably, whereupon, to the fullest extent available under the law:

- (**Experts first**) to settle a legal dispute, the parties agree to discuss properly and then, failing that, a final and binding expert determination using an expert in cryptographically secure transaction systems;
- (**No blockchain remedies**) where the parties end up in legal dispute, they agree that neither will seek a specific performance remedy that would force a party to do something within the crypto system;
- (**No mistakes**)  the parties agree:
	- to conduct sufficient due diligence on the transaction to the extent that any unintentional outcome of the smart contract can be considered the result of their own negligence;
	- that they are sophisticated enough to make that statement; and 
	- based on the above, agree not to sue for mistake / fraud;
- (**limitation of liability**) the parties limit liability to each other to the fullest extent available, with the exception of liabilities caused by smart contract code;
- (**Compensation in fiat**) the parties agree that to the extent that there are damages payable they will be payable in fiat and the parties agree which fiat that is; and
- (**Governing jurisdiction**) the parties should agree to the governing law and courts to hear any claim.

Here are some other ideas for topics to address in the legal wrapper for specific types of transaction.

- (**Regulatory intervention**) The parties should share the risk, as is appropriate, for regulatory intervention.  Amounts payable under various indemnities should be determined by the legal layer.
- (**Unwinding transaction**) Where the smart contract leads to an unlawful / void legal outcome, the parties agree how to unwind / compensate for the legal failure of the smart code transaction.
- (**Liquidated damages**) The parties may agree how liquidated damages should be calculated for transaction-specific legal issues that arise.

## Admin Provisions

- Each party bears its own transaction costs.
- The entity represented by the person who signs a transaction is responsible for the transaction;
- [We should address who is to be communicated with (for a decentralised project) as a representative]; and
- code comments are not legally operative.

## Other Considerations

It's likely worth finding jurisdictions with courts that are less likely to intervene when parties agree to code as law.
