# Simple solidity
Easy contract text to solidity code converter. This project will allow to create and read smart contracts to ordinary people in any languages without knowledge of programming languages.


Each phrase means a certain section of code with a detailed explanation. User can use own library or other's people libraries for creating smart contracts fast and easy.

Any user can share, modify and use other's users contracts without knowledge of programming languages.

Example of a document (contract source) that user can write 

```
Contract name: Simple Contract. 
```

this text will be translated to code with Simple solidity:

```
pragma solidity ^0.4.15;

// "Simple Contract" text converted to Solidy-accepted contract name
contract SimpleContract {

}
```

Next text example
```
Contract name: Simple Contract. 
Contract is mortal. Contract can accept Ether.
```

will be translated to code:
```
pragma solidity ^0.4.15;

// "Contract is mortal." text adds this contract
contract mortal {
    address owner;
    function mortal() {owner = msg.sender;}
    function kill() {if (msg.sender == owner) selfdestruct(owner);}
}

// "Contract is mortal." adds this modifier
contract SimpleContract is mortal {
    // "Contract can accept Ether"
    function() payable {}
}
```

Next example
```
Contract name: Simple Contract. 
Contract is mortal. Contract can accept Ether.

User has a shopping list
```

```
pragma solidity ^0.4.15;

contract mortal {
    address owner;
    function mortal() {owner = msg.sender;}
    function kill() {if (msg.sender == owner) selfdestruct(owner);}
}

contract SimpleContract is mortal {
    function() payable {}
    
    // "User has a shopping list". Create shopping structure
    struct Shopping {

    }
    
    // "User has a shopping list". Create user structure, add shopping list to this structure
     struct  User {
        Shopping[] ShoppingList;
    }
    
    // "User has a shopping list". Create users list
    mapping (address => User) users;
}
```

Next example
```
Contract name: Simple Contract. 
Contract is mortal. Contract can accept Ether.

User has a shopping list. Shopping list has fields: name, count.
User can add items in shopping list.
```

Converts to
```
pragma solidity ^0.4.15;

contract mortal {
    address owner;
    function mortal() {owner = msg.sender;}
    function kill() {if (msg.sender == owner) selfdestruct(owner);}
}

contract SimpleContract is mortal {
    function() payable {}
    
    struct Shopping {
        // added field Name
        string Name;
        // added field Count
        int Count;
    }
    
    struct  User {
        Shopping[] ShoppingList;
    }
    
    mapping (address => User) users;
    
    // "User can add items in shopping list"
    function addShoppingList(string Name, int Count){
       users[msg.sender].ShoppingList.push(Shopping(Name, Count));
    }
}
```

Creation steps:

Month 1 - Creation of a template system for recognizing English text and searching for suitable solidity code in system. 

Month 2 - Adding possibility to extend system with any human-readable language, possibility to create and share code and contracts

Month 3-4 - Creating a platform for easy creation and sharing of code and text of the contracts.