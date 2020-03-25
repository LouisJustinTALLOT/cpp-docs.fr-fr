---
title: Évaluateur d'expression, erreur CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196064"
---
# <a name="expression-evaluator-error-cxx0015"></a>Évaluateur d'expression, erreur CXX0015

expression trop complexe (dépassement de capacité de la pile)

L’expression entrée était trop complexe ou imbriquée trop profondément pour la quantité de stockage disponible pour l’évaluateur d’expression C.

Le dépassement de capacité se produit généralement en raison d’un trop grand nombre de calculs en attente.

Réorganisez l’expression afin que chaque composant de l’expression puisse être évalué à mesure qu’elle est rencontrée, au lieu d’attendre que d’autres parties de l’expression soient calculées.

Fractionnez l’expression en plusieurs commandes.

Cette erreur est identique à CAN0015.
