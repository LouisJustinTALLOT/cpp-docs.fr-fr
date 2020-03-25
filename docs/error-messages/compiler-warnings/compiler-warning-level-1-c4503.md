---
title: Avertissement du compilateur (niveau 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 9077c448f3b5f1d70d18047b91dcf300e606c91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186543"
---
# <a name="compiler-warning-level-1-c4503"></a>Avertissement du compilateur (niveau 1) C4503

> '*identificateur*' : longueur du nom décoré dépassée, le nom a été tronqué

## <a name="remarks"></a>Notes

Cet avertissement du compilateur est obsolète et n’est pas généré dans Visual Studio 2017 et les compilateurs ultérieurs.

Le nom décoré était plus long que la limite du compilateur (4096) et a été tronqué. Pour éviter cet avertissement et la troncation, réduisez le nombre d’arguments ou les longueurs de nom des identificateurs utilisés. Un hachage est appliqué aux noms décorés qui sont plus longs que la limite du compilateur et ne sont pas menacés par une collision de noms.

Lors de l’utilisation d’une version antérieure de Visual Studio, cet avertissement peut être émis lorsque votre code contient des modèles spécialisés sur les modèles de façon répétée. Par exemple, une carte de cartes (à partir C++ de la bibliothèque standard). Dans ce cas, vous pouvez faire de vos typedefs un type (un **struct**, par exemple) qui contient le mappage.

Toutefois, vous pouvez décider de ne pas restructurer votre code.  Il est possible d’expédier une application qui génère des C4503, mais si vous recevez des erreurs de temps de liaison sur un symbole tronqué, il peut être plus difficile de déterminer le type du symbole dans l’erreur. Le débogage peut également être plus difficile ; le débogueur peut avoir difficilement mapper le nom de symbole au nom de type. Toutefois, l’exactitude du programme n’est pas affectée par le nom tronqué.

## <a name="example"></a>Exemple

L’exemple suivant génère des C4503 dans les compilateurs avant Visual Studio 2017 :

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

Cet exemple montre une façon de réécrire votre code pour résoudre C4503 :

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
