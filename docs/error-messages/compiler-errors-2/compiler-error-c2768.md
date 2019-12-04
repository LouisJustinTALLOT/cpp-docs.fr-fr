---
title: Erreur du compilateur C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759787"
---
# <a name="compiler-error-c2768"></a>Erreur du compilateur C2768

'fonction' : utilisation non conforme d’arguments template explicites

Le compilateur n’a pas pu déterminer si une définition de fonction était supposée être une spécialisation explicite d’un modèle de fonction ou si la définition de fonction était supposée être pour une nouvelle fonction.

Cette erreur a été introduite dans Visual Studio .NET 2003, dans le cadre des améliorations de la conformité du compilateur.

L’exemple suivant génère l’C2768 :

```cpp
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
