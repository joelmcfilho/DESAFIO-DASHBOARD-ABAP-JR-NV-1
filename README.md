Projeto criado em resposta ao desafio do curso "ABAP 100%", ministrado por FioriNET (Cristiano Santos).

Segue a especificação funcional do projeto:
3.	Transações
•	VA03
•	VA05
•	VL03N
•	VL10
•	VF03
•	VF05N

4.	Tabelas/View
•	VBAK, KNA1, VBFA, LIKP, VBRK

5.	Parâmetros (STVARV, ZXXXPARAM, ...)

6.	Programas
•	N/A

7.	Objetivo 
Atualmente não existe um relatório standard para mostrar todo o fluxo dos documentos de vendas.
Deve ser criado um relatório que mostre na mesma linha o número da ordem de venda, da remessa (fornecimento) e da fatura.

8.	Especificação Funcional 
Criar um programa que selecione o fluxo dos documentos de vendas e mostre o resultado em forma de relatório.
Este programa deve ter uma tela inicial contendo parâmetros de seleção para usar como filtros. Os filtros são:

Cliente:  kna1-kunnr
Ordem de venda: vbak-vbeln
Remessa: likp-vbeln
Fatura: vbrk-vbeln

O relatório deve conter os seguintes campos:
Tabela VBAK: Ordem de Vendas
VBELN ERDAT ERNAM NETWR WAERK VKORG VTWEG SPART GBSTK KUNNR

Tabela KNA1: Cliente
NAME1
Encontrar NAME1 onde KUNNR = vbak-kunnr

Tabela LIKP: Remessa
VBELN ERDAT VSTEL BTGEW GEWEI

Tabela VBRK: Fatura
VBELN FKDAT MWSBK FKSTO

Condições de ligação para encontrar o fluxo de documentos na tabela vbfa
- de ordem para remessa
Selecionar VBELN onde VBELV = vbak-vbeln, VBTYP_N = J, VBTYP_V = C

- de remessa para fatura
Selecionar vbeln onde vbelv = vbeln da seleção anterior, VBTYP_N = M, VBTYP_V = J

ORIENTAÇÕES TÉCNICAS:
O que voce precisa saber de ABAP:
- tabelas internas
- operações de leitura (select)
- loop, read table, select for all entries
- append
- funções ou classes
- ALV

9.	Cenários de Testes
OV 76
Remessa 0080000028
Fatura 0090000030
