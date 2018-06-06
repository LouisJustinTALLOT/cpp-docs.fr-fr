---
title: Compilateur avertissement (niveau 2) C4412 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4412
dev_langs:
- C++
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47659a9ba0469b8ee719dbc686ba611e876d32c1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704011"
---
# <a name="compiler-warning-level-2-c4412"></a>Avertissement du compilateur (niveau 2) C4412

> '*fonction*' : signature de fonction contient le type '*type*' ; Objets C++ sont unsafe à passer entre le code pure et mixte ou natif.

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Si vous disposez du code qui doit être pure, nous recommandons de porter vers c#.

Le compilateur a détecté une situation potentiellement dangereuse qui peut entraîner une erreur d’exécution : un appel est fait à partir un **/CLR : pure** compiland à une fonction qui a été importée via dllimport et la signature de fonction contienne un type non sécurisé . Un type est unsafe, s’il contient une fonction membre ou un membre de données est un type non sécurisé ou une indirection à un type non sécurisé.

Cela est déconseillé en raison de la différence entre la valeur par défaut conventions entre le code natif pur d’appel (ou mixte natif et managé). Lors de l’importation (via `dllimport`) une fonction dans une **/CLR : pure** compiland, assurez-vous que les déclarations de chaque type dans la signature sont identiques à celles du module qui exporte la fonction (est particulièrement vigilant différences dans les conventions d’appel implicites).

Une fonction membre virtuelle est particulièrement susceptible de provoquer des résultats inattendus.  Toutefois, même une fonction non virtuelle doit être testée pour vous assurer que vous obtenez les résultats corrects. Si vous êtes sûr que vous obtenez les résultats corrects, vous pouvez ignorer cet avertissement.

C4412 est désactivée par défaut. Consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) et [dllexport, dllimport](../../cpp/dllexport-dllimport.md) pour plus d’informations.

Pour résoudre cet avertissement, supprimez toutes les fonctions du type.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4412.

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>Exemple

L’exemple suivant est un fichier d’en-tête qui déclare deux types. Le `Unsafe` type est dangereux, car il possède une fonction membre.

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>Exemple

Cet exemple exporte des fonctions avec les types définis dans le fichier d’en-tête.

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>Exemple

La valeur par défaut de convention d’appel un **/CLR : pure** diffère de la compilation d’une compilation native.  Lorsque C4412.h est inclus, `Test` par défaut est `__clrcall`. Si vous compilez et exécutez ce programme (n’utilisez pas **/c**), le programme lève une exception.

L’exemple suivant génère l’erreur C4412.

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```