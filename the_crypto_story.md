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
    + The transition to PoS cut Ethereum's energy usage by something like
        99.95%.
    + Here's how a Bitcoin miner make money:
        + 1. Spend dollars to buy computers and electricity.
        + 2. Use the computers and electricity to generate Bitcoin.
        + 3. Sell the Bitcoin, or hold them and hope they go up.
    + Here's how an Ethereum validator makes money:
        + 1. Buy Ether.
        + 2. Lock it up.
        + 3. Get paid fees in Ether that are, roughly, a percentage of the Ether
             you've locked up. Currently the fees are around 4%.
    + Instead of downloading the software to run a full Ethereum validator node,
        and depositing 32 Ether, you can hand your Ether over to someone else
        and let *them* be a validator. Id doesn't need to be 32 Ether: If you
        have 1 Ether, and 31 other people each have 1 Ether, and you all pool
        your Ether together, then you have enough to stake, validate
        transactions, and earn fees. And then you can each have a cut of the
        fees. The work of validating transactions can be completely seperated
        from the actual staking of Ether.
    + Crypto has found a novel way to *create yield*. It will pay you interest
        not for the reason banks generally do - because they're lending your
        money to some other customer who will make use of it - but because you
        are, in your small way, helping to maintain the security of the
        transaction ledger.
* iii. Gas
    + Ethereum has "gas," which is a fee that people and smart contracts pay for
        computation. Each transaction specifies 1) a maximum gas limit
        (basically a number of computational steps) and 2) a price per unit of
        gas. If the transaction uses up all its gas - it it takes more steps to
        execute than the gas limit - it fails (and still pays the gas fee). This
        deters people from sending superlong transactions that clog the netwoek,
        and it absolutely prevents them from clogging the network forever.
    + In early Ethereum, the gas fees, as well as built-in mining rewards, were
        paid to the miner who mided a block. Since the move to PoS, the built-in
        rewards are lower. And now some of the gas fees are "burned" instead of
        being paid to validators. The basic result is that Ether as a whole is
        paying less for security under PoS than it used to.
* iv. Tokens
    + ERC-20: One thing a smart contract can do in Ethereum is create new
        cryptocurrencies. These cryptocurrencies are generally called "tokens."
    + Why do this?
        + 1. You can make up an arbitrary token that trades electronically.
        + 2. If you do that, people might pay a nonzero amount of money for it.
        + 3. Worth a shot, no?
    + This is so easy, there's 4 lines of code in the Ethereum white paper for
        "implementing a token system" on Ethereum.
    + ERC-20, a token standard which lives on the Ethereum blockchain. One
        essential property of an ERC-20 token is that it's fungible - like
        dolars, or Bitcoin, or Ether.
    + ERC-721, a token standard for non-fungible tokens or NFTs.
            + The ERC-721 introduces a standard for NFT, in other words, this
                type of Token is unique and can have different value than
                another Token from the same Smart Contract, maybe due to its
                age, rarity or even something else like its visual. Wait,
                visual?
            + Yes! All NFTs have a [numerical] variable called tokenId, so for
                any ERC-721 Contract, the pair contract address, [numerical]
                tokenId must be globally unique. That said, a dapp can have a
                "converter" that uses the tokenId as input and outputs an image
                of something cool, like zombies, weapoons, skills or amazing
                kitties!
* v. An ICO
    + Here's another important difference between Ethereum and Bitcoin. Bitcoin
        never raised money; Ethereum did. You can think of Bitcoin as more of
        less the open-source passion product of one anonymous guy who really
        likes cryptography.
    + In July 2014 they sold Ether "at the price of 1000-2000 ether per BTC, a
        mechanism intended to fund the Ethereum organization and pay for
        development," according to Ethereum's white paper. In all, they sold
        about 60 million Ether for about $18.3 million, all before the
        technology itself went live. Today that's worth billions of dollars.
    + There was a 2017 ICO boom which a lot of projects raised a lot of money by
        selling tokens that never turned out to be useful.
