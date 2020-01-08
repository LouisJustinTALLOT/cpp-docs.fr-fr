---
title: IF (MASM)
ms.date: 12/17/2019
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 38d366a3a41e7b08759594899cdcbb2cb84dfbfa
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317290"
---
# <a name="if"></a>IF

Accorde un assembly de *ifstatements* si *expression1* a la valeur true (différente de zéro) ou *elseifstatements* si *expression1* a la valeur false (0) et si *Expression2* a la valeur true.

## <a name="syntax"></a>Syntaxe

> **Si** *expression1*\
> *If-states*\
> ⟦**ElseIf** *Expression2*\
> *ElseIf-States*⟧ \
> ⟦**ELSE**\
> *else-States*⟧ \
> **ENDIF**

## <a name="remarks"></a>Notes

Les directives suivantes peuvent être remplacées par [ElseIf](elseif-masm.md): **ELSEIFB**, **elseifdef (** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**et **elseifndef (** . Assemble éventuellement *else-States* si l’expression précédente est false. Notez que les expressions sont évaluées au moment de l’assembly.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
