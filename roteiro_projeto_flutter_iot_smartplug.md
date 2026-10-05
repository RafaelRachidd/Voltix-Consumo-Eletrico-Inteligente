# Projeto Flutter + IoT — Gestão de Custos de Energia para Pequenas Empresas

## 1. Visão geral do projeto

### Nome provisório
**EnergiaPME**

### Proposta
Desenvolver um aplicativo mobile em **Flutter**, integrado desde o início a um **Smart Plug Positivo**, para monitorar o consumo de energia elétrica de equipamentos utilizados por pequenas empresas.

O aplicativo deverá transformar os dados coletados pelo dispositivo IoT em informações úteis para gestão, como:

- potência instantânea;
- consumo acumulado;
- custo estimado da energia utilizada;
- histórico de consumo;
- identificação dos equipamentos de maior gasto;
- comparação de consumo entre períodos.

---

# 2. Problema

Pequenas empresas normalmente recebem apenas o valor total da conta de energia elétrica e nem sempre conseguem identificar:

- quais equipamentos consomem mais energia;
- quanto cada equipamento representa no custo mensal;
- quais períodos apresentam maior consumo;
- onde existem oportunidades de economia.

O projeto busca fornecer essas informações de forma simples e acessível.

---

# 3. Público-alvo

O sistema será pensado principalmente para:

- pequenos escritórios;
- lojas;
- salões de beleza;
- oficinas;
- pequenos comércios;
- prestadores de serviços;
- micro e pequenas empresas em geral.

---

# 4. Objetivo geral

Criar um sistema mobile capaz de receber dados reais de consumo energético provenientes de um dispositivo IoT e apresentar essas informações de forma organizada para auxiliar pequenas empresas no controle de seus gastos com eletricidade.

---

# 5. Objetivos específicos

- Integrar o Smart Plug ao ambiente de monitoramento.
- Obter dados reais de consumo de energia.
- Exibir potência e consumo no aplicativo Flutter.
- Permitir associar cada medição a um equipamento.
- Calcular o custo estimado de energia.
- Armazenar dados para consulta posterior.
- Criar um painel simples com indicadores de consumo.
- Comparar períodos de utilização.
- Identificar equipamentos ou períodos de maior gasto.
- Auxiliar na tomada de decisão para redução de custos.

---

# 6. Arquitetura inicial

O fluxo esperado do sistema será:

```text
Equipamento elétrico
        ↓
Smart Plug Positivo
        ↓
Rede Wi-Fi / serviço conectado
        ↓
Camada de integração
        ↓
Banco de dados
        ↓
Aplicativo Flutter
        ↓
Dashboard de consumo e custos
```

A forma exata de integração entre o Smart Plug e o aplicativo deverá ser definida após os primeiros testes com o dispositivo.

---

# 7. Primeira etapa — Configuração do Smart Plug

Antes do desenvolvimento completo do aplicativo, será necessário conhecer o funcionamento real do dispositivo.

## Atividades

- [ ] Configurar o Smart Plug.
- [ ] Conectar o dispositivo ao Wi-Fi.
- [ ] Vincular ao aplicativo oficial.
- [ ] Testar com um equipamento de baixa potência.
- [ ] Verificar quais informações de energia são disponibilizadas.
- [ ] Verificar se existe consumo instantâneo.
- [ ] Verificar se existe consumo acumulado.
- [ ] Verificar se existe histórico.
- [ ] Investigar de que forma os dados podem ser acessados externamente.
- [ ] Registrar resultados dos testes.

## Dados desejados

Preferencialmente:

- potência instantânea em W;
- energia consumida em kWh;
- estado ligado/desligado;
- data e horário da medição;
- histórico de consumo.

> O Smart Plug deverá ser utilizado conforme as especificações do fabricante, sem desmontagem ou modificação da parte elétrica.

---

# 8. Segunda etapa — Estudo da integração

Após configurar o Smart Plug, será estudada a forma de obter seus dados para uso no projeto.

## Objetivo

Criar um caminho para que os dados medidos cheguem ao sistema.

Possível estrutura:

```text
Smart Plug
    ↓
Serviço/API disponível
    ↓
Aplicação intermediária ou banco
    ↓
Flutter
```

## Atividades

- [ ] Identificar se existe API ou integração disponível.
- [ ] Verificar formato dos dados retornados.
- [ ] Registrar um exemplo de leitura.
- [ ] Testar atualização dos valores.
- [ ] Definir como os dados serão armazenados.
- [ ] Definir como o Flutter consultará os dados.

Esta etapa deverá ser concluída antes de avançar para funcionalidades mais complexas.

---

# 9. Terceira etapa — Protótipo de comunicação

O primeiro objetivo técnico será simples:

> **Fazer uma única medição real aparecer no sistema.**

Exemplo:

```text
Equipamento: Ventilador

Potência atual:
72 W

Consumo acumulado:
0,45 kWh
```

## Meta

- [ ] Obter um valor real do Smart Plug.
- [ ] Salvar ou transmitir esse valor.
- [ ] Exibir o valor no aplicativo Flutter.

Somente depois dessa etapa funcionar será ampliado o sistema.

---

# 10. Estrutura dos dados

Cada registro poderá armazenar:

- identificador;
- nome do equipamento;
- setor/local;
- potência instantânea;
- consumo acumulado;
- data;
- horário;
- custo estimado;
- identificação do Smart Plug.

Exemplo conceitual:

```text
Equipamento: Computador Administrativo
Setor: Escritório
Potência: 180 W
Consumo: 1,85 kWh
Data: 05/10/2026
Horário: 14:30
```

---

# 11. Cálculo do custo

O custo da energia será obtido a partir do consumo medido pelo dispositivo.

## Fórmula

\[
C = E \times T
\]

Onde:

- `C` = custo estimado;
- `E` = energia consumida em kWh;
- `T` = tarifa de energia em R$/kWh.

### Exemplo

Se o Smart Plug registrar:

\[
E = 42,5\ kWh
\]

e a empresa cadastrar:

\[
T = R\$0,95/kWh
\]

então:

\[
C = 42,5 \times 0,95
\]

\[
C = R\$40,38
\]

---

# 12. Telas do aplicativo

## Tela 1 — Dashboard

Tela principal com os principais indicadores.

### Exibir

- consumo atual;
- consumo acumulado;
- custo estimado;
- equipamento monitorado;
- status do dispositivo;
- última atualização.

Possível visualização:

```text
Consumo atual
180 W

Consumo acumulado
42,5 kWh

Custo estimado
R$ 40,38

Última leitura
14:30
```

---

## Tela 2 — Equipamentos

Listagem dos equipamentos cadastrados.

Exemplo:

```text
Computador Administrativo
Consumo: 42,5 kWh
Custo: R$ 40,38

Ventilador
Consumo: 18,2 kWh
Custo: R$ 17,29
```

---

## Tela 3 — Cadastro do equipamento

Campos:

- nome;
- setor/local;
- identificação do Smart Plug;
- tarifa utilizada;
- observações.

---

## Tela 4 — Detalhes do equipamento

Exibir:

- nome;
- setor;
- potência atual;
- consumo acumulado;
- custo;
- última medição;
- histórico resumido.

---

## Tela 5 — Histórico

Permitir visualizar o consumo por período.

Exemplos:

- hoje;
- últimos dias;
- mês atual.

Informações:

- consumo do período;
- custo do período;
- maior consumo registrado;
- média de consumo.

---

# 13. Dashboard empresarial

O dashboard deverá transformar medições técnicas em informações fáceis de entender.

## Indicadores desejados

- Consumo total
- Custo total
- Potência atual
- Equipamento de maior consumo
- Maior período de consumo
- Última atualização

Possível evolução:

- gráfico de consumo por período;
- gráfico de custo por equipamento.

---

# 14. Histórico e análise

A parte científica e matemática do projeto será fortalecida pelo tratamento dos dados reais.

Poderão ser calculados:

## Média de consumo

\[
\bar{x} = \frac{x_1+x_2+\cdots+x_n}{n}
\]

## Variação de consumo

Comparação entre períodos:

\[
\Delta E = E_2 - E_1
\]

## Variação percentual

\[
V\% = \frac{E_2-E_1}{E_1}\times100
\]

Isso permitirá responder perguntas como:

- O consumo aumentou ou diminuiu?
- Quanto um equipamento representa no gasto total?
- Qual período teve maior consumo?
- Qual equipamento deve receber atenção primeiro?

---

# 15. Escopo mínimo do MVP

O MVP deverá obrigatoriamente utilizar dados provenientes do Smart Plug.

## Funcionalidades mínimas

- [ ] Smart Plug configurado.
- [ ] Obtenção de uma leitura real.
- [ ] Exibição do valor no Flutter.
- [ ] Cadastro de equipamento.
- [ ] Associação do equipamento ao Smart Plug.
- [ ] Exibição da potência medida.
- [ ] Exibição do consumo acumulado.
- [ ] Cadastro da tarifa de energia.
- [ ] Cálculo do custo.
- [ ] Histórico básico.
- [ ] Dashboard principal.

---

# 16. Funcionalidades secundárias

Somente após o MVP estar funcionando:

- [ ] Comparação entre dias.
- [ ] Comparação entre equipamentos.
- [ ] Gráficos.
- [ ] Alertas de consumo elevado.
- [ ] Meta mensal de gasto.
- [ ] Estimativa de custo até o final do mês.
- [ ] Vários Smart Plugs simultaneamente.

---

# 17. Estratégia de desenvolvimento