* vi. Other chains
    + Layers, trilemmas
        + The basic ideas of Ethereum - a distributed computer, smart contracts,
            dapps, new tokens, etc. - caught on broadly within crypto. Ether is
            now the second-biggest cryptocurrency. (well behind Bitcoin, well
            ahead of everything else).
        + Buit it has a lot of competition: If you;re building smart contracts,
            there are a lot of other blockchains where you can run them,
            including: BNB Chain, Solana, Avalanche, Cardano, Tezos, Polkadot,
            Algorand, Tron, and Terra 2.0 (Terra 1.0 blew itself up, oops.)
        + These platforms, like Bitcoin and Ethereum, are called "Layer 1
            blockchains," meaning they're entirely separate from on another;
            each Layer 1 blockchain maintains its own ledger. They compete with
            one another much like other tech platforms do, arguing that they
            offer better performance, a better environment for developers, a
            different programming style, better tools.
        + The blockchain trilemma: Blockchains want to be scalable,
            decentralized, and secure. But you can only choose 2 out of those 3.
        + Bitcoin and Ethereum chose decentralization and security, which makes
            them fairly slow computers. Other blockchains are faster but more
            centralized.
        + Layer 2 systems are used for scaling a Layer 1. Bitcoin has the
            Lightning Network, a Layer 2 payment system that basically lets
            people on the Bitcoin blockchain set up payments to each other
            without running all of them through the blockchain. This makes the
            payments faster and cheaper, and they periodically settle on the
            blockchain for security.
    + Bridges, wrapping
        + Some people in crypto are faithful to a single blockchain: They are
            Bitcoin maximalists, or Ethereum or Avalanche or Solana loyalists.
        + ...sometimes you will want to own the token of one blockchain on
            another blockchain. This comes up a lot in decentralized finance, or
            DeFi, the system of crypto exchanges and financial products that
            live on blockchains.
        + Bridge, a bridge is generally a smart contract on one blockchaine, a
            smart contract on another blockchain, and some sort of trusted
            computer program that sits between them and passes messages.
        + If you want to swap some Ether for SOL, you find a bridge. You send
            your Ether to the bridge's smart contract in Ethereum, which locks
            it up: As far as the Ethereum blockchain is concerned, your Ether
            belongs to the bridge now. The bridge's off-chain computer program
            sees this and alerts its Solana smart contract, which gives you the
            equivalent of the Ether on the Solana blockchain.
        + Bridges are notorious sites of rist in crypto... An actual big
            Solana/Ethereum bridge is called Wormhole; it was hacked this year
            for about $320 million of wETH.

## C A Slow Database
* Intro: Here's a slightly different generalization of Bitcoin:
    + 1. Look, you've built a distributed *database*.
    + 2. This database has some fascinating properties. It's distributed,
         decentralized, secure, trustless, and permissionless.
    + 3. Your database happens to track the ownership of electronic coins.
    + 4. What if we built a database like that to track the ownership of *other*
         things?
* i. Map and territory
    + People are always talking about moving real estate registries or cargo
        manifests or carbon emissions onto the blockchain. This is appealing
        because, as a database, the blockchain has some nice properties. The
        important public blockchains such as Bitcoin and Ethereum are secure,
        open, and permissionless. Anyone can prove they own a Bitcoin, and that
        ownership can't be reversed arbitrarily.
    + if, somehow, the houses were moved to the blockchain, that would
        permanently allow for permissionless innovation: Everyone could build
        programs and exchanges and derivatirves and interfaces for house buying,
        and the best ones could win.
    + The problem is that houses can't live on the blockchain. They live in the
        real world. They can burn down and stuff. Conncting the electronic
        artifact on the blockchain - the house token? - to its real-world
        referent - the house - is philosophically and practically tricky.
    + How to make this connection is largely an unsolved problem, and quite
        possibly an *unsolvable* one, but also an important one. If you could
        ingest the physical world into that financial system, you'd have
        something cool.
* ii. Enterprise blockchain
    + In 2010, if you were a loan trader at a bank, and you thought, "Ugh, our
        systems for trading loans are so slow and kludgy," and you walked into
        the CEO's office and said, "We should spend tens of millions of dollars
        hiring top-notch programmers to build a new loan-trading system, and we
        should start a consortium with our competitors and clients where we all
        agree to use the same loan-trading system, because that will make life
        easier and eliminate a lot of back-office costs," The CEO would probably
        say things like:
        + Who are you?" and "Get out of my office" and "You're fired."
    + But in 2017, if you were a loan trader at a bank, or a blockchain
        consultant, or frankly a person off the street, and you walked into the
        office of a bank CEO and shouted the word "blockchain!" the CEO would
        hand you a sack of money. Lots and lots and lots of people took
        advantage of this. "Blockchain" was for a while the seciest word in
        finance, and banks were tripping over themselves to announce blockchain
        initiatives.
