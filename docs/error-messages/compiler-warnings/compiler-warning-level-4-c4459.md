---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4459'
title: Avertissement du compilateur (niveau 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: cc074c0624a392ce058a284eb21661d7d34ae11f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251399"
---
# <a name="compiler-warning-level-4-c4459"></a>Avertissement du compilateur (niveau 4) C4459

> la déclaration de'*identifier*'masque la déclaration globale

La déclaration de l' *identificateur* dans la portée locale masque la déclaration de l' *identificateur* portant le même nom dans la portée globale. Cet avertissement vous informe que les références à l' *identificateur* dans cette portée sont résolues à la version déclarée localement, et non à la version globale, qui peut être ou non votre intention. En règle générale, nous vous recommandons de réduire l’utilisation des variables globales comme une bonne pratique d’ingénierie. Pour réduire la pollution de l’espace de noms global, nous vous recommandons d’utiliser un espace de noms nommé pour les variables globales.

Cet avertissement est nouveau dans Visual Studio 2015, dans le compilateur Microsoft C++ version 18,00. Pour supprimer les avertissements de cette version du compilateur ou d’une version ultérieure lors de la migration de votre code, utilisez l’option du compilateur [/WV : 18](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4459 :

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Une façon de résoudre ce problème consiste à créer un espace de noms pour vos éléments globaux, mais de ne pas utiliser une **`using`** directive pour mettre cet espace de noms dans la portée, de sorte que toutes les références doivent utiliser des noms qualifiés non ambigus :

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
