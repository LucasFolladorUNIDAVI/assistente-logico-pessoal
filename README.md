# Assistente Lógico Pessoal

> Atividade da disciplina Linguagem de Programação e Paradigmas · UNIDAVI · 2026/2

**Aluno(a):** Lucas
**Linguagem do sistema:** Python

## O que é

Uma base de conhecimento em Prolog (`meus_dados.pl`) com fatos e regras sobre mim e um assistente em linha de comando que consulta essa base pela ponte (`prolog.py`).

## Como executar

Requisitos: SWI-Prolog no PATH e Python 3.

```bash
# testar a ponte
python teste_ponte.py

# executar o assistente
python assistente.py
```

## Minha base

- Fatos: `eu/1`, `cursa/3`, `compromisso/3`, `sabe/2`, `gosta/2`
- Regras: `ocupado/2`, `livre/2`, `o_que_faco/3`, `pode_ensinar/1`, `dia_cheio/1` e a minha regra abaixo

## Minha regra (R6)

```prolog
% R6 · MINHA REGRA: dia em que a minha noite está livre e posso ver
% uma série de que gosto (maratona de série).
maratona(Dia, Serie) :- livre(Dia, noite), gosta(serie, Serie).
```

**O que ela significa:** `maratona(Dia, Serie)` é verdadeira quando existe um dia em que a minha noite está livre e uma série de que eu gosto. O primeiro subobjetivo, `livre(Dia, noite)`, verifica que não tenho aula nem compromisso nesse dia à noite. O segundo, `gosta(serie, Serie)`, escolhe uma das séries cadastradas nos meus gostos. O Prolog combina os dois e devolve cada par dia/série possível.

## Saída real do assistente

```text
=== Assistente pessoal de lucas ===
1. Minhas disciplinas
2. Agenda de um dia
3. Horários livres
4. Estou livre em...?
5. Linguagens que posso ensinar
6. Meus gostos por categoria
7. Dias cheios
8. Minha regra: maratona de série
0. Sair
> 4
Dia: sexta
Turno (manha, tarde, noite): noite

Não: sexta de noite está ocupado (ou dia/turno inválido).

> 7

== Dias cheios (2 turnos ou mais ocupados) ==
  - segunda
  - terca
  - quarta
  - quinta
  - sexta

> 8

== Maratona de série (noite livre) ==
  - segunda à noite: orange is the new black
  - segunda à noite: brooklyn nine nine
  - terca à noite: orange is the new black
  - terca à noite: brooklyn nine nine
  - quinta à noite: orange is the new black
  - quinta à noite: brooklyn nine nine
  - sabado à noite: orange is the new black
  - sabado à noite: brooklyn nine nine
```