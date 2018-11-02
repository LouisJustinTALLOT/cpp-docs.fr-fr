---
title: Valeurs de retour (C++)
ms.date: 11/04/2016
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
ms.openlocfilehash: 047058a18597384a3da47d1c22874c7a297f1a48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463568"
---
# <a name="return-values-c"></a>Valeurs de retour (C++)

Une valeur de retour scalaire qui peut être stockée sur 64 bits est retournée via RAX. Ceci inclut les types __m64. Les types non scalaires, y compris les valeurs float, double et types de vecteur, tels que [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) sont retournées dans XMM0. L'état des bits non utilisés dans la valeur retournée dans RAX ou XMM0 est non défini.

Les types définis par l'utilisateur peuvent être retournés par valeur depuis des fonctions globales et des fonctions de membres statiques. Pour être retournés par valeur dans RAX, les types définis par l'utilisateur doivent avoir une longueur de 1, 2, 4, 8, 16, 32 ou 64 bits, et pas de constructeur, de destructeur ou d'opérateur d'affectation de copie, pas de membre de données non statique privé ou protégé, pas de membre de données non statique de type référence, pas de classe de base, pas de fonction virtuelle et pas de membre de données qui ne répondent pas également à ces spécifications requises. (Il s'agit essentiellement de la définition d'un type POD de C++ 03. Comme la définition a été modifiée dans la norme C++ 11, nous déconseillons l'utilisation de `std::is_pod` pour ce test.) Sinon, l'appelant prend la responsabilité d'allouer de la mémoire et de passer un pointeur pour la valeur de retour comme premier argument. Les arguments suivants sont décalés d'un argument vers la droite. Le même pointeur doit être retourné par l'appelé dans RAX.

Ces exemples montrent comment les paramètres et les valeurs de retour sont passés pour les fonctions avec les déclarations spécifiées :

## <a name="example-of-return-value-1---64-bit-result"></a>Exemple de résultat de 1 à 64 bits de valeur de retour

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

## <a name="example-of-return-value-2---128-bit-result"></a>Exemple de résultat de 2-128 bits de valeur de retour

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Exemple de valeur de retour 3 : résultat de type utilisateur par pointeur

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

## <a name="example-of-return-value-4---user-type-result-by-value"></a>Exemple de valeur de retour 4 : résultat de type utilisateur par valeur

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)