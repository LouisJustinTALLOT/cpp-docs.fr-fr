---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703784"
---
# <a name="if-32-bit-masm"></a>. IF (MASM 32 bits)

Génère du code qui teste `condition1` (par exemple, AX > 7) et exécute les *instructions* si cette condition a la valeur true. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> . SI condition1<br/>
> instructions<br/>
> [[. ELSEIF condition2<br/>
> instructions]]<br/>
> [[. TIERCE<br/>
> instructions]]<br/>
> .ENDIF

## <a name="remarks"></a>Notes

Si un [. SINON](../../assembler/masm/dot-else.md) , ses instructions sont exécutées si la condition d’origine a la valeur false. Notez que les conditions sont évaluées au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>