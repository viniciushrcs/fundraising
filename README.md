# FundMe - Projeto de Arrecadação de Fundos

## Descrição

O projeto FundMe é uma aplicação descentralizada (dApp) criada para facilitar a arrecadação de fundos em Ether (ETH) utilizando a rede Ethereum. O projeto utiliza um contrato inteligente chamado `FundMe.sol` e uma biblioteca chamada `PriceConverter.sol` para garantir que todas as contribuições sejam feitas em um valor mínimo em dólar (USD).

## Recursos

- Arrecadação de fundos com valor mínimo definido em dólares (USD)
- Utiliza Chainlink para obter a taxa de câmbio ETH/USD em tempo real
- Apenas o dono do contrato pode retirar os fundos arrecadados
- Funções de visualização para obter informações sobre os doadores e o valor doado

## Como usar

1. Faça o deploy do contrato `FundMe.sol` na rede Ethereum. Certifique-se de fornecer o endereço do contrato Chainlink Price Feed ao implantar o contrato.

2. Interaja com o contrato através de uma carteira Ethereum (por exemplo, MetaMask) ou um aplicativo front-end.

   - Para doar, envie uma transação para a função `fund()` com o valor de Ether desejado. O contrato verificará se a quantia convertida em dólares é maior ou igual ao mínimo exigido (por exemplo, 50 dólares) usando a biblioteca `PriceConverter.sol`. Se a condição for atendida, sua doação será aceita e registrada no contrato.

   - O dono do contrato pode retirar os fundos acumulados chamando a função `withdraw()`. Isso transferirá o saldo do contrato para o endereço do proprietário e zerará os valores doados pelos doadores.

3. O contrato também possui funções de visualização que permitem obter informações sobre os doadores e seus respectivos valores doados:

   - `getAddressToAmountFunded(address)`: Retorna o valor doado por um endereço específico
   - `getFunder(uint256)`: Retorna o endereço de um doador com base no índice fornecido
   - `getOwner()`: Retorna o endereço do proprietário do contrato
   - `getPriceFeed()`: Retorna o endereço do contrato Chainlink Price Feed usado para obter a taxa de câmbio ETH/USD

## Biblioteca PriceConverter.sol

A biblioteca `PriceConverter.sol` é usada para converter o valor em Ether doado para dólares americanos (USD) com base na taxa de câmbio obtida do Chainlink Price Feed.

- `getPrice(AggregatorV3Interface)`: Retorna a taxa de câmbio ETH/USD com precisão de 18 dígitos
- `getEthAmountInUsd(uint256, AggregatorV3Interface)`: Converte um valor em Ether para dólares americanos usando a taxa de câmbio ETH/USD

## Dependências

- [Solidity](https://soliditylang.org/) versão 0.8.0 ou superior
- [Chainlink Price Feed](https://docs.chain.link/docs/using-chainlink-reference-contracts/): Contrato para obter a taxa de câmbio ETH/USD em tempo real

## Contribuindo

Sinta-se à vontade para contribuir com este projeto, seja corrigindo bugs, adicionando novos recursos ou melhorando a documentação. Todos são bem-vindos para ajudar a melhor