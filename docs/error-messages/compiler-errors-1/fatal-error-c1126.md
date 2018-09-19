---
title: Erreur irrécupérable C1126 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062473"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126

'identificateur' : l’allocation automatique dépasse la taille

Espace alloué pour les variables locales de fonction (plus d’une quantité limitée d’espace utilisée par le compilateur, notamment un 20 octets supplémentaires pour les fonctions remplaçables à) dépasse la limite.

Pour corriger cette erreur, utilisez `malloc` ou `new` pour allouer de grandes quantités de données.