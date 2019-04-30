---
title: Évaluateur d'expression, erreur CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: f73aef18563426d28a81b92b3c37d1b7e345d0d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397144"
---
# <a name="expression-evaluator-error-cxx0015"></a>Évaluateur d'expression, erreur CXX0015

expression trop complexe (débordement de pile)

L’expression est trop complexe ou imbriquées trop profondément pour la quantité de stockage disponible pour l’évaluateur d’expression de C.

Dépassement de capacité se produit généralement en raison du trop grand nombre de calculs en attente.

Réorganiser l’expression afin que chaque composant de l’expression peut être évaluée tel qu’il est trouvé, au lieu de devoir attendre d’autres parties de l’expression doit être calculée.

Fractionnez l’expression en plusieurs commandes.

Cette erreur est identique à CAN0015.