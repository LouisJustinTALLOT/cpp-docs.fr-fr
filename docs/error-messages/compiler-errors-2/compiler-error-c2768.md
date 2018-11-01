---
title: Erreur du compilateur C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: 9c0fb8fb0a98830aaf061ba980e7bdd7903f25e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626172"
---
# <a name="compiler-error-c2768"></a>Erreur du compilateur C2768

'fonction' : utilisation non conforme d’arguments template explicites

Le compilateur n’a pas pu déterminer si une définition de fonction était supposé pour être une spécialisation explicite d’un modèle de fonction ou si la définition de fonction était supposé pour être pour une nouvelle fonction.

Cette erreur a été introduite dans Visual Studio .NET 2003, dans le cadre des améliorations de la conformité du compilateur.

L’exemple suivant génère l’erreur C2768 :

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```