---
title: . IF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691542"
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