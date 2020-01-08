---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317277"
---
# <a name="goto"></a>GOTO

Transfère l’assembly à la ligne marquée **:** _macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Notes

**Goto** n’est autorisé que dans [les](for-masm.md)blocs [macro](macro.md), for, [fichi](forc.md), [REPEAT](repeat.md)et [while](while-masm.md) . La cible *macrolabel* doit être la seule directive sur la ligne et doit être précédée d’un signe deux-points de début.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
