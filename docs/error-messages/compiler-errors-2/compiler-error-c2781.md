---
description: 'En savoir plus sur : erreur du compilateur C2781'
title: Erreur du compilateur C2781
ms.date: 11/04/2016
f1_keywords:
- C2781
helpviewer_keywords:
- C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
ms.openlocfilehash: 9d99353b808494b20007784dd6016097afc783d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298004"
---
# <a name="compiler-error-c2781"></a>Erreur du compilateur C2781

'declaration' : attend au moins value1 argument-value2 fourni

Un modèle de fonction avec une liste de paramètres de variables a trop peu d’arguments.

L’exemple suivant génère l’C2781 :

```cpp
// C2781.cpp
template<typename T>
void f(T, T, ...){}

int main() {
   f(1);   // C2781

   // try the following line instead
   f(1,1);
}
```
