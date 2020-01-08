---
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 6402b75c10b1400d56923116621f00b4d0908822
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318252"
---
# <a name="savexmm128"></a>.SAVEXMM128

Génère un `UWOP_SAVE_XMM128` ou une entrée de code de déroulement `UWOP_SAVE_XMM128_FAR` pour le registre XMM et le décalage spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.

## <a name="syntax"></a>Syntaxe

> **. SAVEXMM128** *xmmreg* , *décalage*

## <a name="remarks"></a>Notes

**. SAVEXMM128** permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration de la trame [proc](proc.md) à l' [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. . Les SAVEXMM128 doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

*offset* doit être un multiple de 16.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
