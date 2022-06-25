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

>Chapter 2 Day 2
>>    Explain why we wouldn't call changeGreeting in a script.
>>>   I believe changeGreeting is acting as a function that changes NewGreeting. Im not sure a value would get returned.     

>>   What does the AuthAccount mean in the prepare phase of the transaction?
>>>  AuthAccount is the users ID credentials to the Account on the Flow blockchain.  

>>   What is the difference between the prepare phase and the execute phase in the transaction?
>>>  The prepare phase is to call information from the account.  The Execute phase can perform functions and change 

>>  This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

    Add two new things inside your contract:
        A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
        A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

    Add a script that reads myNumber from the contract

    Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.
```cadence
pub contract HelloWorld {

    pub var greeting: String

    pub fun changeGreeting(newGreeting: String) {
        self.greeting = newGreeting
    }
    pub var myNumber: Int
    
    pub fun changemyNumber(newmyNumber: Int) {
        self.myNumber = newmyNumber
    }

    init() {
        self.greeting = "Hello, World!"
        self.myNumber = 0
    }
}
```

```cadence
import HelloWorld from 0x01

pub fun main(): Int {
    return HelloWorld.myNumber
}
```
```cadence
import HelloWorld from 0x01

transaction(mynewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.changemyNumber(newmyNumber: mynewNumber)
  }
}
```

>Chapter 2 Day 3
>>1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.
```cadence
pub contract ADS {

    pub var allNames: [String] 
    
    pub fun addNames(name: String)    {
        self.allNames.append(name)
    }

    init() {
        self.allNames = ["Jeff", "Leah", "Willow"]
    }
}
```
```cadence
import ADS from 0x01

transaction (name: String) {

  prepare(acct: AuthAccount) {}

  execute {
    ADS.addNames(name: name)
  }
}
```
```cadence
import ADS from 0x01

  pub fun main(): [String] {
  return ADS.allNames

  }
```

>>2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!

```cadence
pub contract ADS {

    pub var allSocial: [String]

    pub var luckySocial: {UInt64: String}

    pub fun addSocial(social: String) {
        self.allSocial.append(social)
        }

    
    init() {
        self.allSocial = ["Facebook", "Instagram", "Twitter", "YouTube", "Reddit", "LinkedIn"]    

        self.luckySocial = {1: "Twitter", 2: "LinkedIn", 3: "YouTube", 4: "Reddit", 5: "Facebook", 6: "Instagram"}


    }

   
}
```

```cadence
import ADS from 0x01

pub fun main(): {UInt64 : String} {
  return ADS.luckySocial
  }
```
  >>3.  Explain what the force unwrap operator !
    >>> You use a ! force unwrap operator when you are calling a function on an item that is in a dictionary defined within a struct.  It is required to do this to to avoide calling a function on a nil value...which would cause the program to fail.
  
  >>4.  
    What the error message means
    Why we're getting this error
    How to fix it
    >>>This error means 'thing' must be defined within a struct.
    >>>We're getting this error because 'thing' needs to be unwrapped first
    >>>we'd fix it by putting in "!", {address : String}!

>Chapter 2 Day 4
>>1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).
>>2. Create a dictionary or array that contains the Struct you defined.
>>3. Create a function to add to that array/dictionary.

>>>```cadence
    pub contract Authentication {

    pub var runner: {Address: Runner}
    
    pub struct Runner {
        pub let firstName: String
        pub let lastName: String
        pub let time: AnyStruct
        pub let account: Address

        
        init(_firstName: String, _lastName: String, _time: AnyStruct, _account: Address) {
            self.firstName = _firstName
            self.lastName = _lastName
            self.time = _time
            self.account = _account
        }
    }

    pub fun addRunner(firstName: String, lastName: String, time: AnyStruct, account: Address) {
        let newRunner = Runner(_firstName: firstName, _lastName: lastName, _time: time, _account: account)
        self.runner[account] = newRunner
    }

    init() {
        self.runner = {}
    }

}
```

>> 4.  Add a transaction to call that function in step 3.

>>>```cadence
import Authentication from 0x01

transaction(firstName: String, lastName: String, time: AnyStruct, account: Address) {

    prepare(signer: AuthAccount) {}

    execute {
        Authentication.addRunner(firstName: firstName, lastName: lastName, time: time, account: account)
        log("We're done.")
    }
}
```


>> 5.  Add a script to read the Struct you defined.
>>>```cadence
import Authentication from 0x01

pub fun main(account: Address): Authentication.Runner {
    return Authentication.runner[account]!
}
```




