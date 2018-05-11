
# Intro
This is my note for the search assignment "try and build a decentralized search Dapp" of [TheSchool.AI](https://www.theschool.ai)

I think of :
- Put a button "support us" on [YaCy P2P search engine](https://yacy.net/) to send ETH to the node => Not a decentralized search
- Take a small fee at every query a user made to support the YaCy node where the query occurs. It could have been a way to use [Oraclize.it](http://www.oraclize.it/). => But who want's to wait for a Blockchain validation at every query they made in a search engine ?
- Make the crawling of a website available to everyone throw a decentralized application. So a company who want to be indexed in YaCy could just pay a worker for it. => Make sens and will make me learn something new !

# Decentralized Computing

How to do it ?
You can't do much compute task directly in a smart contract as you have to pay for every instruction. The compute intensive task as to be done off-chain. System like [Oraclize.it](http://www.oraclize.it/) allow to call a webservice but it's more to get info like a price or weather, not launch a compute task that will take several minutes or more. And with Oraclize.it the computing is centralized.
Fortunatly there are projects that target to allow decentralized intensive computing task. For exemple [Golem](https://golem.network/) and [RNDR](https://rendertoken.com/) for 3D rendering. We will use [iExec](https://iex.ec/) who allow to decentralize our own compute task.

iExec is a whole ecosystem with a market-place for DApps, Oracle mecanisme, Scheduler, workers,... Dedicated to off-chain computing in a fully decentralized way.
(https://iex.ec/app/uploads/2017/08/decentralized-cloud-infographic@3x-1.png)

The V2 is coming at the end of the month and will introduce the Proof Of Completion system.

[iExec SDK](https://github.com/iExecBlockchainComputing/iexec-sdk) is a NodeJS application build above Truffle who allow to easily create and manage your application.

It is now possible to use a Docker image with iExec. So my goal is to embeded YaCy in a Docker container in a way that allow iExec to launch the crawl.

YaCy exist as a Docker container and the crawler could be launch by calling an url :
```
http://localhost:8090/Crawler_p.html?crawlingDomMaxPages=10000&range=wide&intention=&sitemapURL=&crawlingQ=on&crawlingMode=url&crawlingURL=http://WEBSITE_TO_CRAWL.net/&crawlingFile=&mustnotmatch=&crawlingFile%24file=&crawlingstart=Neuen%20Crawl%20starten&mustmatch=.*&createBookmark=on&bookmarkFolder=/crawlStart&xsstopw=on&indexMedia=on&crawlingIfOlderUnit=hour&cachePolicy=iffresh&indexText=on&crawlingIfOlderCheck=on&bookmarkTitle=&crawlingDomFilterDepth=1&crawlingDomFilterCheck=on&crawlingIfOlderNumber=1&crawlingDepth=4
```
For more information read the [wiki page](http://www.yacy-websearch.net/wiki/index.php/Dev:APICrawler).

So everything seems to match together ;-)

But we need to finish the iExec task when the crawler finish the indexation and save it to the YaCy P2P network.


## Installation

### Docker

### iExec

[iExec SDK|https://github.com/iExecBlockchainComputing/iexec-sdk] could be installed through npm but it failed on my computer.
With Docker it also failed, but the comunity helped me and it was the occasion to help them fix a bug [https://github.com/iExecBlockchainComputing/iexec-sdk/pull/37]

Docker installation as a command line tools is done in one line :
```
echo 'alias iexec='"'"'docker run -e DEBUG=$DEBUG --interactive --tty --rm -v $(pwd):/iexec-project -w /iexec-project iexechub/iexec-sdk'"'"'' >> ~/.bashrc && source ~/.bashrc

```

Project init :
iExec SDK is build over truffle and allow to easily build and deploy app. Getting ETH and RLC for testing is easy :
```
iexec init # init a project
cd iexec-init # enter the project
iexec wallet create # create a wallet
iexec wallet getETH # get some ETH
iexec wallet getRLC # get some RLC
iexec wallet show # check you received the tokens
iexec account allow 5 # credit your account with RLC
iexec account show # check your iExec account balance
```

### YaCy


