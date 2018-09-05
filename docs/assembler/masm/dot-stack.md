---
title: . PILE | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95e8d69903fabf60fdb5bc04d90452bdad163a19
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676234"
---
# <a name="stack"></a>.STACK

Lorsqu’il est utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md), définit un segment de pile (avec le nom du segment de pile). Le paramètre facultatif `size` Spécifie le nombre d’octets pour la pile (valeur par défaut 1 024). Le `.STACK` directive ferme automatiquement l’instruction de la pile.

## <a name="syntax"></a>Syntaxe

> . PILE [[taille]]

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>