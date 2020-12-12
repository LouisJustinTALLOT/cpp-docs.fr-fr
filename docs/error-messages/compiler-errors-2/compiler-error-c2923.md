---
description: 'En savoir plus sur : erreur du compilateur C2923'
title: Erreur du compilateur C2923
ms.date: 11/04/2016
f1_keywords:
- C2923
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
ms.openlocfilehash: 7897ba68998f88f82144278e79c97d8fec9f85d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270275"
---
# <a name="compiler-error-c2923"></a>Erreur du compilateur C2923

'type' : 'identifier' n’est pas un argument de type de modèle valide pour le paramètre 'param'.

Il manque un type nécessaire pour instancier le modèle ou le générique dans la liste d’arguments. Vérifiez la déclaration du modèle ou du générique.

L’exemple suivant génère l’erreur C2923 :

```cpp
// C2923.cpp
template <class T> struct TC {};
int x;
int main() {
   TC<x>* tc2;   // C2923
   TC<int>* tc2;   // OK
}
```

L’erreur C2923 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2923b.cpp
// compile with: /clr /c
generic <class T> ref struct GC {};

int x;

int main() {
   GC<x>^ gc2;   // C2923
   GC<int>^ gc2;   // OK
}
```
