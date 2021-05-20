# Rede Neuroral Para classificação litológica pytorch

Criação de Rede Neural para classificacao Litológica feita em pytorch. O modelo, a partir de uma série de atributos litólógicos, classifica o tipo de rocha informado.

## Estrutura dos dados

#### Arquivo .csv  com 1.170.511 amostras contendo:
'DEPTH_MD', 'X_LOC', 'Y_LOC', 'Z_LOC', 'CALI', 'RSHA', 'RMED', 'RDEP',
       'RHOB', 'GR', 'NPHI', 'PEF', 'DTC', 'SP', 'BS', 'ROP', 'DCAL', 'DRHO',
       'MUDWEIGHT', 'RMIC', 'FORCE_2020_LITHOFACIES_LITHOLOGY', 'Carbon_Index',
       'Normalized_RHOB', 'Normalized_GR', 'Delta_DTC', 'Delta_RHOB',
       'Delta_GR', 'Delta_DEPTH_MD', 'Delta_Carbon_Index', 'GROUP_encoded',
       'FORMATION_encoded'
       
#### Categorias e distribuiçao
São 11 categorias possíveis de rochas (FORCE_2020_LITHOFACIES_LITHOLOGY):

* Categoria | Quantidade
* 65000.0   | 720803
* 30000.0   | 168937
* 65030.0   | 150455
* 70000.0   |  56320
* 80000.0   |  33329
* 99000.0   |  15245
* 70032.0   |  10513
* 88000.0   |   8213
* 90000.0   |   3820
* 74000.0   |   1688
* 86000.0   |   1085
* 93000.0   |    103
 

## Análise e Treinamento

### Análise Inicial Parte 1 
#### (TrabalhoFinal-Parte1.ipynb)

 * Observou-se um resultado baixo, apesar do modelo bem simples conseeguir algum resultado
 * Percebe-se que nem todas as colunas parecem serem úteis para o modelo e o balanceamento de treino e teste pode ser melhor
 * Verificado overfiting e underfiting, mostrou-se underfiting

### Análise Inicial Parte 2
#### (TrabalhoFinal-Parte2.ipynb)

* Tentou-se balancear os dados e modificar a estrutura da rede neural com mais uma camada sem sucesso
* Verificado overfiting e underfiting, mostrou-se underfiting

### Análise Inicial Parte 3
#### (TrabalhoFinal-Parte3.ipynb)

* Aplicar o StandardScaler mostrou um resultado muito bom
* Aumentando a quantidade de treinamento e diminuindo o learning rate também mostrou-se melhor
* Aplicar MinMaxScaler mostrou-se pior
* Utilizado o stratify nos dados, para pegar um balanceamento melhor para treino mostrou uma boa melhora
* Verificado overfiting e underfiting, mostrou-se equilibradamente melhorado para os dois.

### Análise Inicial Parte 4
#### (TrabalhoFinal-Parte4.ipynb)

* Tentou-se utilizar apenas parte do modelo para gerar resultados, sem muitas melhorias
* Verificado overfiting e underfiting, mostrou-se underfiting

### Análise Inicial Parte 5
#### (TrabalhoFinal-Parte5.ipynb)

* Utilizar mini batch mostrou-se um bom método
* Verificado overfiting e underfiting, mostrou-se equilibradamente melhorado para os dois.
* Estudado como salvar e carregar modelos pytorch para criar modelos finais.

### Trabalho Final Final
#### (TrabalhoFinal Final.ipynb)

* Criados modelos que serão testados mais a fundo com diversas configurações
* Feitos testes e mapeados resultados
* Por fim, treino-se de novo, com mais epocas e menos learning rate o melhor modelo encontrado

## Resultados dos Treinamentos

       Nome 	Normalizado   Função Custo  Otimizador        Learn R     ep. 	Batch 	Drop 	Resultado Acerto(%)
       modeloTres 	Sim 	CrossEntropyLoss 	Adam          0.00015 	40 	Sim 	Não 	0.911287
       modeloTres 	Sim 	CrossEntropyLoss 	RMSprop       0.00015 	40 	Sim 	Não 	0.904969
       modeloTres 	Sim 	CrossEntropyLoss 	Adam 	       0.00150 	3000 	Não 	Não 	0.901616
       modeloTres 	Sim 	CrossEntropyLoss 	RMSprop       0.00150 	3000 	Não 	Não 	0.899224
       modeloTres 	Sim 	CrossEntropyLoss 	SGD 	       0.00015 	40 	Sim 	Não 	0.894760
       modeloDois 	Sim 	CrossEntropyLoss 	Adam 	       0.00150 	4000 	Não 	Sim 	0.888588
       modeloDois 	Sim 	CrossEntropyLoss 	Adam 	       0.00015 	40 	Sim 	Sim 	0.884141
       modeloDois 	Sim 	CrossEntropyLoss 	RMSprop       0.00015 	40 	Sim 	Sim 	0.870988
       modeloDois 	Sim 	CrossEntropyLoss 	RMSprop       0.00150 	4000 	Não 	Sim 	0.869955
       modeloDois 	Sim 	CrossEntropyLoss 	SGD 	       0.00015 	40 	Sim 	Sim 	0.865888
       modeloUm 	Sim 	CrossEntropyLoss 	Adam 	       0.00150 	4000 	Não 	Não 	0.861292
       modeloUm 	Sim 	CrossEntropyLoss 	Adam 	       0.00015 	40 	Sim 	Não 	0.853983
       modeloUm 	Sim 	CrossEntropyLoss 	RMSprop       0.00015 	40 	Sim 	Não 	0.850814
       modeloUm 	Sim 	CrossEntropyLoss 	RMSprop       0.00150 	4000 	Não 	Não 	0.843197
       modeloUm 	Sim 	CrossEntropyLoss 	SGD 	       0.00015 	40 	Sim 	Não 	0.840301
       modeloTres 	Sim 	CrossEntropyLoss 	SGD 	       0.00150 	3000 	Não 	Não 	0.753045
       modeloDois 	Sim 	CrossEntropyLoss 	SGD 	       0.00150 	4000 	Não 	Sim 	0.736159
       modeloUm 	Sim 	CrossEntropyLoss 	SGD 	       0.00150 	4000 	Não 	Não 	0.731537
       modeloAnalise Não 	CrossEntropyLoss 	SGD 	       0.05000 	100 	Não 	Não 	0.614123
       modeloTres 	Sim 	CrossEntropyLoss 	SGD 	       0.00010 	80 	Sim 	Não 	0.000000
       
## Conclusão

* A função Adam se mostrou a mais adequada para os modelos construidos
* Modelos com mais cadamas mostraram melhores resultados
* Normalizar os dados mostrou-se essencial
* Um menor learning rate e mais epocas mostrou melhores resultados
* Mini Batch mostrou-se bastante efetivo

## Mais informações
Relatório: Trabalho Final Relatório.ipynb

## Autor
Recigio Poffo - recigio@gmail.com
