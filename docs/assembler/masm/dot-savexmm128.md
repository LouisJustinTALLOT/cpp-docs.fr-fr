---
description: En savoir plus sur :. SAVEXMM128
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 697598aa5820b029d19da62a817c60455059865e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131116"
---
# <a name="savexmm128"></a>.SAVEXMM128

Génère une `UWOP_SAVE_XMM128` entrée ou un `UWOP_SAVE_XMM128_FAR` Code de déroulement pour le registre XMM et le décalage spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.

## <a name="syntax"></a>Syntaxe

> **. SAVEXMM128** *xmmreg* , *décalage*

## <a name="remarks"></a>Notes

**. SAVEXMM128** permet aux utilisateurs ml64.exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration d’image [proc](proc.md) à la [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata` . . Les SAVEXMM128 doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

*offset* doit être un multiple de 16.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
