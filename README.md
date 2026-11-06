name: Run postman API tests

on: 
	
  push:
    branches:
	- '**'

jobs:
   api-test:
     runs-on: ubuntu-latest

     steps:
         -name: Checkout Repository
          uses: actions/Checkout@v3
        
	 -name: Setup Node
          uses: actions/setup-node@v3
	    with
             node-version:26

         -name: install Newman
          run: npm install -g newman
		
	 -name: Run Collection
	  run: newman run Collection.json
