---
layout: post
title: Constructing ERC20 token that would violate Howey test yet would protect investor more than regulator does. Part 1: Security.
---

# Constructing ERC20 token that would violate Howey test yet would protect investor more than regulator does. Part 1: Security.

## Motivation

Money was monopolised by state for more than 100 years now.  Every attempt to issue private money was prosecuted, usually changing the law as it suited those, in power. 

Cryptocurrencies provide the safe haven from regulation attempts since 2009.

Much of progress for last 400 years can be attributed to a single organizational invention: the corporation.

> A corporation is a company or group of people authorized to act as a single entity (legally a person) and recognized as such in law.
> …
> Registered corporations have legal personality and are owned by shareholders whose liability is generally limited to their investment. Shareholders do not typically actively manage a corporation; shareholders instead elect or appoint a board of directors to control the corporation in a fiduciary capacity. In most circumstances, a shareholder may also serve as a director or officer of a corporation.
> [https://en.wikipedia.org/wiki/Corporation](https://en.wikipedia.org/wiki/Corporation)

It was perfected even more by opening the investment opportunity for wider and wider audience.  I’d guess,much of the US development in 19th century was due to pooling of capital into new ventures, making more experimentation possible and, thus, creating more wealth, and more possibilities to invest.

Yet, that window of opportunity was closed to the general public by The Securities Act of 1933, which limited the opportunity for early stage investment just to a tiny slim of already wealthy people.

The introduction of Ethereum platform and the ERC20 token standard resulted in proliferation of ICO’s. ICO opened the opportunity to participate in a high risk, high return early stage investing,for everyone able to launch an Ethereum wallet.

Still, the state wants to protect its monopoly power and pushes the regulation forward.  The most recent prominent example is _SEC’s Report of Investigation Pursuant to Section 21(a) of the Securities Exchange Act of 1934: The DAO_ ([https://www.sec.gov/litigation/investreport/34-81207.pdf](https://www.sec.gov/litigation/investreport/34-81207.pdf))

In this series of posts I’d show

- How to easy is to construct a token, that would be a security
- How to add investor protection at least on the same level as a regulated security provides
- That regulation, prohibiting the issuing securities on smart contracts, doesn’t provide any additional investor protection, but only limits the high-risk high-return investment opportunities to the wealthy.


## Howey test

> 2. For purposes of the Securities Act, an investment contract (undefined by the Act) means a contract, transaction, or scheme whereby a person invests his money in a common enterprise and is led to expect profits solely from the efforts of the promoter or a third party
> [https://supreme.justia.com/cases/federal/us/328/293/case.html](https://supreme.justia.com/cases/federal/us/328/293/case.html)

Ok, I’m not a lawyer, I’m just a mere software developer, so let me get a checklist for this:

> Under the Howey Test, a transaction is a security (or investment contract) if:
> 
> - It is an investment of money
> - There is an expectation of profits from the investment
> - The investment of money is in a common enterprise
> - Any profit comes from the efforts of a promoter or third party
> 
> [https://hackernoon.com/did-the-sec-just-throw-away-the-howey-test-df56784b0f38](https://hackernoon.com/did-the-sec-just-throw-away-the-howey-test-df56784b0f38)

Let’s take it step by step.

## It is an investment of money

By using a [fairly standart construct](https://github.com/OpenZeppelin/zeppelin-solidity/blob/5aba967db9bbff2089c1dcc855d9d5e83b293389/contracts/crowdsale/Crowdsale.sol#L64) we’re creating a `Token/Crowdsale` that’s exactly “an investment of money” 

## There’s an expectation of profits from the investment

This expectation is usually set in a whitepaper or another form of promotional material.  Even if the authors claim that there should be no expectation of profits, contributors usually expect to resell the token at a higher value.

In any case, we can explicitly violate it by allowing token to pay dividends.  For example, we can reuse this code [https://medium.com/@weka/dividend-bearing-tokens-on-ethereum-42d01c710657](https://medium.com/@weka/dividend-bearing-tokens-on-ethereum-42d01c710657)

## The investment of money is in a common enterprise

Check this analysis of SEC report

> **“Common enterprise” is a simple inquiry when funds are pooled** – The SEC did not even separately discuss this element. It just asserted there was a common enterprise and observed in passing that investor funds were pooled to fund projects.
> [https://www.lexology.com/library/detail.aspx?g=3ea81ec0-bfdb-4dca-ac24-0a306cd63c99](https://www.lexology.com/library/detail.aspx?g=3ea81ec0-bfdb-4dca-ac24-0a306cd63c99)

Enough said.

## Any profit comes from the efforts of a promoter or third party

See another definition of a common enterprise:

> In the context of an investment contract, a “common enterprise” is defined as an enterprise in which the fortunes of the investor are interwoven with and dependent upon the efforts and success of those offering or selling the investment or of third parties.
> [https://definitions.uslegal.com/c/common-enterprise/](https://definitions.uslegal.com/c/common-enterprise/)

I understand this, that a person can just make an investment transaction, lay back, and relax.  Other people, for example token project directors or token project officers will do the value-added work, that will, finally, generate dividends.

That goal is also achieved by inserting a dividend clause into our contract.

Note that voting is not considered a “significant effort”:

> **Voting rights are not significant efforts of investors** – Holders of DAO Tokens had rights to vote on projects before funds were deployed for projects, but this was not enough to make token holders actively involved in managing the business. This may not be a huge surprise (for example, voting rights are one of the most notable features of stock, which is widely regarded as a security), but it is a question we have heard several times.
> [https://www.lexology.com/library/detail.aspx?g=3ea81ec0-bfdb-4dca-ac24-0a306cd63c99](https://www.lexology.com/library/detail.aspx?g=3ea81ec0-bfdb-4dca-ac24-0a306cd63c99)

For more detailed analysis, I refer you to the [SEC Report](https://www.sec.gov/litigation/investreport/34-81207.pdf) itself.

## Conclusion

It's trivial to construct an ERC20 token that would _definitely_ be considered a securities by the US regulators.

In the next post I'll describe how the same construct can provide same or better investor protection than existing law (making regulation an extremely expensive device which has the only rational purpose: to stop innovation)

