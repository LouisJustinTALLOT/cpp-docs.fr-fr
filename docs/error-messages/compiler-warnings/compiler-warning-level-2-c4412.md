---
title: Avertissement du compilateur (niveau 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665515"
---
# <a name="compiler-warning-level-2-c4412"></a>Avertissement du compilateur (niveau 2) C4412

> «*fonction*' : signature de fonction contient le type '*type*' ; Objets C++ n’est unsafe pour passer entre le code pure et mixte ou natif.

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Si vous avez le code qui doit être pure, nous vous recommandons de porter à C#.

Le compilateur a détecté une situation potentiellement dangereuse susceptibles d’entraîner une erreur d’exécution : un appel est effectué à partir d’un **/CLR : pure** compiland à une fonction qui a été importée via dllimport et la signature de fonction contient un type non sécurisé . Un type est unsafe s’il contient une fonction membre ou un membre de données est un type non sécurisé ou une indirection à un type non sécurisé.

Cela n’est pas sûre en raison de la différence entre la valeur par défaut conventions entre code pur et native d’appel (ou mixte natif et managé). Lors de l’importation (via `dllimport`) une fonction dans un **/CLR : pure** compiland, assurez-vous que les déclarations de chaque type dans la signature sont identiques à celles du module qui exporte la fonction (qui est particulièrement vigilant différences dans les conventions d’appel implicites).

Une fonction membre virtuelle est particulièrement susceptibles d’engendrer des résultats inattendus.  Toutefois, même une fonction non virtuelle doit être testée pour vous assurer d’obtenir les résultats corrects. Si vous êtes sûr que vous obtenez les résultats corrects, vous pouvez ignorer cet avertissement.

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