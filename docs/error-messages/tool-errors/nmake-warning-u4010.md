---
description: 'En savoir plus sur : NMAKE Warning U4010'
title: Avertissement NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: d0c72044576ebf3441fdec7980c933edec671097
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334795"
---
# <a name="nmake-warning-u4010"></a>Avertissement NMAKE U4010

'target' : la génération a échoué ; /K spécifié, en continuant...

Une commande du bloc de commandes pour la cible donnée a retourné un code de sortie différent de zéro. L’option/K a indiqué à NMAKE de poursuivre le traitement des parties non liées de la build et d’émettre un code de sortie 1 lorsque la session NMAKE est terminée.

Si la cible donnée est, elle-même, dépendante d’une autre cible, NMAKE émet un avertissement [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) après cet avertissement.
