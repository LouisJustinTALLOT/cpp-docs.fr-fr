---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: e8213052dce8d84d62f90d4bc2653435c2b31434
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398225"
---
# <a name="if-32-bit-masm"></a>. IF (MASM 32 bits)

Génère du code qui teste l’erreur *condition1* (par exemple, ax > 7) et exécute les *instructions* si cette condition a la valeur true. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. Si** *condition1*\
> *instructions*\
> ⟦ **. ELSEIF** *condition2*\
> *instructions*⟧ \
> ⟦ **. SINON**\
> *instructions*⟧ \
> **.ENDIF**

## <a name="remarks"></a>Notes

Si un [. SINON](../../assembler/masm/dot-else.md) , ses instructions sont exécutées si la condition d’origine a la valeur false. Notez que les conditions sont évaluées au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