## D Web3
* Intro: An important fact about Bitcoin is that it;s both a technological
    method of sending money and the money itself. That is, Bitcoin is a computer
    system for sending Bitcoins, and a Bitcoin is the thing that the Bitcoin
    system sends.
    + Some of what goes on in crypto is *about the technology*: People use the
        ideas of blockchains and smart contracts and so forth to build software.
    + Some of what goes on in crypto is *about the money*: People call up their
        brokers to place bets on the prices of crypto tokens going up.
    + Broadly speaking, the name for this is "web3." The idea is that the
        original web was the early development of the internet, when people
        built decentralized open community-controlled protocols for the
        internet. "Web 2.0," or "web2," was when big tech companies more or less
        took over the internet; now your experience of the internet is largely
        mediated through Facebook and Google and Apple and Amazon, and they make
        tons of money from controlling the internet. No open decentralized
        projet is going to compete with them. But web3 will be when people build
        decentralized open community-controlled protocols for the internet again
        *and also make lots of money*. Because the decentralized protocols won't
        be owned by big tech companies, but they won't be free and owned by no
        one, either. They'll be owned by their users.
    + Just kidding; They'll be owned by venture capitalists who but tokens in
        these projects early on and who are the biggest boosters of web3. But
        also by their users.
* i. Tokens and tokenomics
    + Think about what you get when you buy a Vitcoinl One thing you get is a
        unit of "digital cash": You can send the Bitcoin to someone else to buy
        a sandwich or whatever.
    + But another thing you get is a *share* in the Bitcoin project. Not a share
        of actual stock, but still a chance to profit from the succews of
        Bitcoin. If this digital cash things takes off, then lots of people will
        want Bitcoin to use to buy sandwhiches, and there will be a lot of
        demand for Bitcoin. But only 21 million Bitcoin will ever exist. So each
        Bitcoin will be more valuable as more people decide to use Bitcoin as
        their way to transfer digital cash.
    + That logic never quite made sense A convenient currency for digital cash
        transfer has a stable value, and the *rising* value of Bitcoin makes is
        *less* useful as a currency: If your Bitcoin keep going up in value, you
        should not spend them on sandwiches. Bitcoin as an appreciating asset
        will be a bad currency. Still, it worked well *enough*. Bitcoin is used
        enough for digital transfers of value that it became valuable, and early
        adopters got rich.
    + This is a key financial innovation of crypto: Crypto built an efficient
        system to make *the customers of a business also its shareholders.*
    + Lots of crypto projects have this basic structure. Filecoin is a
        decentralized system for storing files, where you can pay to store files
        or get paid for storing files for someone else. You pay, or get paid, in
        Filecoin.
    + Helium is a decentralized system for wireless hotspots, where you can get
        paid for running a hotspot or pay for access. You pay, or get paid, in
        Helium's tokens.
    + This is potentially powerful because crypto is in the network-effects
        business. Bitcoin is a useful payment system if lots of people have
        Bitcoin and accept it for payments. Ethereum is a useful computing
        system if lots of people build apps on Ethereum.
* ii. DAOs
    + ...pronounced "dow," which stands for "decentralized autonomous
        organization." DAOs aren't decentralized autonomous organizations. In
        the early daysm, people sometimes thought that's what they were. "This
        comany runs automatically through smart contracts with no human
        intervenntion," they would say. "It's never been seen before in human
        history." But, no. The thing that runs automatically through smart
        contracts with no human intervention is a *smart contract*. A DAO is a
        way for *people* to get together to *vote* to control a pot of money or
        a protocol on the blockchain.
    + In other words, a DAO is a ... company? Like, just a regular company? It
        has shareholders, who put in money and control it. (Actually, they put
        in money and get back tokens that give them rights to govern the DAO.)
        And the shareholders can vote. DAOs are unlike regular companies in that
        the shareholders (token holders) tend to vote on more stuff: Often
        there's a chat room on an app called Discord, and people can propose
        ideas for the DAO, and there are procedures for holding a vote. Whereas
        US public companies let shareholders vote in only very constrained and
        symbolic ways, DAOs tend to let token holders vote on all sorts of stuff
        and often give them a fair amount of real control of the company. In
        this, DAOs look more like *partnerships* than public corporations.
