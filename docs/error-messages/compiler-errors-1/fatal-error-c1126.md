---
title: Erreur irrécupérable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203632"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126

'identificateur' : l’allocation automatique dépasse la taille

L’espace alloué pour les variables locales d’une fonction (plus une quantité limitée d’espace utilisé par le compilateur, comme des 20 octets supplémentaires pour les fonctions remplaçables) dépasse la limite.

Pour corriger cette erreur, utilisez `malloc` ou `new` pour allouer de grandes quantités de données.
