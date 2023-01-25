# Introduction

The global life insurance market is \~\$3tn[^1]. However, none of the
insurance companies service the web3 market. Given that the total market
cap of the currently listed tokens is about \$1tn (at its peak, it was
about \$3tn \... some large protocols like arbitrum, zksync, starknet,
scroll, etc yet to list), the addressable market is quite large

This represents a significant opportunity for a crypto native, global
life insurance protocol that accepts payments in tokens, and pays out
claims to a wallet.

In fact, with a lower cost structure (and hence lower premiums), we
believe web3 based life insurance could be a service that gives
"normies" a real use case to ramp on to crypto.

In the beginning, we will focus on DAOs where they insure members who
are working on critical aspects of their project. In the fiat world,
this is called Key Person Insurance

Once established, we will then move to insuring individuals as well.
Ideally in a privacy-preserving manner

# Why?

## Life insurance does not exist in web3

Insurance is key to mitigating risks. However, in crypto, there is
currently no option to buy using tokens, and receive claims payout to a
wallet.

## Lower premiums

A typical life insurance company uses 40% of the premiums to pay for
operational expenses + marketing. With non-upgradeable contracts and
"outsourced" KYC (Polygon ID or some such) + Claim Verification
(Kleros), we believe we can reduce that significantly. Hopefully, this
becomes a good use case where crypto makes a difference to the real
world

## Invest in web3 projects

Every insurance company is also an investor. The fact that we are crypto
native helps us take advantage of investment opportunities in the sector
as an investor, liquidity provider or parking funds in Aave/Compound

# Quote engine

Building a quote engine is priority number one. We plan to build and
test a quote engine for the USA (legal issues?), Germany, UK, Thailand,
Japan, India, Australia, Canada, Singapore, UAE, and South Africa. Once
ready, we can easily extend it to other countries since all we will need
is country specific data

# How will it work?

As we said earlier, our first product will be for DAOs.

1.  DAOs fill up a form giving details like their treasury wallet(s),
    own token address, AL wallet address, project discord, project
    twitter, website, founder twitter, and some such. We can calculate
    the current treasury value, percentage of that treasury held in
    their own token, average for the past 6 months, etc

2.  This information is then posted on a discussion forum for token
    holders to discuss. The idea here is to weed out obvious frauds.

    a.  A process will be followed to check the data given. For example,
        a confirmation on Twitter and Discord that the DAO is really
        asking access, the wallets are really theirs, etc

3.  Vote on Snapshot

4.  Once it passes, the data is then stored on-chain and their wallet
    (most probably a Gnosis Safe) is then given access

    a.  Ideally this is automated. Doing it manually adds an attack
        vector