* iii. Identity, reputation, credentials
    + Many of the grand claims that people make about web3 are about reputation
        and identity. The idea is that you can keep your identity on the
        blockchain in some immutable, decentralized, transparent, provable form,
        and then do good stuff with it.
    + You can have some crypto wallet that contains not just tokens that you
        *bought*, but also token you received for *doing* things. When you
        graduate from college, your college sends you a Backelor's Degree Token,
        or a series of tokes specifying the courses you took and your grades and
        maybe what you learned. Same for DMV, same for job promotions, etc.
        (These tokens will also, in the general case, be *nontransferable*: You
        can't sell your college degree to someone else.)
    + ... if you're looking for a job, you'll show prospective employers your
        degree tokens and conference tokens and Reddit tokens and whatever else
        seems relevant.
## E Uncensorable Ledgers
* i. Censorship resistance
    + Ordinarily, if there's some database on a computer software, and it
        changes some data field, it can just change that field back to what it
        was; those are equivalent, easy things for a computer to do. But the
        blockchain make it *hard* to change things back.
    + Blockchain is one-way; its ledger is permanent. This is nice if you want
        your ledger to be really secure, hard to hack, backed up in multiple
        places, though honestly it's probably an overkill for those purposes.
        But it's *really* nice if you want your ledger to be immune from
        *government meddling*.
* ii. Or not
    + A meme in crypto is the "$5 wrench attack," named for an xkcd web cartoon
        pointing out that the way to seal someone's crypto currency isn't by
        using sophisticated methods to hack his laptop but rather by "hitting
        him with this $5 wrench until he tells us the password."
    + ...crypto creates a *permanent public record* of those transactions... And
        that's where they get you. The normal way to turn your Bitcoin into
        dollars is through a centralized crypto exchange, such as the apps for
        buying and selling crypto that you saw advertised during the Super Bowl.
        They're the main "fiat off-ramp," the place that lets you well your
        Bitcoin for dollars.
    + ...if your *Bitcoin* are on a bad list, they won't turn them into dollars
        for you. If you come by 100,000 Bitcoin in the wrong way... and the
        government has blacklisted it for some reason, the exchange will ask you
        where they came from if you try to transfer it to them.
## F Digital Scarcity
* Intro: We've talked about how Satoshi's essential technological innovation was
    that he found a way to make numbers on computers *scare*. And a weirdly
    important generalization of Bitcoin is that it is a way to create electronic
    scarcity.
* i. Wait, what?
    + Is that good? For digital cash it is, sure. Dollars are electronic ledger
        entries that are scarce because a complicated system of banking
        regulation makes them scare; banks *can* make new dollars just by
        changing a number in a database, but there's a lot of ceremony involved
        in making sure they do that in the right way. Bitcoin solves this with
        the supply cap.
    + One possible future is that the world will be increasingly like that, at
        least for some people. Technological progress will make the basic
        necessities increasingly abundant and also less fun, the physical world
        will become more honmogenous and boring, and everyone will spend more of
        their time online. Their friendships and romances and family life will
        occur on computers; their lives will get meaning from stuff that happens
        on computers.
* ii. Rare monkey JPEGs
    + Remember, an NFT is just a token with a number. If you buy Bitcoin,
        your Bitcoin is identical to anyone else's Bitcoin. If you but an NFT,
        it has a number. There will be some series of NFTs-some ERC-721 token
        series with a name, let's call them Tedious Tamarins- and each NFT in
        that series will have a number, and Tedious Tamarin No. 63 will be
        distinguished from Tedious Tamarin No. 64 by having a different number.
    + If you buy and NFT, what you own is a notation on the blockchain that says
        you own a pointer to some web server. On that web server there's
        *probably* a picture of a monkey, but that's none of the blockchain's
        business. Meanwhile the intellectual-property rights to that picture of
        a monkey are *certainly* none of the blockchain's business. It's not
        uncommon for the person or company selling the SFT series to 1) own the
        IP rights to the pictures of the monkeys and 2) promise to transfer
        those rights, or some of them, to individual holders of the NFTs. But if
        that happens, it happens off the blockchain; those promises are or
        aren't enforceable through the normal legal system. And it's not all
        that uncommon for the person selling the NFT series *not* to own the IP
        rights.
