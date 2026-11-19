# Iluminação pública inteligente e renovável na Avenida Paulista

**Global Solution 2026.2 | Soluções em Energias Renováveis e Sustentáveis (SERS) | Ciência da Computação**
**Desafio integrador:** Neighborhood Action Dashboard (CitizenTech)

## Identificação

| Campo | Informação |
|---|---|
| Integrante | Carlos Augusto Mantovani da Silva |
| RM | 566604 |
| Turma | 1CCPR |
| Modalidade | Trabalho individual |
| Disciplina | Soluções em Energias Renováveis e Sustentáveis (SERS) |

> Este repositório documenta a **contribuição de SERS** ao Neighborhood Action Dashboard. Caso seja integrado a um repositório compartilhado com outras disciplinas, todo o conteúdo desta contribuição está identificado como **SERS**.

---

## 1. Diagnóstico do problema

**Espaço comunitário escolhido:** trecho de 2,8 km da Avenida Paulista, em São Paulo (SP), um dos espaços públicos de maior circulação da cidade.

**Situação atual:** a iluminação da via foi modernizada pela Prefeitura em janeiro de 2024, e as luminárias já são de LED. A norma da via exige 30 lx de iluminância.

**Problema energético:** apesar da troca de tecnologia, a iluminação opera com **fluxo constante durante toda a noite**, sem monitoramento de consumo por ponto e sem fonte renovável associada. O custo de energia é pago pelo município, e a eficiência já obtida com o LED não é aproveitada para ajustar o fluxo à demanda real de pedestres.

**Público beneficiado:** pedestres, ciclistas, comerciantes e visitantes da Paulista (alto fluxo diário, Metrô e vias abertas a pedestres aos domingos), além do município, que arca com o custo da energia.

**Condições de funcionamento:** operação noturna de cerca de 12 h por dia, 365 dias por ano, com atendimento obrigatório ao nível de 30 lx.

**Benefícios esperados:** redução de consumo e de custo de energia, uso de fonte renovável por compensação de créditos, maior visibilidade do consumo e base de dados para decisões públicas.

## 2. Solução proposta

Foram comparadas três alternativas para a **mesma necessidade** (iluminar o trecho por 12 h/noite, em 1 ano de referência):

| Alternativa | Descrição |
|---|---|
| **A. Base** | LED com fluxo constante (situação atual) |
| **B. Eficiência** | LED com dimerização e telegestão: 6 h a 100% e 6 h a 60% do fluxo |
| **C. Renovável** | B + usina fotovoltaica remota de 128 kWp, que compensa o consumo por créditos na rede (geração distribuída) |

Também foi analisada e **descartada** a alternativa **D (luminárias solares autônomas)**, por sombreamento de prédios e árvores, risco de furto, custo de reposição de baterias e exigência de 30 lx.

## 3. Dados utilizados e fontes

