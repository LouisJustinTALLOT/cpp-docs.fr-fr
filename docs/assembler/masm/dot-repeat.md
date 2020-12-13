---
description: En savoir plus sur :. REPEAT (MASM 32 bits)
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: e418093f4ff821b2e99b9e1332b50b64b64ac862
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131220"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (MASM 32 bits)

Génère du code qui répète l’exécution du bloc d' *instructions* jusqu’à ce que la *condition* devienne true. [. UNTILCXZ](dot-untilcxz.md), qui devient true lorsque CX est égal à zéro, peut être substitué à [. JUSQU’à](dot-until.md). La *condition* est facultative avec **. UNTILCXZ**. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. Tab**\
> *publication*\
> **.** *Condition* until

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