* iii. The metaverse
    + I plan to go to my grave not knowing what "the metaverse" is, so I'm
        certainly not going to explain it to you. But one thing it is is that
        you can buy some real estate on the internet. Like, there will be a
        picture of a house on the internet, and so on...
    + How much should your house in the metaverse cost? Two plausible answers
        might be "It should cost as much a sa house, it's a house," or "It
        should be basically free, it's just a file on a computer, there's
        essentially infinite space in the metaverse, and nobody has to actually
        nail together the house."
    + ...it's hard not to think of the movie *The Matrix*. You know the premise:
        Everyone is a sack of meat in a bath of nutrients with their brains
        plugged into a remarkably realistic simulation of late-'90s America.
    + So they simulated late capitalism instead. Even in a world where all the
        goods are digital and available in limitless abundance, you still have
        to have a (simulated) desk job to pay for them. Digital scarcity.


# III The Crypto Financial System
Let's step back a bit and abstract from what we've discussed so far. Crypto is:
* 1. A set of tokens, which are worth fluctuating amounts of money. We can say
     that these tokens are financial assests, like stocks and bonds.
* 2. A novel set of ways to create new tokens and distribute them and try to
     make them worth money.
* 3. A novel way of *holding* financial assets: Instead of the databases that
     people use to hold stocks and bonds, you can own your crypto on the
     blockchain.
* 4. A novel way to write contracts and computer programs (computer programs
     that are contracts, and contracts that are computer programs).

## A Your Keys, Your Coins, Your Hard Drive in a Garbage Dump
* i. Holding crypto
    + ...the traditional financial syetem is deeply *intermediated*, and the
        crypto system is not. If you have money, your bank tracks your money for
        you; if you have stock, your broker tracks your stock for you; etc.
    + One dumb, simple thing that this means: If you have money in the bank and
        you forget your ATM PIN or your online banking password, you'll have a
        hard time taking money out. But the bank owes you the money; they can't
        just be like, "Aha, got you, the money is ours now." Crypto doesn't
        *necessarily* work like that. Owning Bitcoin means 1) having a public
        Bitcoin address with some Bitcoin in it and 2) possessing the private
        key to that address. If you have the public address/private key pair,
        then you own the Bitcoin. If you don't have that pair, then you can't.
        If you lose your private key or lose track of your public address,
        there's no one to recover your password for you or give you back your
        Bitcoin. They're just gone.
    + Mainly people use "software wallets," which generate and keep track of
        their addresses and private keys and allow them to sign transactions and
        send and recieve crypto online. Most modern wallets require you to keep
        track not of private keys, but rather a "seed phrase" of, typically, 12
        random-looking words. You use this seed phrase to generate a
        public/private key pairing, and you can use it to access wallet.

* ii. *Not* holding crypto
    + ...in traditional finance there's a big business offering those
        instruments. CME Group Inc. offers Bitcoin futures, which are basically
        the bet that I outlined above: You pay me $5 for every dollar that
        Bitcoin goes up, and I pay you $5 for every dollar it goes down. It's a
        trusted centralized, traditional0finance way to bet on the price
        movements of Bitcoin.
    + So wrapping a Bitcoin in a *stock* would increase its appeal. The easiest
        way to do this would be a cash Bitcoin exchange-traded fund, a pot of
        money that trades like stock on a stock exchange and invests the money
        in Bitcoin. People keep trying to do this, but the US Securities and
        Exchange Commission remains skeptical and hasn't approved cash Bitcoin
        ETFs, though they exist in some other countries.
    + The US has, however, approved Bitcoin *futures* ETFs, which invest in
        Bitcoin through futures contracts. Two layers of abstraction: a Bitcoin,
        wrapped in a futures contract, wrapped in a stock, and delivered to your
        brokerage account.



# IV Trust, Money, Community





# Docket

## Chapter 1, Section C, Subsection i, bullet 4, line 76: (Shots fired at gm???)
[C-Digital-Cash](##C-Digital-Cash)
(This is a hilariously bad reference, I'll figure out how to point directly to
section maybe, but not quote itself...

## Chapter 2, Section C, Subsection i, bullet 2-4, isn't this crypto oracles?

