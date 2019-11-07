---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703574"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (MASM 32 bits)

Génère du code qui répète l’exécution du bloc d' *instructions* jusqu’à ce que `condition` devienne true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), qui devient true lorsque CX est égal à zéro, peut être substitué à [. JUSQU’à](../../assembler/masm/dot-until.md). La `condition` est facultative avec **. UNTILCXZ**. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> .REPEAT<br/>
> instructions<br/>
> . Condition UNTIL

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>