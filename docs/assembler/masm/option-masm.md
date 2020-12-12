---
description: 'En savoir plus sur : OPTION'
title: OPTION (MASM)
ms.date: 07/15/2020
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: e2ab1f232b63c2a368204584c1fed69efb40e6ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97126228"
---
# <a name="option"></a>OPTION

Active et désactive les fonctionnalités de l’assembleur.

## <a name="syntax"></a>Syntaxe

> **`OPTION`***option-list*

## <a name="remarks"></a>Notes

Les options disponibles sont les suivantes :

:::row:::
   :::column span="":::
      **`CASEMAP`**\
      **`DOTNAME`**\
      **`NODOTNAME`**\
      **`EMULATOR`**\
      **`NOEMULATOR`**\
      **`EPILOGUE`**\
      **`EXPR16`**
   :::column-end:::
   :::column span="":::
      **`EXPR32`**\
      **`LANGUAGE`**\
      **`LJMP`**\
      **`NOLJMP`**\
      **`M510`**\
      **`NOM510`**\
      **`NOKEYWORD`**
   :::column-end:::
   :::column span="":::
      **`NOSIGNEXTEND`**\
      **`OFFSET`**\
      **`OLDMACROS`**\
      **`NOOLDMACROS`**\
      **`OLDSTRUCTS`**\
      **`NOOLDSTRUCTS`**\
      **`PROC`**
   :::column-end:::
   :::column span="":::
      **`PROLOGUE`**\
      **`READONLY`**\
      **`NOREADONLY`**\
      **`SCOPED`**\
      **`NOSCOPED`**\
      **`SEGMENT`**\
      **`SETIF2`**
   :::column-end:::
:::row-end:::

La syntaxe de Language est **`OPTION LANGUAGE:`** _`x`_ , où *`x`* est l’un des,,,, **`C`** **`SYSCALL`** **`STDCALL`** **`PASCAL`** **`FORTRAN`** ou **`BASIC`** . **`SYSCALL`**, **`PASCAL`** , **`FORTRAN`** et **`BASIC`** ne sont pas pris en charge avec [`.MODEL`](dot-model.md) **`FLAT`** .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
