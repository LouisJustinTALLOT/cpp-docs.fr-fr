---
title: .PUSHFRAME
description: Décrit le. PUSHFRAME directive MASM, utilisée pour spécifier comment dérouler une fonction Frame.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 0aaec119d26d87fddb1eba505458da1250a5926e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317576"
---
# <a name="pushframe"></a>.PUSHFRAME

Génère une entrée de code de déroulement `UWOP_PUSH_MACHFRAME`. Si le mot clé de **code** facultatif est spécifié, le modificateur 1 est attribué à l’entrée du code de déroulement. Sinon, le modificateur est 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦**code**⟧;;

## <a name="remarks"></a>Notes

. PUSHFRAME permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame. Elle est uniquement autorisée dans le prologue, qui s’étend de la déclaration d’image [proc](proc.md) à la [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les PUSHFRAME** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
