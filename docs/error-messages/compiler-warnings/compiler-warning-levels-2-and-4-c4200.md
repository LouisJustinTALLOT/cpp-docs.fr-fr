---
description: 'En savoir plus sur : avertissement du compilateur (niveaux 2 et 4) C4200'
title: Avertissement du compilateur (niveaux 2 et 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 7068e98303049db4e64e46abbd9dae14c11395f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234343"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Avertissement du compilateur (niveaux 2 et 4) C4200

extension non standard utilisée : tableau de taille zéro dans un struct/union

Indique qu'une structure ou une union contient un tableau de taille zéro.

La déclaration d’un tableau de taille zéro est une extension Microsoft. Cela provoque un avertissement de niveau 2 lors de la compilation d'un fichier C++ et un avertissement de niveau 4 lors de la compilation d'un fichier C. La compilation C++ génère aussi cet avertissement : « Impossible de générer un constructeur de copie ou un opérateur d'assignation de copie lorsque UDT contient un tableau de taille zéro. » Cet exemple génère l'avertissement C4200 :

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Cette extension non standard est souvent utilisée pour assurer une interface entre le code et les structures de données externes qui ont une longueur variable. Si ce scénario s'applique à votre code, vous pouvez désactiver l'avertissement :

## <a name="example"></a>Exemple

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```
