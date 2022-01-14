# Wlovecoin (WLOVE) audit report.


# Summary

This is the report from a security audit performed on [Token Wlovecoin](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol) by [Blockchain Technology SAS](https://github.com/blockchaintechnologysas/audit/blob/main/doc/granacoin-graco-audit_report.md). This contracts are a version of [OpenZeppelin Contracts v4.4.0](https://github.com/OpenZeppelin/openzeppelin-contracts).

The audit mainly focused on the security of the funds and the fault tolerance of the token. The main intention of this token is the commercialization of the company's products UNIVERSO DE LOS COSMETICOS S.A.S. of Cali-Colombia

# In scope

1. [gracocoin.sol](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol)

# Findings Processes

In total, **12** were reported including:

- 2 event.

- 10 funcion.

It is reported that it has no errors (No critical security issues were found).

## Event

### 1. Event Transfer(address indexed from, address indexed to, uint tokens)

#### Severity: LOW

#### Description

This event is emitted when the number of tokens (value) is sent from the from address to the to address.

### 2. Event Approval(address indexed tokenOwner, address indexed spender, uint tokens)

#### Severity: LOW

#### Description

This event is emitted when the amount of tokens (value) is approved by the owner to be used by spender (End User).

## Funcion

### 1. ERC20Burnable.

#### Severity: LOW

#### Description

You can perform the Burning Token function, make Repurchases to be able to Burn Tokens.
** _burn (account, amount); **

#### Recommendation

According to the code, only the administrator with the authorized Role can perform this action.

### 2. ERC20Snapshot.

#### Severity: LOW

#### Description

The definitions of the functions of `gracocoin.sol`.

With the Snapshop function, it allows us to obtain token support at any time to have it for consultations for seasons defined by a consecutive one, or to take balances from all holders.

** _snapshot (); **

Writing:
• <Snapshot> Write (creates a copy are consecutive)
Reading:
• <TotalSupplyAt> <Snapshotld>
• <BalanceOf> (Address) and (Snapshotld)

#### Recommendation

prolonged use of backups generates the cost of higher memory and this generates higher Cost in Gas

### 3. AccessControl.

#### Severity: lOW

#### Description

El control de acceso, es decir, "a quién se le permite hacer esto", es increíblemente importante en el mundo de los contratos inteligentes. El control de acceso de su contrato puede regir quién puede acuñar tokens, congelar transferencias y muchas otras cosas. Por lo tanto, es fundamental comprender cómo lo implementa, no sea que alguien más robe todo su sistema.
Escritura:
•	< Grant Role >
•	< Renounce Role>
•	< Revoke Role >

Lectura:
•	< Get Role Admin >
•	< Hash Role >
  
#### Recommendation  
  
Use with caution only the administered  

### 4. Pausable

#### Severity: low

#### Description

the ability to perform all system operations with the system administrator, this allows to avoid losses.
Writing:
• <Paused> Enable or Disable

Reading:
• <Paused> Boolean (true and false)

#### Recommendation

Specify `public` visibility for the contract's inner variables.

### 5. TotalSupply 

#### Severity: low

#### Description

Shows the total token created..

### 6. BalanceOf(address)

#### Severity: low

#### Description

Returns the number of tokens that an address (account) owns. This function is a getter and does not change the status of the contract.

### 7. allowance(address tokenOwner, address spender)

#### Severity: not a security issue

#### Description

The ERC-20 standard allows one address to assign an assignment to another address in order to retrieve tokens from it. This getter returns the remaining number of tokens that spenderse will allow you to spend on behalf of owner. This function is a getter and does not modify the state of the contract and should return 0 by default.

### 8. transfer(address to, uint tokens)

#### Severity: not a security issue

#### Description

Moves the number tokens from the address of the caller to the function (msg.sender) to the address of the recipient. This function issues the Transfer. Returns true if the transfer was possible.
 
### 9. approve(address spender, uint tokens)

#### Severity: not a security issue

#### Description

Set the amount of token that allows the transfer of the balance call function (msg.sender). This function emits the approval event. The function returns whether the mapping was successful.
  
### 10. transferFrom(address from, address to, uint tokens)

#### Severity: not a security issue

#### Description

Move the amount of tokens to the recipient address using the allocation mechanism. the amount is deducted after the caller's allowance. This function issues the Transfer event.  
  
# Specification ContractABI

[Contract](https://bscscan.com/address/0x84aea9789137bfef54915d21dad85ecbdcdf840b#code) GRACO
 
[{"inputs":[],"stateMutability":"nonpayable","type":"constructor"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"owner","type":"address"},{"indexed":true,"internalType":"address","name":"spender","type":"address"},{"indexed":false,"internalType":"uint256","name":"value","type":"uint256"}],"name":"Approval","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"account","type":"address"}],"name":"Paused","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"bytes32","name":"role","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"previousAdminRole","type":"bytes32"},{"indexed":true,"internalType":"bytes32","name":"newAdminRole","type":"bytes32"}],"name":"RoleAdminChanged","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"bytes32","name":"role","type":"bytes32"},{"indexed":true,"internalType":"address","name":"account","type":"address"},{"indexed":true,"internalType":"address","name":"sender","type":"address"}],"name":"RoleGranted","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"bytes32","name":"role","type":"bytes32"},{"indexed":true,"internalType":"address","name":"account","type":"address"},{"indexed":true,"internalType":"address","name":"sender","type":"address"}],"name":"RoleRevoked","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint256","name":"id","type":"uint256"}],"name":"Snapshot","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"from","type":"address"},{"indexed":true,"internalType":"address","name":"to","type":"address"},{"indexed":false,"internalType":"uint256","name":"value","type":"uint256"}],"name":"Transfer","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"account","type":"address"}],"name":"Unpaused","type":"event"},{"inputs":[],"name":"DEFAULT_ADMIN_ROLE","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"DOMAIN_SEPARATOR","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"MINTER_ROLE","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"PAUSER_ROLE","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"SNAPSHOT_ROLE","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"owner","type":"address"},{"internalType":"address","name":"spender","type":"address"}],"name":"allowance","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"spender","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"approve","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"account","type":"address"}],"name":"balanceOf","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"account","type":"address"},{"internalType":"uint256","name":"snapshotId","type":"uint256"}],"name":"balanceOfAt","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"burn","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"account","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"burnFrom","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"decimals","outputs":[{"internalType":"uint8","name":"","type":"uint8"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"spender","type":"address"},{"internalType":"uint256","name":"subtractedValue","type":"uint256"}],"name":"decreaseAllowance","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"bytes32","name":"role","type":"bytes32"}],"name":"getRoleAdmin","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"bytes32","name":"role","type":"bytes32"},{"internalType":"address","name":"account","type":"address"}],"name":"grantRole","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"bytes32","name":"role","type":"bytes32"},{"internalType":"address","name":"account","type":"address"}],"name":"hasRole","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"spender","type":"address"},{"internalType":"uint256","name":"addedValue","type":"uint256"}],"name":"increaseAllowance","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"to","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"mint","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"name","outputs":[{"internalType":"string","name":"","type":"string"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"owner","type":"address"}],"name":"nonces","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"pause","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"paused","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"owner","type":"address"},{"internalType":"address","name":"spender","type":"address"},{"internalType":"uint256","name":"value","type":"uint256"},{"internalType":"uint256","name":"deadline","type":"uint256"},{"internalType":"uint8","name":"v","type":"uint8"},{"internalType":"bytes32","name":"r","type":"bytes32"},{"internalType":"bytes32","name":"s","type":"bytes32"}],"name":"permit","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"bytes32","name":"role","type":"bytes32"},{"internalType":"address","name":"account","type":"address"}],"name":"renounceRole","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"bytes32","name":"role","type":"bytes32"},{"internalType":"address","name":"account","type":"address"}],"name":"revokeRole","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"snapshot","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"bytes4","name":"interfaceId","type":"bytes4"}],"name":"supportsInterface","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"symbol","outputs":[{"internalType":"string","name":"","type":"string"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"totalSupply","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"snapshotId","type":"uint256"}],"name":"totalSupplyAt","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"recipient","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"transfer","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"sender","type":"address"},{"internalType":"address","name":"recipient","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"transferFrom","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"unpause","outputs":[],"stateMutability":"nonpayable","type":"function"}]  

