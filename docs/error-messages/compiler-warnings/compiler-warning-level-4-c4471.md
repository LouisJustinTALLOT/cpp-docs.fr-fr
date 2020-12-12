---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4471'
title: Avertissement du compilateur (niveau 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: cef492bf8aab33f46b3f590a13ffa5462a7ca41d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203495"
---
# <a name="compiler-warning-level-4-c4471"></a>Avertissement du compilateur (niveau 4) C4471

'*énumération*' : une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int pris par défaut)

Une déclaration anticipée d’une énumération non délimitée a été trouvée sans spécificateur pour le type sous-jacent. Par défaut, Visual C++ suppose que **`int`** est le type sous-jacent pour une énumération. Cela peut provoquer des problèmes si un type différent est utilisé dans la définition d’énumération, par exemple, si un type explicite différent est spécifié, ou si un type différent est défini implicitement par un initialiseur. Vous pouvez également rencontrer des problèmes de portabilité. les autres compilateurs ne supposent pas que **`int`** est le type sous-jacent d’une énumération.

Cet avertissement est désactivé par défaut. vous pouvez utiliser/Wall ou/w *N* 4471 pour l’activer sur la ligne de commande, ou utiliser #pragma [Avertissement](../../preprocessor/warning.md) dans votre fichier source.

## <a name="examples"></a>Exemples

Dans certains cas, cet avertissement est parasite. Si une déclaration anticipée pour une énumération apparaît après la définition, cet avertissement peut se déclencher. Par exemple, ce code est valide, même s’il peut provoquer C4471 :

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

En général, il est possible d’utiliser la définition complète pour une énumération non définie au lieu d’une déclaration anticipée. Vous pouvez placer la définition dans un fichier d’en-tête et l’inclure dans les fichiers sources qui y font référence. Cela fonctionne dans le code écrit pour C++ 98 et versions ultérieures. Nous vous recommandons cette solution pour la portabilité et la facilité de maintenance.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

En C++ 11, vous pouvez ajouter un type explicite à une énumération non délimitée et à sa déclaration anticipée. Nous vous recommandons cette solution uniquement si la logique d’inclusion d’en-tête complexe empêche l’utilisation de la définition au lieu d’une déclaration anticipée. Cette solution peut entraîner un problème de maintenance : Si vous modifiez le type sous-jacent utilisé pour la définition d’énumération, vous devez également modifier toutes les déclarations anticipées pour qu’elles correspondent, ou vous pouvez avoir des erreurs silencieuses dans votre code. Vous pouvez placer la déclaration anticipée dans un fichier d’en-tête pour réduire ce problème.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

Si vous spécifiez un type explicite pour une énumération, nous vous recommandons d’activer également Warning [C4369](compiler-warning-level-1-C4369.md), qui est activé par défaut. Cela identifie les cas où un élément d’énumération requiert un type différent du type spécifié explicitement.

Vous pouvez modifier votre code pour utiliser une énumération délimitée, une fonctionnalité qui est nouvelle dans C++ 11. La définition et le code client qui utilise le type d’énumération doivent être modifiés pour utiliser une énumération délimitée. Nous vous recommandons d’utiliser une énumération délimitée si vous rencontrez des problèmes de pollution d’espace de noms, car les noms des éléments d’énumération définis sont limités à l’étendue de l’énumération. Une autre fonctionnalité d’une énumération délimitée est que ses membres ne peuvent pas être convertis implicitement en un autre type de type intégral ou énumération, qui peut être une source de bogues subtils.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```
