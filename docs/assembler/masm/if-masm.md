---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: ed7b9e63bb19dcc16539dbdaaf1f6a7f16566b3c
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397462"
---
# <a name="if-masm"></a>IF (MASM)

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

Les directives suivantes peuvent être remplacées par [ElseIf](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **elseifdef (** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**et **elseifndef (** . Assemble éventuellement *else-States* si l’expression précédente est false. Notez que les expressions sont évaluées au moment de l’assembly.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
