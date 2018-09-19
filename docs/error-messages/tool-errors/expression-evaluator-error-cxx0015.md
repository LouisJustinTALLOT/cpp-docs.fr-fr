---
title: Évaluateur d’expression, erreur CXX0015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050814"
---
# <a name="expression-evaluator-error-cxx0015"></a>Évaluateur d'expression, erreur CXX0015

expression trop complexe (débordement de pile)

L’expression est trop complexe ou imbriquées trop profondément pour la quantité de stockage disponible pour l’évaluateur d’expression de C.

Dépassement de capacité se produit généralement en raison du trop grand nombre de calculs en attente.

Réorganiser l’expression afin que chaque composant de l’expression peut être évaluée tel qu’il est trouvé, au lieu de devoir attendre d’autres parties de l’expression doit être calculée.

Fractionnez l’expression en plusieurs commandes.

Cette erreur est identique à CAN0015.