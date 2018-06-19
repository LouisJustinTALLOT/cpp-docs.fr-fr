---
title: Du compilateur (niveau 4) d’avertissement C4471 | Documents Microsoft
ms.custom: ''
ms.date: 04/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4471
dev_langs:
- C++
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a530cee3c3fcfec8566d46b116fcc4e71760ed11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302683"
---
# <a name="compiler-warning-level-4-c4471"></a>Du compilateur (niveau 4) d’avertissement C4471
'*énumération*' : une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int pris par défaut)  
  
Une déclaration anticipée d’une énumération non délimitée a été trouvée sans un spécificateur pour le type sous-jacent. Par défaut, Visual C++ suppose `int` est le type sous-jacent d’une énumération. Cela peut entraîner des problèmes si un type différent est utilisé dans la définition de l’énumération, par exemple, si un autre type explicit est spécifié, ou si un autre type est implicitement défini par un initialiseur. Vous pouvez également avoir des problèmes de portabilité ; autres compilateurs ne supposent pas `int` est le type sous-jacent d’une énumération.  
  
Cet avertissement est désactivé par défaut. Vous pouvez utiliser Wall ou Wn*N*4471 pour l’activer sur la ligne de commande ou utilisez #pragma [avertissement](../../preprocessor/warning.md) dans votre fichier source.  
  
Dans certains cas, cet avertissement est faux. Si une déclaration anticipée pour une énumération s’affiche après la définition, cet avertissement peut être activé. Par exemple, ce code est valide, même si elle peut entraîner la C4471 :  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>Exemple  
En règle générale, il est plus sûr d’utiliser la définition complète pour une énumération non délimitée au lieu d’une déclaration anticipée. Vous pouvez mettre la définition dans un fichier d’en-tête et incluez-le dans les fichiers sources qui s’y rapportent. Cela fonctionne dans le code écrit pour C ++ 98 et versions ultérieures. Nous vous recommandons de cette solution pour la portabilité et la facilité de maintenance.  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>Exemple  
Dans C ++ 11, vous pouvez ajouter un type explicite pour une énumération non délimitée et sa déclaration anticipée. Nous vous recommandons de cette solution uniquement si la logique d’inclusion d’en-tête complexes empêche l’utilisation de la définition à la place d’une déclaration anticipée. Cette solution peut entraîner un problème de maintenance : Si vous modifiez le type sous-jacent utilisé pour la définition de l’énumération, vous devez également modifier toutes les déclarations vers l’avant pour faire correspondre, ou vous avez peut-être des erreurs en mode silencieux dans votre code. Vous pouvez placer la déclaration anticipée dans un fichier d’en-tête pour minimiser ce problème.  
  
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
  
Si vous spécifiez un type explicite pour une énumération, nous vous recommandons de vous permettent également d’avertissement [C4369](compiler-warning-level-1-C4369.md), qui est activé par défaut. Cela identifie les cas où un élément d’énumération requiert un autre type que le type spécifié de façon explicite.
  
## <a name="example"></a>Exemple  
Vous pouvez modifier votre code pour utiliser un enum limité, une fonctionnalité qui est nouvelle dans C ++ 11. La définition et le code client qui utilise le type d’énumération doivent être modifiées pour utiliser un enum limité. Nous vous recommandons de qu'utiliser un enum limité si vous rencontrez des problèmes avec la pollution d’espace de noms, comme les noms des éléments de l’énumération définie sont limités à la portée de l’enum. Une autre fonctionnalité d’un enum limité est que ses membres ne peut pas être implicitement convertis en un autre type intégral ou énumération, qui peut être une source de bogues subtils.

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
  
