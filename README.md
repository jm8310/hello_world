# MobiCheck Demo
##Deploying the demo##To deploy to Bluemix simply use the button below then follow the instructions. This will generate the NodeJS server and the Blockchain service for you.
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/IBM-Blockchain/car-lease-demo.git)
To deploy the demo locally follow the instructions [here](Documentation/Installation%20Guide.md#deploying-locally)
##Application overview##
This application is designed to demonstrate how product (mobile) can be modeled on the Blockchain using a mobile selling scenario. In the scenario mobiles are modeled using Blockchain technology with the following attributes:

| Attribute     | Type
|-------------  | ---------------------------------------------------------------------------------|
|BarCode ID     | Unique BarCode Id for the Mobile in the form of int                              |
|ESN            | int                                                                              |
|Make           | String                                                                           |
|Model          | String                                                                           |
|Colour         | String                                                                           |
|Owner          | Identity of participant                                                          |
|Scrapped       | Boolean                                                                          |
|Status         | Int between 0 and 4                                                              |

The application is designed to allow participants to interact with the vehicle assets creating, updating and transferring them as their permissions allow. The participants included in the application are as follows:

| Participant    | Permissions                                                         
---------------------------------------
| Regulator      | Create, Read (All Products), Transfer                               
| Manufacturer   | Read (Own Products), Update (VIN, Make, Model, Colour, Reg), Transfer
| Dealership     | Read (Own Products), Update (Colour, Reg), Transfer                              
| Customer       | Read (Own Products), Update (Colour, Reg), Transfer                  
| Scrap Merchant | Read (Own Products), Scrap                         

The demonstration allows a view of the ledger that stores all the interactions that the above participants have has with their assets. The ledger view shows the regulator every transaction that has occurred showing who tried to to what at what time and to which product. The ledger view also allows the user to see transactions that they were involved with as well as showing the interactions with the assets they own before they owned them e.g. they can see when it was created.

##Application scenario##The scenario goes through the lifecycle of a Mobile Product which has the following stages:
1. Product(Mobile) is created as a template by the regulator. 2. Product template is transferred to the manufacturer. 3.  Manufacturer updates the Product template to define it as a Product giving it a make, model, reg etc. 4. Manufacturer transfers the Product to dealership to be sold. 5. Dealer  transfers the Product to a Customer. 6. Customer transfers the product to a manufecturer so that it can be scrapped as part of buyback. 7. Scrap merchant scraps the product.##Component model##The demo is built using a 3 tier architecture. The user interacts with the demo using a [web front end](Documentation/Client%20Side.md) that is provided by the NodeJS server in the middle tier. This web front end uses JavaScript to make HTTP requests to the NodeJS server which has an API ([defined here](Documentation/API Methods.md)) which in turn makes calls via HTTP to the HyperLedger fabric to get details about the blockchain and also interact with the [chaincode](Chaincode/src/vehicle_code/vehicles.go). Information on the chaincode interface can be found [here](Documentation/Chaincode Interface.md)![Technical Component Model](/Images/Technical_Component_Model.png)####Stages:#### 1. Vehicle is created as a template by the regulator. 2. Vehicle template is transferred to the manufacturer. 3.  Manufacturer updates the vehicle template to define it as a vehicle giving it a make, model, reg etc. 4. Manufacturer transfers the vehicle to dealership to be sold. 5. Dealership transfers the vehicle to a lease company. 6. Lease company transfers the vehicle to a leasee. The vehicle is not leased instead the application is showing what would happen if the lease were to have come to an end and the leasee activated the purchase option. 7. Leasee transfers the vehicle to a scrap merchant so that it can be scrapped. 8. Scrap merchant scraps the vehicle.##Component model##The demo is built using a 3 tier architecture. The user interacts with the demo using a [web front end](Documentation/Client%20Side.md) that is provided by the NodeJS server in the middle tier. This web front end uses JavaScript to make HTTP requests to the NodeJS server which has an API ([defined here](Documentation/API Methods.md)) which in turn makes calls via HTTP to the HyperLedger fabric to get details about the blockchain and also interact with the [chaincode](Chaincode/src/vehicle_code/vehicles.go). Information on the chaincode interface can be found [here](Documentation/Chaincode Interface.md)![Technical Component Model](/Images/Technical_Component_Model.png)
