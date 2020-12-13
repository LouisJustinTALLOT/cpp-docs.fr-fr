---
description: En savoir plus sur :. IF (MASM 32 bits)
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: e6ce9695f90a90665aee1cdaf15167963360fe04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131675"
---
# <a name="if-32-bit-masm"></a>. IF (MASM 32 bits)

Génère du code qui teste l’erreur *condition1* (par exemple, ax > 7) et exécute les *instructions* si cette condition a la valeur true. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. Si** *condition1*\
> *publication*\
> ⟦**. ELSEIF** *condition2*\
> *instructions*⟧ \
> ⟦**. SINON**\
> *instructions*⟧ \
> **. ENDIF**

## <a name="remarks"></a>Notes

Si un [. SINON](dot-else.md) , ses instructions sont exécutées si la condition d’origine a la valeur false. Notez que les conditions sont évaluées au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
