# Requirements Document 

Date: 22 march 2022

Version: 0.0

 
| Version number | Change |
| ----------------- |:-----------|
| | | 


# Contents

- [Informal description](#informal-description)
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
	+ [Context Diagram](#context-diagram)
	+ [Interfaces](#interfaces) 
	
- [Stories and personas](#stories-and-personas)
- [Functional and non functional requirements](#functional-and-non-functional-requirements)
	+ [Functional Requirements](#functional-requirements)
	+ [Non functional requirements](#non-functional-requirements)
- [Use case diagram and use cases](#use-case-diagram-and-use-cases)
	+ [Use case diagram](#use-case-diagram)
	+ [Use cases](#use-cases)
    	+ [Relevant scenarios](#relevant-scenarios)
- [Glossary](#glossary)
- [System design](#system-design)
- [Deployment diagram](#deployment-diagram)

# Informal description
Medium companies and retailers need a simple application to= manage the relationship with suppliers and the inventory of physical items stocked in a physical warehouse. 
The warehouse is supervised by a manager, who supervises the availability of items. When a certain item is in short supply, the manager issues an order to a supplier. In general the same item can be purchased by many suppliers. The warehouse keeps a list of possible suppliers per item. 

After some time the items ordered to a supplier are received. The items must be quality checked and stored in specific positions in the warehouse. The quality check is performed by specific roles (quality office), who apply specific tests for item (different items are tested differently). Possibly the tests are not made at all, or made randomly on some of the items received. If an item does not pass a quality test it may be rejected and sent back to the supplier. 

Storage of items in the warehouse must take into account the availability of physical space in the warehouse. Further the position of items must be traced to guide later recollection of them.

The warehouse is part of a company. Other organizational units (OU) of the company may ask for items in the warehouse. This is implemented via internal orders, received by the warehouse. Upon reception of an internal order the warehouse must collect the requested item(s), prepare them and deliver them to a pick up area. When the item is collected by the other OU the internal order is completed. 

EZWH (EaSy WareHouse) is a software application to support the management of a warehouse.



# Stakeholders

| Stakeholder Name | Description |
|:-----|:------------|
| Companies | Establishment made of several departments whose main objective is to sell items; "Retailers" is a synonym |
| Suppliers | The emobodiement of an entity that provides a certain product to a company; "Manufacturers" could be an  example of a supplier |
| Warehouse Manager | Person in charge of making order requests to the suppliers and supervising the work of the warehouse's workers|
| Supplier Manager | Person in charge of handling the order requests received|
| Administrator | Manages the addition of Companies to the software |
| Warehouse Workers | Employees that execute the directions of the manager(item unpacking,item positioning,quantity check)  |
| Quality Office | Check the quality of the product upon arrival to the warehouse |
| Organizational unit | Different branch or department of a Company |
| Organizational unit Manager | The head of a organizational unit that can start an internal order procedure |
| Competitors | Any company that produces Warehouse Management applications|
| StartUp Owner | The founder/creator of the startup company "EZWH" |
| Startup Financer | Group or individuals funding the startup "EZWH" |
| Cloud Service | Service to store data and perform calculations on cloud |
| Payment service | Service to allow payment of orders |
| Transportation Service | Service that takes care of the external and internal orders |

# Context Diagram and interfaces

## Context Diagram
![ContextDiagram](./out/context_diagram/ContextDiagram.svg)

## Interfaces

| Actor | Logical Interface | Physical Interface |
|:------|:------------------|:-------------------|
| Warehouse Manager | GUI | M&K |
| Supplier Manager | GUI | M&K |
| Administrator | GUI | M&K |
| Quality Office | GUI | M&K |
| Organizational Unit Manager | GUI | M&K |
| Warehouse Workers | GUI | Tablet |
| Payment Service | Internet Connection | API |
| Cloud Service | Internet Connection | API |
| Transportation Service | Internet Connection | M&K |

# Stories and personas
Mario, 30, is the manager of a big company's warehouse, handling hundresds of items per day. He has always managed the position of the goods by himself, leading to some management problems during the years. Also the re-fill process is handled by him, directly calling to different suppliers asking for availabilities of items. He would really like to use an application which can automatize this entire handling process. 

Ercole, 45, has been recently hired as manager in a company that acts as a supplier for other companies or retailers, by selling mechanical components to them. In his previous job, he was used to a software which automatically checks if an order is satisfiable or not and contacts the transportation company. Now he has to manually check the availabilities for every item, and directly phone the transaportation company. He would like to emulate the same experience got in his previous mansion.

Ezio, 35, is the chief of one of the Organizational Unit that composes a worldwide company. Anytime he needs an item from the central warehouse, he send an internal order request to the headquarter offices, which will be only later sent to the warehouse, resulting in a huge delay of time due to burocracy. He would really appreciate a software that manages a direct communication with the warehouse manager. 

# Functional and non functional requirements

## Functional Requirements

| FR1   | Manage Orders |
| FR1.1 |Manage External orders  |
| FR1.1.1 | Display the Supplier's list  |
| FR1.1.2| Show all the items in the catalogue of a specific supplier |
| FR1.1.3 | Place new external order |
| FR1.1.4 | Cancel the external order |
| FR1.1.5 | Add an item to the external order |
| FR1.1.6 | Remove an item from the external order |
| FR1.1.7 | Display an external order |
| FR1.2 | Manage Internal order |
| FR1.2.1 | Display the list of items in the Warehouse |
| FR1.2.2 | Place a new internal order |
| FR1.2.3 | Cancel an interal order |
| FR1.2.4 | Add an item to the interal order |
| FR1.2.5 | Remove an item to the interal order |
| FR1.2.6 | Display an interal order |
| FR1.2.7 | Manage the status of the order |
| FR1.2.8 | Manage transportation method |

| FR2   | Manage Warehouse                                  |
| FR2.1 | Track the position of every item                  |
| FR2.2 | Update quantity of an item                        |
| FR2.3 | Track remaining free space for every item         |
| FR2.4 | Add an item                                       |
| FR2.5 | Remove an item                                    |

| FR3   | Manage Account      |
| FR3.1 | Add account         |
| FR3.2 | Remove account      |
| FR3.3 | Update account      |
| FR3.4 | Modify privileges   |

| FR4   | Manage Quality                                  |
| FR4.1 | Manage a test                    |
| FR4.1.1 | Add a test with its description                   |
| FR4.1.2 | Update the test's description                   |
| FR4.1.3 | Delete a test                    |
| FR4.2 | Manage order quality check                     |
| FR4.2.1 | Display orders in the staging area  |
| FR4.2.2 | Display the list of possible tests for every item inside the order  |
| FR4.2.3 | Add a test to the item                     |
| FR4.2.4 | Remove a test from the item                     |
| FR4.2.5 | Report the result of a test                     |
| FR4.2.6 | Ignore an item                     |
| FR4.2.7 | Ignore an order                     |



| FR5   | Manage Supplier Catalogue   |
| FR5.1 | Add an item                 |
| FR5.2 | Remove an item              |
| FR5.3 | Show items in the catalogue |
| FR5.4 | Update an item's attribute      |

## Non Functional Requirements

| ID    | Type        | Description  | Refers to |
|:------|:-----------:|:-------------| ----------|
| NFR1 | Privacy      | Users' passwords must not be saved in the system | FR3 |
| NFR2 | Privacy      | The data of a customer should not be disclosed outside the application | All FR |
| NFR3 | Usability    | The user must learn how to use the application in less than 20 minutes | All FR |
| NFR3 | Portability |The application should be accessed by Chrome (version 81 and more recent), and Safari (version 13 and more recent) (this covers around 80% of installed browsers); and from the operating systems where these browsers are available (Android, IoS, Windows, MacOS, Unix). As for devices, the application should be usable on smartphones (portrait) and PCs (landscape). | All FR |
| NFR4 | Performance  | The Suppliers' list must be retrieved in less than 1 seconds | FR1.2 |
| NFR2 | Performance  | All functions should complete in leass than 0.5 second | All FR |
| NFR5 | Localisation | Decimal numbers use . (dot) as decimal separator | All FR |
| NFR6 | Domain       | Currency is Euro |


# Use case diagram and use cases


## Use case diagram
\<define here UML Use case diagram UCD summarizing all use cases, and their relationships>


\<next describe here each use case in the UCD>
### Use case 1, UC1
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other normal executions> |
|  Exceptions     | \<exceptions, errors > |

##### Scenario 1.1 

\<describe here scenarios instances of UC1>

\<a scenario is a sequence of steps that corresponds to a particular execution of one use case>

\<a scenario is a more formal description of a story>

\<only relevant scenarios should be described>

| Scenario 1.1 | |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the scenario can start> |
|  Post condition     | \<Boolean expression, must evaluate to true after scenario is finished> |
| Step#        | Description  |
|  1     |  |  
|  2     |  |
|  ...     |  |

##### Scenario 1.2

##### Scenario 1.x

### Use case 2, UC2
..

### Use case x, UCx
..



# Glossary

![ClassDiagram](./out/class_diagram/ClassDiagram.svg)

# System Design
\<describe here system design>

\<must be consistent with Context diagram>

# Deployment Diagram 

\<describe here deployment diagram >