5.  Members now find their DAO, and start their application.

    a.  The first step is to scan their Polygon ID (or similar)

        i.  If they do not have one, they are prompted to create

    b.  We then ask for access to Name, Address, Date of Birth, and
        Government ID number, if any (SSN, Aadhaar, National Insurance,
        etc)

    c.  PII (name, address, Govt Id) is then locked into a smart
        contract that only reveals this information to Kleros if there
        is a claim.

        i.  We only need country & city for our quote calculations

    d.  Additional information is asked (ht, wt, smoking, medical
        history, occupation, etc, etc) that helps determine a premium
        quote

        i.  All information given is accepted on "Utmost Good Faith"

        ii. Doing it this way has the additional benefit of not having
            to disclose personal information to the DAO

        iii. We also ask if they are OK to be doxxed if their claim is
             rejected the first time (might use something like https://arxiv.org/pdf/2005.03535.pdf)

             1.  If they say yes, we could reduce their premium and/or
                 give them a higher sum insured

    e.  Maximum sum insured is determined by the Treasury assets. Lower
        the assets, lower the sum that a person can be insured for

        i.  The idea is to reduce incentive for fraud

6.  When the DAO logs in with its AL wallet/Safe, it will see all the
    quotes. If they are reasonable, they can now set-up a Superfluid to
    continuously stream the premium

7.  Insurance cover stops if

    a.  No money in the wallet

        i.  Coverage will resume if stream restarts within 30 days

        ii. Beyond 30 days, a new application will have to be made

    b.  DAO terminates the stream/insurance

    c.  The insured individual initiates termination of insurance using
        their Polygon ID wallet

        i.  If not possible using Polygon ID wallet, then we will have
            to prompt them to login when they create quote

    d.  Treasury values fall below a certain amount OR if it falls
        suddenly by a significant percentage (indicating a hack).
        Amounts/Percentages can be decided by Governance

8.  If any details in the quote are edited, then a new quote is
    generated and needs approval by the DAO

    a.  This could typically happen if there is change in

        i.  Place of residence

        ii. Smoking status

        iii. etc

9.  If a claim is made,

    a.  DAO raises a claim and stakes 10% of the Sum Assured. This is to
        incentivise someone to raise an objection. In most
        circumstances, gaining the 10% will be more than gaining from a
        fraudulent claim

    b.  Details are sent to Kleros

        i.  DAO uploads the relevant documents like death certificate,
            doctor/coroner report, etc

        ii. Kleros verifies

            1.  Validity of the uploaded documents (personal info
                redacted).

                a.  Kleros will source and build a database of various
                    documents to ensure a validity check

            2.  Kleros jurors also fill up a form based on the data in
                the doctor's/coroner's report. This indicates cause of
                death and answers a set of questions to check with the
                answers given at the time of insurance (for example, if
                the insured indicated he is a non smoker, but the report
                says that he is)

    c.  If all is well, payment of sum assured + staked amount is made.
        If not, DAO is slashed. Appeal possible. See below

    d.  However, any one can raise an objection by staking 1% of Sum
        Insured

        i.  We send Kleros all the relevant information including the
            encrypted name, address, govt id, date of birth

        ii. Kleros then matches the Name and other personal details.
            This is done in a privacy preserving manner by mixing real
            data with 1000s of made up records. This won't save Satoshi
            Nakamoto from being doxxed, but should be enough privacy for
            most

    e.  If all well, payment is made and the objector is slashed. If
        not, DAO is slashed

        i.  Can appeal to a bigger juror bench

        ii. If the Insured has indicated that they are happy to be
            doxxed, we can use this to test validity of the claim as
            well

# Why only DAOs? Why not personal life insurance?

Ideally, we would like to build this with a much simpler wallet
interface, maybe even use Biconomy SDK or some such. One that can be
created using social logins and does not require seed phrases, etc.
Maybe even allow people to buy using fiat. Need some time to research
this

In any case, the quote engine and most contracts will be reusable for
personal life insurance as well

When we go down this route, wallet 'credit score' can also help
determine premiums/sum insured. Multiple options exist like degenscore,
masa, cred, spectral, RociFi, ArcX, Bird, etc

# Regulation

Regulations exist to protect consumers. Although, we do not plan to be
registered as an insurance company in any jurisdiction, we intend to
follow regulations with respect to funds, solvency ratio, investments,
etc

# Tokenomics

Some thoughts ... although MAY CHANGE SIGNIFICANTLY.

1.  grants/initial investment pays for development

2.  %age of the premium pays for maintenance

3.  Start with \$1mn pot (PremiumWallet) that keeps increasing due to
    premiums and investment returns

4.  Continuous auction using Variable Rate Gradual Dutch Auctions to
    increase our ability to underwrite

    a.  Price should not be below issue price

    b.  Dilutes team and initial investors

No airdrops. Contributoors will be AL, with min investment (\$1000?) to
increase ownership. For now, we do not envisage insurance buyers
participating in governance

-   Although involving them as a check on DAO decisions may be a good
    idea. For example, if DAO votes for an investment but insurance
    buyers have the ability to veto risky investments

    -   If vetoed, maybe the ppl who voted for it face some
        loss/slashing?

        -   Maybe this makes it too complex/impractical. Or has
            unintended consequences. idk

# Governance

The protocol itself is governance-minimised. However, we do need
governance for the following

1.  Approve DAOs that can apply for insurance

2.  Approve investments

Since most of the money raised will go into the PremiumWallet and almost
all the premiums (minus payouts ofc) act as returns, we expect strong
participation in governance.

# Partnerships

Have had a couple of conversations with Kleros, and they are keen to
work on this. If successful, they can potentially offer this service to
fiat insurance companies as well

Haven't spoken with Polygon ID as yet. But I know they are keen to
showcase their tech

[^1]: https://www.globaldata.com/store/report/life-insurance-market-analysis/
