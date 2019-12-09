---
title: .PUSHFRAME
description: Décrit le. PUSHFRAME directive MASM, utilisée pour spécifier comment dérouler une fonction Frame.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 5f951396291ecb12dab500a364f176106c5daa8b
ms.sourcegitcommit: 2cac0150ab3bc8260f866451019b8e22c7e1ac11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945850"
---
# <a name="pushframe"></a>.PUSHFRAME

Génère une entrée de code de déroulement `UWOP_PUSH_MACHFRAME`. Si le mot clé de **code** facultatif est spécifié, le modificateur 1 est attribué à l’entrée du code de déroulement. Sinon, le modificateur est 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦**code**⟧;;

## <a name="remarks"></a>Notes

. PUSHFRAME permet aux utilisateurs de ml64. exe de spécifier le déroulement d’une fonction Frame. Elle est uniquement autorisée dans le prologue, qui s’étend de la déclaration d’image [proc](../../assembler/masm/proc.md) à la [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les PUSHFRAME** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
