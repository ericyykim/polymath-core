## 1.3.0 -> 1.4.0

1. Deploy new SecurityTokenRegistry
Params = Polymath Registry Address, STVersionProxy001, 250 POLY

---> Migrate data from original STR to new STR

2. Deploy Oracles
- a) Deploy POLY Oracle and update STR
	Kovan address = 0x9c2c839c71ae659b82f96071f518c6e96c3af071
	SecurityTokenRegistry.changeOracle ("POLY", "USD", 0x9c2c839c71ae659b82f96071f518c6e96c3af071 )

- b) Deploy ETH Oracle and update STR
	Kovan address = 0x2a64846750e0059bc4d87648a00faebdf82982a9
	SecurityTokenRegistry.changeOracle ("ETH", "USD", 0x2a64846750e0059bc4d87648a00faebdf82982a9 )

3. Deploy USDTieredSTO contract and verify it on the ModuleRegistry:
- a) Kovan params:
  		0xb06d72a24df50d4e2cac133b320c5e7de3ef94cb, 100000000000000000000000,0,0
  	Kovan Address: 0xd4eb00b4e222ae13b657edb3e29e1d2df090c1d3

- b) ModuleRegistry -> RegisterModule
  	Kovan params: 0xd4eb00b4e222ae13b657edb3e29e1d2df090c1d3

- c) ModuleRegistry -> VerifyModule
  	Kovan params: 0xd4eb00b4e222ae13b657edb3e29e1d2df090c1d3, true



4. Update PolymathRegistry with new STR
- a) PolymathRegistry.changeAddress ("SecurityTokenRegistry",0x2f279fde5b3a9d4570e21ccc6d67a6962b134902)

- b) Update registry addresses on all registries

  - i. TickerRegistry.updateFromRegistry
	- ii. ModuleRegistry.updateFromRegistry
	- iii. SecurityTokenRegistry.updateFromRegistry -----> Make sure it's the new registry
	- iv. Any SecurityToken instances out there if needed
