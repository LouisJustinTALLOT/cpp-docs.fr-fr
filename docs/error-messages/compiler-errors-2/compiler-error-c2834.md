---
title: Erreur du compilateur C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677602"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834

'operator opérateur' doit être globalement qualifié

Le `new` et `delete` opérateurs sont liées à la classe dans laquelle ils résident. Résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` d’une autre classe. Pour implémenter plusieurs formes de la `new` ou `delete` opérateur, créer une version de l’opérateur avec des paramètres formels supplémentaires.