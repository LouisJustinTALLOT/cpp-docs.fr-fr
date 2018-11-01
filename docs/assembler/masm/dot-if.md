---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483636"
---
# <a name="if"></a>.IF

Génère du code qui teste `condition1` (par exemple, AX > 7) et exécute la *instructions* si cette condition est vraie.

## <a name="syntax"></a>Syntaxe

> . IF condition1<br/>
> instructions<br/>
> [[. ELSEIF condition2<br/>
> instructions]]<br/>
> [[. ELSE<br/>
> instructions]]<br/>
> .ENDIF

## <a name="remarks"></a>Notes

Si un [. AUTRE](../../assembler/masm/dot-else.md) suit, ses instructions est exécutées si la condition d’origine a la valeur false. Notez que les conditions sont évaluées au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>