These contracts are ready to use. At the time of the audit, the development of these contracts is considered complete. a certificate was created authorizing the use by the company December 12, 2021. Link: https://github.com/blockchaintechnologysas/audit/blob/main/cert/No2Acta-02CertificadoAuditoriaGranacoinGraco12Diciembre2021.pdf

## Repositorio:
•	https://bitbucket.org/granacoin/graco/ 
•	https://gitlab.com/granacoin/granacoin 
•	https://github.com/granacoin/granacoin 
  
  
# Certificado Digital

No critical vulnerabilities were detected. The reported The Blockchain Technology company with NIT 901366479-3 genres:

That the digital asset identified with the name GRANACOIN, with the abbreviation GRACO, created on December 9, 2021 with the contract 0x84aeA9789137bfEf54915d21DaD85ECbdcdF840b in the Binance Smart Chain Network (BSC), Internal audit document BT-A-002 was created on the date December 12, 2021. The document was stored in the BSC network Contract 0xCc2A4Dc4924EE496787451B7EE0818320B4AA949 with the Hash 0x0c2c86656a7bb40161d4d473fd148334f192a15faf54897c3c941399d .522 Document can be viewed: BT-A-002 Token Granacoin Audit Report 12-12-2021


Audit Certificate Number 2, It is issued in Cali, Valle del Cauca, on the 12th day of December 2021.
