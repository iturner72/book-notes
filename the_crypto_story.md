# The Crypto Story

by Matt Levine

*I, Ian Turner added this article to my book-notes repo in order to reference
during the gm.xyz/C/OnTheBrink Book Club. I will pitch the idea of making this
document both a place for notes, and a docket for the conversation. I will
probably take more notes on the trad fi comments than the crypto ones since I am
very much ignorant of financial vocab, but above average with crypto concepts*



# Notes

## Intro
* Joel Weber proposes that he is perhaps wrong about crypto and encourages his
    readers to understand this new technology that is here to stay.

# I Ledgers, Bitcoin, Blockchains
## A Life In Databases
* Modern life consists in large part of entries in databases.
* If you have money, what you have is an entry in your bank's database saying
    how much money you have. If you have a share of stock, what you have is
    generally an entry on a list - kept by the company or, more likely, some
    central intermediary (Depository Trust & Clearing Corp. DTCC). The DTCC owns
    most of the shares of most US companies on behalf of everyone else. If you
    own stock, what you have is an entry on DTCC's list entitling you to some of
    the shares DTCC holds, and it has an entry on a company's list of how many
    shares it owns.
* ...your ownership of that house is probably written down in some database; in
    the US this often means there's a record of your buying the house - your
    title - in a filing cabinet in the basement of some county clerk's office.
    (It's not a very *good* database.)
* We trust the keepers of the database
    + ...it means we have an abstract snse of trust in the broader system, the
        system of laws and databases and trust itself. It's a towering and
        underappreciated achievement of modernity that we mostly do trust the
        database-keepers, and that they mostly are trustworthy.
## B What If You Don't Like It?
* i. Distrust
    + But we don't always trust them, and they're not always trustworthy.
    + There are banks you can't trust to hold your money for you and places
        where you can't trust the rule of law to regulate them.
    + There are governments you can't trust not to seize your money from the
        banks, or falsify election results, or change the property registry and
        take your house.
* ii. Composability
    + These databases aren't always very good. Lots of the banking system is
        written in a very old computer language called Cobol...
    + What if we rewrote all the databases from scratch, in modern computer
        languages using modern software engineering principles, with the goal of
        making them interact with one another seamlessly?
    + What if there was one database, and everyone ran it?
## C Digital Cash
* Intro.
    + In 2008, Satoshi Nakamoto published a method for everyone to run a
        database, thus inventing "crypto."
    + Satoshi invented "an electronic payment system based on cryptographic
        proof instead of trust, allowing any two willing parties to transact
        directly with each other without the need for a trusted third party."
* i. Digression: What are you even reading? Why are you reading it? Why am I
    writing it?
    + When Satoshi invented Bitcoin, one Bitcoin was worth zero dollars: it was
        just an idea he made up. At its peak last November, on Bitcoin was worth
        more than $67,000, and the total value of all the crypto in circulation
        was something like $3 trillion.
    + Many people who got into crypto early got very rich very fast and were
        very annoying about it.
    + I didn't sit down and write 40,000 words to tell you that crypto is dumb
        and worthless and will now vanish without a trace. That would be an odd
        use of time. My goal here is not to convince you that crypto is building
        the furute and that if you don't get on board you'll stay poor. My goal
        is to convince you that crypto is interesting, that it has found some
        new things to say about some old problems, and that even when those
        things are wrong, they're wrong in illuminating ways.
    + ...then some vague theoretical musings like "Well, maybe we could build a
        social media network on web3?" (Shots fired at gm???)
    + *instant redeption by Levine* It's still early. Maybe someone will build a
        really good social media network on web3.
* ii. Digression: Names and people
    + Really nothing of note here fellas
* iii. Digression: The "crypto" in crypto
    + Most of what I talk about in the article won't be about cryptography; it
        will be about, you know, Ponzis. But the base layer of crypto really is
        about cryptography, so it will be helpful to know a bit about it.
    + *I suppose I will note some of the basics for posterity*
    + A useful property in a cryptographic function is that it be "one-way."
        This means it's easy to turn the input string into the output string,
        but hard to do it in revers; it's easy to compute the function in one
        direction but impossible (highly improbable [Matt needs to read his
        Szabo]) in the other.
    + ...another important one-way function is public key encryption. I have two
        numbers, called a "public key" and a "private key." These numbers are
        long and random-looking, but ther're related to each other: Using a
        publicly available algorithm, one number can be used to lock a message,
        and the other can unlock it.
* iv. How Bitcoin works
    + The simple form of Bitcoin goes like this. There's a big public list of
        addresses, each with a unique label that looks like random numbers and
        letters, and some balance of Bitcoin in it.
    + There are thousands (???)  of copies of the ledger; every node on the
        network has its own list of how many Bitcoin are in each address.
    + Crypto systems try to use economic incentives to make people act honestly,
        rather than *trusting* them to act honestly.
* v. Oh, the blockchain
    + Every Bitcoin transaction is brodcast to the network. Some computers on
        the network - ther're called "miners' - compile the transactions as they
        arrive into a group called a "block." At some point, a version of a
        block becomes official: The list of transactions in that block, in the
        order in which they're listed, becomes canonical, part of the official
        Bitcoin record. We say that the block has been "mined." In Bitcoin, a
        new block is mined roughly every 10 minutes.
    + To mine a block, Bitcoin miners do an absurd and costly thing. Each miner
        takes a summary of the list of transactions in the block, along with a
        hash of the previous block. Then the miner sticks another arbitrary
        number - called a "nonce" - on the end of the list. The miner runs the
        whole thing through a SHA-256 hashing algorithm. This generates a
        64-digit hexadecimal number. If that number is small enough, then the
        miner has mined the block. If not, the miner tries again with a
        different nonce.
    + When miners find the right number of zeros, they publish the block and its
        hash to the Bitcoin network. Everyone else reviews the block and decides
        if it's valid. Miner is awarded with Bitcoin.
* vi. Mining
    + Miners need special hardware to do all these hashing calculations over and
        over again, and these days run huge farms of always-on computers.
    + That's why Satoshi, and everyone else, calls this method of confirming
        transactions "proof of work." If you produce the right hash for a block,
        it proves you did a lot of costly computter work. You wouldn't do that
        lightly.
    + Bitcoin block reward was set at 50 Bitcoin per block in the software from
    + the start and halves every four years. Currently it's 6.25 BTC per block.
    + Right now, the Bitcoin network is paying around 1.5% of its value per year
        to miners.



# II What Does It Mean?
## A A Store of Value
* Intro
    + A minimal generalization of Bitcoin is something like: Satoshi invented a
technology for people to send numbers to one another.
* i. Shitcoins
    + Here's another extremely simple generalization of Bitcoin:
        + 1. You can make up an arbitrary token that trades electronically.
        + If you do that, people might pay a nonzero amount of money for it.
        + Worth a shot, no?
    + What makes Bitcoin valuable isn't the elegance of its code, but its social
        acceptance.
* ii. An uncorrelated asset
    + Here's another generalization of Bitcoin:
        + Satoshi made up an arbitrary token that trades electronically for some
            price.
        + The price turns out to be high and volatile.
        + The price of an arbitrary token is ... arbitrary?
    + Modern portfolio theroy demonstrates that adding an uncorrelated asset to
        a portfolio can improve returns and reduce risk.
    + In practice, it turns out that the price of Bitcoin is pretty correlated
        with the stock market, especially tech stocks. Bitcoin *hasn't* been a
        particularly effective inflation hedge: its price rose during years when
        US inflation was low, and it's fallen this year as inflation has
        increased.
* iii. GameStop
    + ... one important possibility is that the first generalization of Bitcoin,
        that an arbitrary tradeable electronic token can become valuable just
        because people want it to, permanently broke everyone's brains about all
        of finance.
## B A Distributed Computer
* Intro
    + Here's another, very different generalization of Bitcoin. In its sharpest
        form, it's mostly attributed to programmer Vitalik Buterin...
        + 1. Look, this thing you made is a big, sprawling *computer*
        + This computer has some fascinating properties: it's *distributed,
            decentralized, secure, final, trustless and permissionless.
        + But it's not a very *good* computer. Mostly it just keeps a list of
            payments.
        + Let's do the same thing, but make it a good computer.
* i. Ethereum
    + The computer that Vitalik invented is generally called Ethereum, or the
        Ethereum Virtual Machine: it's a virtual computer, distributed among
        thousands of redundant nodes. Each node knows the "state" of the
        computer - what's in its memory - and each transaction on the system
        updates that state.
    + ...you can write *programs* to run on the computer to do things
        automatically. One sort of program might be: Send 10 Ether to Address Y
        *if* something happens. Alice and Bob might want to bet on a football
        game, or on a presidential election, or on the price of Ether.
    + ...the Ethereum Name Service, or ENS, which allows people to register
        domain names like "matthewlevine.eth" and use them across various
        Ethereum functions. You end Ether to the ENS program, and it registers
        that name to you - you send in money, and it sends you back a domain.
    + The standard analogy here is a vending machine: A vending machine is a
        computer in the realy world, where you put in a dollar and you get back
        something that you want. You don't negotiate with the vending machine,
        or make small talk about the weather while it rings you up. The machine
        is entirely automated.
    + In the crypto world, these programs are called "smart contracts."
    + Developers build "dapps," or decentralized apps, on Ethereum and other
        blockchains. These are computer programs that mostly run on the web but
        keep some of their essential data on the blockchain.
    + One other limit is that it's a *slow* computer. The way Ethereum executes
        programs is that you broadcast the instructions to thousands of nodes on
        the network, and they each execute the instructions and reach consensus
        on the results of the instructions. That all takes time. Your program
        needs to run thousands of times on thousands of computers.
* ii. Proof of stake
    + ...on September 15, after years of planning, Ethereum switched to a new
        consensus mechanism: Ethereum now uses something called proof of stake
        (or PoS). A bunch of computers - in PoW they;re called "miners," in PoS
        they're called "validators" - work to compile these transactions into an
        official ordered list, called the blockchain.
    + Oversimplifying a bit, the general mechanics are:
        + 1. Anyone can volunteer to be a validator by "staking" some of the
            network's currency, depositing into a special smart contract. The
            staked currency can't be withdrawn for some period. On ethereum, you
            need to stake 32 ether - currently $40,000 or so - to be a
            validator.
        + 2. Validators get transactions as they come in and compile them into
             blocks.
        + 3. At fixed intervals (say, every 12 seconds), one validator is
             randomly chosen to propose a block, and some other set of
             validators is chosen to review the proposed block and vote on it.
        + 4. The randomy chosen validators agree on whether to add the block to
             the chain. If everyone is doing their job honsestly and
             conscientiously, they'll mostly agree, and the block will be added.
        + 5. The validators get paid fees in ether.
        + 6. If a validator acts dishonestly or lazily - if it proposes wrong
             blocks, or if it fails to propose or vote on blocks, or if someone
             turns off the computer running the validator - it can have some or
             all of its stake taken away as a penalty.



# III The Crypto Financial System



# IV Trust, Money, Community





# Docket
Chapter 1, Section C, Subsection i, bullet 4, line 76: (Shots fired at gm???)
[C-Digital-Cash](##C-Digital-Cash)
(This is a hilariously bad reference, I'll figure out how to point directly to
section maybe, but not quote itself...
