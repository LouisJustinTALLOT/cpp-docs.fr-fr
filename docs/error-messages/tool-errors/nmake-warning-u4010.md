---
title: Avertissement NMAKE U4010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117491"
---
# <a name="nmake-warning-u4010"></a>Avertissement NMAKE U4010

'target' : build a échoué ; /K spécifié, suite...

Une commande dans le bloc de commandes de la cible donnée a retourné un code de sortie différent de zéro. L’option /K a indiqué NMAKE pour continuer le traitement des parties non liées de la génération et d’émettre un code de sortie 1 quand la session NMAKE est terminée.

Si la cible donnée est elle-même dépendante d’une autre cible, NMAKE émet un avertissement [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) après cet avertissement.