O desenvolvimento seguirá a ordem:

```text
SMART PLUG
    ↓
TESTE DE MEDIÇÃO
    ↓
ACESSO AOS DADOS
    ↓
PROTÓTIPO DE INTEGRAÇÃO
    ↓
BANCO DE DADOS
    ↓
FLUTTER
    ↓
DASHBOARD
    ↓
HISTÓRICO
    ↓
ANÁLISES
    ↓
TESTES
```

A integração IoT é parte central do projeto e não será tratada apenas como funcionalidade futura.

---

# 18. Cronograma sugerido

Considerando aproximadamente **3 horas semanais**:

## Semana 1
- Configurar Smart Plug.
- Testar monitoramento.
- Registrar os dados disponíveis.

## Semana 2
- Estudar acesso aos dados.
- Investigar integração.
- Definir arquitetura.

## Semana 3
- Criar primeiro teste de comunicação.
- Obter uma leitura real.

## Semana 4
- Criar estrutura inicial do projeto Flutter.
- Montar tela de leitura do dispositivo.

## Semana 5
- Criar cadastro de equipamentos.
- Associar dispositivo ao equipamento.

## Semana 6
- Implementar cálculo de custos.
- Configurar tarifa.

## Semana 7
- Criar dashboard principal.

## Semana 8
- Criar armazenamento e histórico.

## Semana 9
- Exibir histórico de consumo.

## Semana 10
- Adicionar comparações e indicadores.

## Semana 11
- Melhorar interface.
- Corrigir erros.
- Realizar testes.

## Semana 12
- Testes finais.
- Documentação.
- Preparação da apresentação.

---

# 19. Divisão em marcos

## Marco 1 — IoT funcionando
O Smart Plug está configurado e fornece dados reais.

## Marco 2 — Integração funcionando
O sistema consegue acessar pelo menos uma leitura do dispositivo.

## Marco 3 — Flutter funcionando
O aplicativo exibe os dados recebidos.

## Marco 4 — Gestão funcionando
O aplicativo calcula custos e organiza equipamentos.

## Marco 5 — Histórico funcionando
As medições são armazenadas e podem ser consultadas.

## Marco 6 — Projeto final
Interface revisada, testes realizados e documentação concluída.

---

# 20. Testes

Realizar testes inicialmente com equipamentos simples e compatíveis com os limites do Smart Plug.

Exemplos:

- lâmpada;
- ventilador;
- computador;
- monitor;
- televisão.

## Verificar

- atualização dos dados;
- diferença entre ligado e desligado;
- estabilidade da comunicação;
- armazenamento das medições;
- cálculo do custo;
- comportamento quando o dispositivo estiver offline;
- campos vazios;
- perda de conexão.

---

# 21. Segurança

Como o projeto envolve energia elétrica:

- utilizar o Smart Plug somente dentro das especificações do fabricante;
- não desmontar o dispositivo;
- não realizar alterações internas;
- evitar equipamentos acima da capacidade permitida;
- utilizar tomadas e instalações em boas condições;
- não improvisar conexões elétricas.

O foco do projeto será **software, IoT e análise dos dados**, e não a construção de circuitos ligados diretamente à rede elétrica.

---

# 22. Documentação do projeto

Registrar durante todo o desenvolvimento:

- problema;
- objetivo;
- público-alvo;
- requisitos;
- arquitetura;
- funcionamento do Smart Plug;
- método de integração;
- estrutura do banco;
- telas;
- fórmulas;
- testes;
- resultados;
- limitações;
- possíveis evoluções.

---

# 23. Diferencial do projeto

O sistema não será apenas uma calculadora de consumo.

O diferencial será utilizar:

\[
\boxed{\text{Medições reais}}
\]

obtidas por:

\[
\boxed{\text{IoT}}
\]

e transformá-las em:

\[
\boxed{\text{Informações para gestão empresarial}}
\]

Fluxo principal:

```text
Consumo elétrico real
        ↓
Smart Plug
        ↓
Dados
        ↓
Flutter
        ↓
Análise
        ↓
Custo
        ↓
Decisão empresarial
```

---

# 24. Resultado esperado

Ao final do projeto, uma pequena empresa deverá conseguir:

1. Monitorar um equipamento conectado ao Smart Plug.
2. Visualizar seu consumo real.
3. Acompanhar a potência utilizada.
4. Calcular quanto aquele consumo representa financeiramente.
5. Consultar um histórico.
6. Comparar períodos.
7. Identificar padrões de consumo.
8. Utilizar as informações para reduzir custos.

---

# 25. Princípio do projeto

> **Medir primeiro, compreender depois, economizar como consequência.**

O projeto será desenvolvido com foco em três características:

- **simplicidade de uso;**
- **dados reais por IoT;**
- **utilidade para pequenas empresas.**
