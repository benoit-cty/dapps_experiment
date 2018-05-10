# Intro

For the search assignment "try and build a decentralized search Dapp" I think of :
- Put a button "support us" on [https://yacy.net/] to send ETH to the node => Not realy a decentralized search
- Take a small fee at every query a user made to support the YaCy node where the query occurs. It could have been a way to use [http://www.oraclize.it/]. => But who want's to wait for a Blockchain validation at every query they made in a search engine ?
- Make the crawling of a website available to everyone throw a decentralized application. So a company who want to be indexed in YaCy could just pay a worker for it. => Make sens and will make me learn something new !

# Decentralized Computing

So the way to do it :
XXX

## Installation

[iExec SDK|https://github.com/iExecBlockchainComputing/iexec-sdk] could be installed through npm but it failed on my computer.
With Docker it also failed, but the comunity helped me and it was the occasion to help them fix a bug [https://github.com/iExecBlockchainComputing/iexec-sdk/pull/37]

Docker installation as a command line tools is done in one line :
```
echo 'alias iexec='"'"'docker run -e DEBUG=$DEBUG --interactive --tty --rm -v $(pwd):/iexec-project -w /iexec-project iexechub/iexec-sdk'"'"'' >> ~/.bashrc && source ~/.bashrc

```
