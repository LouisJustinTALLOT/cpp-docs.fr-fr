---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317550"
---
# <a name="savereg"></a>.SAVEREG

Génère un `UWOP_SAVE_NONVOL` ou une entrée de code de déroulement `UWOP_SAVE_NONVOL_FAR` pour le registre (*reg*) et le décalage (*offset*) spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.

## <a name="syntax"></a>Syntaxe

> **. SAVEREG** *reg* __,__ *décalage*

## <a name="remarks"></a>Notes

**. SAVEREG** permet aux utilisateurs de ml64. exe de spécifier la façon dont une fonction frame est déroulée et qui est uniquement autorisée dans le prologue, qui s’étend de la déclaration de la trame [proc](proc.md) à l' [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement des `.xdata` et des `.pdata`. **. Les SAVEREG** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
