# Emerald-Quest-Submission
Quest Submissions
New guy sign up test.

>Chapter 1 Day 1
>>Explain what the Blockchain is in your own words. 
>>> A blockchain is a public general ledger that is secured through decentralized computing using chain specific hash.

>>Explain what a Smart Contract is. 
>>>A smart contract is an entry on a blockchain with specific characterstics or commands.

>>Explain the difference between a script and a transaction.
>>>I believe a script can be used to view infomration on a block chain and a transaction adds, changes or edits information on the blockchain.  

>Chapter 1 Day 2
>>What are the 5 Cadence Programming Language Pillars?
>>> The 5 Pillars are 1) Security 2) Clarity, 3) Approachability, 4) Developer Experience, 5) Resource Oriented Programming

>>In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?
>>> From the history it seem to address some issued discovered on Etheruem.  Improving security seems core, the others seem to address the usability characteristics required for wide spread developer adoption.  

>Chapter 2 Day 1
>Completed the exercise in the playground, but not sure how to share the file/export. How is it best to share? 
>Here is what it looked like.  

pub contract JacobTucker {
 
  pub let is: String

  init() {
      self.is = "the best"
  }

  pub fun hello(): String {
      return self.is
  }
}

// Script1.cdc

import JacobTucker from 0x03

pub fun main() {
    log(JacobTucker.hello())
}
