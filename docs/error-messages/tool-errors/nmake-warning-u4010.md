---
title: Avertissement NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: aa4d2355b18a3c6cc6fc3151c7662fbbbaa665d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298111"
---
# <a name="nmake-warning-u4010"></a>Avertissement NMAKE U4010

'target' : build a échoué ; /K spécifié, suite...

Une commande dans le bloc de commandes de la cible donnée a retourné un code de sortie différent de zéro. L’option /K a indiqué NMAKE pour continuer le traitement des parties non liées de la génération et d’émettre un code de sortie 1 quand la session NMAKE est terminée.

Si la cible donnée est elle-même dépendante d’une autre cible, NMAKE émet un avertissement [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) après cet avertissement.