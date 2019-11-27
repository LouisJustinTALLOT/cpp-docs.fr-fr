---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 08bc5ab50e15aa59e0c49992d1810c7de20f364e
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397949"
---
# <a name="savexmm128"></a>.SAVEXMM128

Génère un `UWOP_SAVE_XMM128` ou une entrée de code de déroulement `UWOP_SAVE_XMM128_FAR` pour le registre XMM et le décalage spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.

## <a name="syntax"></a>Syntaxe

> **. SAVEXMM128** *xmmreg* , *décalage*

## <a name="remarks"></a>Notes

**. SAVEXMM128** permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame et est uniquement autorisé dans le prologue, qui s’étend de la déclaration de la trame [proc](../../assembler/masm/proc.md) à l' [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. . Les SAVEXMM128 doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

*offset* doit être un multiple de 16.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
