---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398049"
---
# <a name="pushframe"></a>.PUSHFRAME

Génère une entrée de code de déroulement `UWOP_PUSH_MACHFRAME`. Si le *code* facultatif est spécifié, le modificateur 1 est attribué à l’entrée du code de déroulement. Sinon, le modificateur est 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦*code*⟧;;

## <a name="remarks"></a>Notes

. PUSHFRAME permet aux utilisateurs de ml64. exe de spécifier la façon dont une fonction frame est déroulée et qui est uniquement autorisée dans le prologue, qui s’étend de la déclaration de la trame [proc](../../assembler/masm/proc.md) à l' [. Directive ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les PUSHFRAME** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
