---
title: Avertissement du compilateur (niveau 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459785"
---
# <a name="compiler-warning-level-1-c4503"></a>Avertissement du compilateur (niveau 1) C4503

> «*identificateur*' : nom longueur décoré dépassée, nom a été tronqué.

## <a name="remarks"></a>Notes

Cet avertissement du compilateur est obsolète et n’est pas généré dans Visual Studio 2017 et les compilateurs plus loin.

Le nom décoré était plus long que la limite du compilateur (4096) et a été tronqué. Pour éviter cet avertissement et la troncature, réduisez le nombre d’arguments ou les longueurs de nom des identificateurs utilisés. Les noms décorés sont plus longtemps que la limite du compilateur un hachage appliqué et ne sont pas risque de conflit de nom.

Lorsque vous utilisez une version antérieure de Visual Studio, cet avertissement peut être émis lorsque votre code contient des modèles spécialisé sur des modèles à plusieurs reprises. Par exemple, une table de tables (à partir de la bibliothèque C++ Standard). Dans ce cas, vous pouvez créer un type à votre typedefs (un **struct**, par exemple) qui contient le mappage.

Vous pouvez, cependant, décider de ne pas restructurer votre code.  Il est possible de livrer une application qui génère l’erreur C4503, mais si vous obtenez des erreurs au moment du lien sur un symbole tronqué, il peut être plus difficile de déterminer le type du symbole dans l’erreur. Débogage mai également être plus difficile ; le débogueur peut avoir le nom du symbole de mappage éprouvant des difficultés au nom de type. Toutefois, l’exactitude du programme, n’est pas affecté par le nom tronqué.

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