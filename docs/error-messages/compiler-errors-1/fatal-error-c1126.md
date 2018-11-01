---
title: Erreur irrécupérable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457773"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126

'identificateur' : l’allocation automatique dépasse la taille

Espace alloué pour les variables locales de fonction (plus d’une quantité limitée d’espace utilisée par le compilateur, notamment un 20 octets supplémentaires pour les fonctions remplaçables à) dépasse la limite.

Pour corriger cette erreur, utilisez `malloc` ou `new` pour allouer de grandes quantités de données.