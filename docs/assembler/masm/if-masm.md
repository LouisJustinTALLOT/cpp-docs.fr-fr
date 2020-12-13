---
description: 'En savoir plus sur : si'
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 09b4bd09155ef848ad165b4e8b0d3a093ade0008
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130207"
---
# <a name="if"></a>IF

Accorde un assembly de *ifstatements* si *expression1* a la valeur true (différente de zéro) ou *elseifstatements* si *expression1* a la valeur false (0) et si *Expression2* a la valeur true.

## <a name="syntax"></a>Syntaxe

> **Si** *expression1*\
> *instructions If*\
> ⟦**ElseIf** *Expression2*\
> *ElseIf-States*⟧ \
> ⟦**Else**\
> *else-States*⟧ \
> **ENDIF**

## <a name="remarks"></a>Notes

Les directives suivantes peuvent être remplacées par [ElseIf](elseif-masm.md): **ELSEIFB**, **elseifdef (**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB** et **elseifndef (**. Assemble éventuellement *else-States* si l’expression précédente est false. Notez que les expressions sont évaluées au moment de l’assembly.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
