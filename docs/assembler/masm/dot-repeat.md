---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: f21f3f3cc4cb86b1ca2503d515dcd7fbcdffe622
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318278"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (MASM 32 bits)

Génère du code qui répète l’exécution du bloc d' *instructions* jusqu’à ce que la *condition* devienne true. [. UNTILCXZ](dot-untilcxz.md), qui devient true lorsque CX est égal à zéro, peut être substitué à [. JUSQU’à](dot-until.md). La *condition* est facultative avec **. UNTILCXZ**. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. RÉPÉTER**\
> *instructions*\
> **.**  *Condition* until

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