| Dado | Fonte |
|---|---|
| Modernização da Paulista (jan/2024) e norma de 30 lx | [Prefeitura de São Paulo](https://prefeitura.sp.gov.br/w/noticia/avenida-paulista-recebe-novo-projeto-de-modernizacao-e-esta-104-mais-iluminada-1) |
| Extensão de 2,8 km | [Prefeitura de São Paulo](https://prefeitura.sp.gov.br/w/noticia/sao-paulo-comemora-470-anos-com-pontos-historicos-ainda-mais-iluminados) |
| Tipo de lâmpada por ponto de luz (GeoSampa) | [Prefeitura de São Paulo](https://prefeitura.sp.gov.br/web/spregula/w/iluminacao_publica/noticias/319281) |
| Fator de emissão do SIN, média nacional de 2023: 0,0385 tCO₂/MWh | [MCTI](https://www.gov.br/mcti/pt-br/acompanhe-o-mcti/noticias/2024/02/fator-de-emissao-de-co2-na-geracao-de-energia-eletrica-no-brasil-em-2023-e-o-menor-em-12-anos) |
| Fator de emissão mensal de abril de 2025: 0,0289 tCO₂/MWh | [MCTI/SIRENE (via Cenário Energia)](https://cenarioenergia.com.br/2025/06/13/brasil-reduz-intensidade-de-carbono-na-geracao-eletrica-com-inclusao-de-novas-renovaveis-na-base-de-calculo-oficial/) |
| Performance ratio de 0,75 e inclinação ótima de 23° para São Paulo | [IEE-USP, Aplicações da Energia Solar Fotovoltaica](https://edisciplinas.usp.br/pluginfile.php/6848059/mod_resource/content/5/undefined/Curso_IEE0004_Aula_11_2022_1.pdf) |
| Irradiação solar (faixa típica de 4 a 5 kWh/m²·dia) | [CRESESB SunData](http://www.cresesb.cepel.br/sundata/index.php) |

## 4. Premissas

Todos os valores são **projeções condicionadas às premissas abaixo, e não resultados garantidos**. Os itens marcados como "a validar" são estimativas que devem ser confirmadas com dados reais.

| Premissa | Valor | Status |
|---|---|---|
| Pontos de luz no trecho | 450 | A validar no GeoSampa (estimativa: ~225 postes nos dois lados × 2 luminárias) |
| Potência média por luminária | 100 W | A validar no catálogo do fabricante/Ilume |
| Funcionamento | 12 h/noite, 365 noites/ano | Aproximação |
| Perfil de dimerização (B e C) | 6 h a 100% e 6 h a 60% | Premissa |
| Tarifa de energia | R$ 0,65/kWh | A validar (tarifa de iluminação pública, Enel SP/ANEEL) |
| Irradiação no plano inclinado | 4,5 kWh/m²·dia | A validar no CRESESB |
| Performance ratio (PR) | 0,75 | IEE-USP |
| Fator de emissão do SIN | 0,0385 tCO₂/MWh (= 0,0385 kg CO₂/kWh) | MCTI, média de 2023 |
| Custo da usina FV | R$ 4.500/kWp; O&M de 1%/ano | A validar com orçamentos |
| Telegestão/dimerização | R$ 330/ponto | A validar |
| Densidade de potência dos módulos | 0,21 kWp/m² | Premissa |

## 5. Estimativa de consumo e cálculos

Fórmula utilizada: **E = (P × t) / 1000**, com E em kWh, P em W e t em h.

**A. Base (LED, fluxo constante)**
100 W × 12 h = 1,2 kWh/noite → 438 kWh/ano por ponto → 450 pontos = **197.100 kWh/ano** (16.425 kWh/mês).

**B. LED com dimerização**
Horas equivalentes = 6 + 6 × 0,6 = 9,6 h/noite.
100 W × 9,6 h × 365 / 1000 = 350,4 kWh/ano por ponto → **157.680 kWh/ano** (13.140 kWh/mês).
Economia de 39.420 kWh/ano (**20%**).

**C. B + geração fotovoltaica compensada**
Produtividade = 4,5 × 0,75 × 365 ≈ 1.232 kWh/kWp·ano.
Potência necessária = 157.680 / 1.232 ≈ **128 kWp** (cerca de 610 m² de módulos).
A usina só atende a via por **compensação de créditos na rede**, pois a iluminação é noturna e a geração é diurna. A usina não alimenta os postes diretamente e pode ficar em outro local, como o telhado de um prédio público.

**Emissões:** kWh × fator de emissão (kg CO₂/kWh). Para A: 197.100 × 0,0385 ≈ 7.588 kg CO₂e/ano.

O cálculo completo, com todas as fórmulas, está em [`dados/Modelo_Iluminacao_Paulista_SERS.xlsx`](dados/Modelo_Iluminacao_Paulista_SERS.xlsx). Alterar qualquer célula da aba **Premissas** recalcula todo o modelo.

## 6. Comparação das alternativas

### Resultados quantitativos (base: 1 ano)

| Indicador | A (base) | B (dimerização) | C (B + FV) |
|---|---|---|---|
| Consumo bruto (kWh/ano) | 197.100 | 157.680 | 157.680 |
| Consumo líquido da rede (kWh/ano) | 197.100 | 157.680 | 0 (compensado) |
| Economia de energia vs. A | n/a | 20% | 20% (consumo bruto) |
| Custo operacional (R$/ano) | 128.115 | 102.492 | 5.760 (somente O&M) |
| Cobertura FV do consumo | 0% | 0% | ~100% (por compensação) |
| Emissões (kg CO₂e/ano) | 7.588 | 6.071 | ~0 (contabilmente) |
| Investimento (R$) | n/a | 148.500 | 724.500 |
| Payback simples | n/a | ~5,8 anos | ~5,9 anos (conjunto, vs. A) |

### Análise qualitativa

| Alternativa | Viabilidade técnica | Impactos ambientais | Benefícios | Limitações |
|---|---|---|---|---|
| **A. Base** | Já implantada | Consumo de 197 MWh/ano, sem energia renovável associada | Nenhum investimento adicional | Fluxo constante, sem dados por ponto, maior custo |
| **B. Dimerização** | Alta: exige luminárias dimerizáveis e módulos de telegestão | Redução de 20% do consumo e das emissões | Economia imediata, dados de consumo, detecção de falhas | A redução de fluxo pode não cumprir os 30 lx exigidos; exige sensores de presença e testes |
| **C. B + FV** | Média: depende de elegibilidade para compensação (Lei 14.300/2022) e de área disponível (~610 m² de módulos) | Zera o consumo líquido da rede; fabricação e descarte de módulos | Cobertura renovável de ~100%, custo de energia próximo de zero | Maior investimento; a geração é diurna e a carga é noturna, então depende da rede e dos créditos |
| **D. Luminárias solares autônomas (descartada)** | Baixa na Paulista | Baterias e seu descarte | Independência da rede | Sombreamento, furto, custo de baterias, 30 lx |

### Achado importante

Como a matriz elétrica brasileira é muito limpa (0,0385 tCO₂/MWh), as emissões totais da via são de apenas ~7,6 tCO₂e/ano. O argumento mais forte da alternativa C é **econômico e de segurança energética**, e não climático.

## 7. Diagrama conceitual de funcionamento

![Diagrama de blocos da solução](docs/diagrama_blocos_iluminacao_paulista.svg)

O diagrama relaciona:

- **Fonte de energia:** rede elétrica e usina FV remota (por compensação de créditos);
- **Equipamentos consumidores:** 450 luminárias LED;
- **Sensores e dados de consumo:** medição por ponto, agenda de operação e sensor de presença;
- **Lógica de automação:** controle de fluxo (100% a 60% na madrugada);
- **Processamento:** cálculo dos indicadores com as premissas de tarifa e emissões;
- **Indicadores no dashboard:** consumo, economia, custo, cobertura FV e emissões.

## 8. Indicadores energéticos e ambientais

| Indicador | Unidade | Valor em A | Valor em B | Valor em C |
|---|---|---|---|---|
| Consumo de energia | kWh/mês | 16.425 | 13.140 | 13.140 (bruto) |
| Consumo líquido da rede | kWh/mês | 16.425 | 13.140 | 0 |
| Economia energética estimada | kWh/mês e % | n/a | 3.285 (20%) | 3.285 (20%) |
| Redução estimada de custos | R$/mês | n/a | 2.135 | 10.196 |
| Participação de energia renovável (cobertura FV) | % | 0% | 0% | ~100% |
| Emissões estimadas | kg CO₂e/ano | 7.588 | 6.071 | ~0 |
| Emissões evitadas vs. A | kg CO₂e/ano | n/a | 1.518 | 7.588 |
| Payback simples | meses | n/a | ~70 | ~71 |

Todos os valores são calculados por fórmula na planilha e se relacionam diretamente com as premissas da seção 4.

## 9. Integração ao Neighborhood Action Dashboard

A aba **Indicadores** da planilha está em **formato longo** (colunas `cenario`, `indicador`, `valor`, `unidade`), pronta para ser exportada em CSV ou JSON e conectada ao dashboard integrado, que será construído depois com as contribuições de todas as disciplinas.

Painel planejado para SERS: comparação entre os cenários A, B e C, em gráficos de consumo (kWh/mês) e custo (R$/mês), com cartões de economia (%), cobertura FV (%) e emissões evitadas (kg CO₂e/ano), conforme o diagrama da seção 7.

## 10. Estrutura do repositório

```
.
├── README.md
├── dados/
│   └── Modelo_Iluminacao_Paulista_SERS.xlsx   # premissas, cálculos e indicadores
└── docs/
    └── diagrama_blocos_iluminacao_paulista.svg  # diagrama de blocos
```

## 11. Limitações da proposta

- Número de pontos, potência das luminárias, tarifa, custo da usina e custo de telegestão são **estimativas a validar**.
- A dimerização pode não cumprir os 30 lx exigidos na Paulista; é preciso avaliá-la com sensores de presença e restringi-la a horários de baixo movimento.
- A usina FV atende a via apenas por **compensação de créditos** (geração distribuída). A elegibilidade da iluminação pública deve ser verificada na Lei 14.300/2022.
- O payback é simples, sem desconto, sem reajuste tarifário e sem considerar a vida útil dos equipamentos.
- O ganho climático é pequeno por causa do baixo fator de emissão do SIN.
- Sensores e telemetria são conceituais: os dados do dashboard são estimados ou simulados, não medidos em campo.
- Estimativas de economia, geração e redução de impactos são **projeções**, e não resultados garantidos.

## 12. Uso de inteligência artificial generativa

Ferramentas de IA generativa (Claude, da Anthropic) foram usadas como apoio para pesquisar fontes, estruturar o modelo de cálculo e redigir a documentação. O autor é responsável pela verificação dos dados, cálculos e referências, e pela compreensão das decisões técnicas adotadas.

## 13. Referências

1. Prefeitura de São Paulo. *Avenida Paulista recebe novo projeto de modernização*. https://prefeitura.sp.gov.br/w/noticia/avenida-paulista-recebe-novo-projeto-de-modernizacao-e-esta-104-mais-iluminada-1
2. Prefeitura de São Paulo. *São Paulo comemora 470 anos com pontos históricos ainda mais iluminados*. https://prefeitura.sp.gov.br/w/noticia/sao-paulo-comemora-470-anos-com-pontos-historicos-ainda-mais-iluminados
3. Prefeitura de São Paulo. *Iluminação pública e GeoSampa*. https://prefeitura.sp.gov.br/web/spregula/w/iluminacao_publica/noticias/319281
4. MCTI. *Fator de emissão de CO₂ na geração de energia elétrica no Brasil em 2023*. https://www.gov.br/mcti/pt-br/acompanhe-o-mcti/noticias/2024/02/fator-de-emissao-de-co2-na-geracao-de-energia-eletrica-no-brasil-em-2023-e-o-menor-em-12-anos
5. Cenário Energia. *Brasil reduz intensidade de carbono na geração elétrica* (fator de abril de 2025, MCTI/SIRENE). https://cenarioenergia.com.br/2025/06/13/brasil-reduz-intensidade-de-carbono-na-geracao-eletrica-com-inclusao-de-novas-renovaveis-na-base-de-calculo-oficial/
6. IEE-USP. *Aplicações da Energia Solar Fotovoltaica* (IEE0004, 2022). https://edisciplinas.usp.br/pluginfile.php/6848059/mod_resource/content/5/undefined/Curso_IEE0004_Aula_11_2022_1.pdf
7. CRESESB. *SunData: potencial solar*. http://www.cresesb.cepel.br/sundata/index.php
