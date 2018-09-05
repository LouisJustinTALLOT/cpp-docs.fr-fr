---
title: . RÉPÉTEZ | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8856ed0e1d86277a413baac2c56e5c5ca2ea9ff0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687950"
---
# <a name="repeat"></a>.REPEAT

Génère du code qui répète l’exécution du bloc de *instructions* jusqu'à ce que `condition` prend la valeur true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), qui prend la valeur true lorsque CX est égal à zéro, peut être remplacé par [. Jusqu'à ce que](../../assembler/masm/dot-until.md). Le `condition` est facultatif avec **. UNTILCXZ**.

## <a name="syntax"></a>Syntaxe

> .REPEAT<br/>
> instructions<br/>
> . Jusqu'à ce que la condition

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>