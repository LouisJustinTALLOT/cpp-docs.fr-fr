---
title: Compilateur avertissement (niveau 1) C4503 | Documents Microsoft
ms.custom: ''
ms.date: 05/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60fdb44c5368ccc5c5f089002614332d95a63fe
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255672"
---
# <a name="compiler-warning-level-1-c4503"></a>Avertissement du compilateur (niveau 1) C4503

> '*identificateur*' : nom longueur décoré dépassée, nom a été tronqué.

## <a name="remarks"></a>Notes

Cet avertissement du compilateur est obsolète et n’est pas généré dans Visual Studio 2017 et les compilateurs ultérieure.

Le nom décoré a dépassé la limite du compilateur (4096) et a été tronqué. Pour éviter cet avertissement et la troncature, réduisez le nombre d’arguments ou la longueur des noms d’identificateurs utilisés. Les noms décorés sont plus longtemps que la limite du compilateur un hachage appliqué et ne sont pas risque de conflit de nom.

Lorsque vous utilisez une version antérieure de Visual Studio, cet avertissement peut être émis lors de votre code contient des modèles spécialisé sur des modèles à plusieurs reprises. Par exemple, une table de tables (à partir de la bibliothèque C++ Standard). Dans ce cas, vous pouvez rendre votre typedefs un type (un **struct**, par exemple) qui contient le mappage.

Vous pouvez, toutefois, décider de ne pas restructurer votre code.  Il est possible d’envoyer une application qui génère l’erreur C4503, mais si vous obtenez des erreurs au moment de lien sur un symbole tronqué, il peut être plus difficile de déterminer le type du symbole dans l’erreur. Le débogage peut également être plus difficile ; le débogueur peut avoir le nom du symbole de mappage, il est difficile pour le nom de type. Toutefois, l’exactitude du programme, n’est pas affectée par le nom tronqué.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4503 dans les compilateurs avant Visual Studio 2017 :

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

Cet exemple illustre une manière de réécrire votre code pour résoudre l’erreur C4503 :

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```