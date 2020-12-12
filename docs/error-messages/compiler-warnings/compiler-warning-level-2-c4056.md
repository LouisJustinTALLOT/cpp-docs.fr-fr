---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4056'
title: Avertissement du compilateur (niveau 2) C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 5d8b96e97197e43bf288476e310ddd842a90ec48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326542"
---
# <a name="compiler-warning-level-2-c4056"></a>Avertissement du compilateur (niveau 2) C4056

débordement de l’arithmétique constante à virgule flottante

L’arithmétique de constante à virgule flottante génère un résultat qui dépasse la valeur maximale autorisée.

Cet avertissement peut être provoqué par des optimisations du compilateur effectuées pendant une opération arithmétique de constante. Vous pouvez ignorer cet avertissement en toute sécurité si elle est supprimée lorsque vous désactivez l’optimisation ([/OD](../../build/reference/od-disable-debug.md)).

L’exemple suivant génère l’C4056 :

```cpp
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```
