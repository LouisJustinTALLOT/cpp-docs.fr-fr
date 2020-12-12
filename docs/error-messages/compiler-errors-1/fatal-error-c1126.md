---
description: 'En savoir plus sur : erreur irrécupérable C1126'
title: Erreur irrécupérable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: d6898b65bafa6862c77b10aa362ffc0a0df6e597
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181004"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126

'identificateur' : l’allocation automatique dépasse la taille

L’espace alloué pour les variables locales d’une fonction (plus une quantité limitée d’espace utilisé par le compilateur, comme des 20 octets supplémentaires pour les fonctions remplaçables) dépasse la limite.

Pour corriger cette erreur, utilisez `malloc` ou **`new`** pour allouer de grandes quantités de données.
