---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4412'
title: Avertissement du compilateur (niveau 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 9b7ce857d5b0545ac620e94bda9655dde0f63489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208630"
---
# <a name="compiler-warning-level-2-c4412"></a>Avertissement du compilateur (niveau 2) C4412

> '*fonction*' : la signature de fonction contient le type'*type*'; Les objets C++ ne sont pas sûrs à passer entre le code pur et le code mixte ou natif.

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017. Si vous avez du code qui doit être pur, nous vous recommandons de le porter vers C#.

Le compilateur a détecté une situation potentiellement dangereuse qui pourrait entraîner une erreur d’exécution : un appel est effectué à partir d’un module de sécurité de l’exécution **/clr : pure** vers une fonction qui a été importée via dllimport et la signature de la fonction contient un type non sécurisé. Un type n’est pas sécurisé s’il contient une fonction membre ou a un membre de données qui est un type non sécurisé ou une indirection vers un type unsafe.

Cela est risqué en raison de la différence entre les conventions d’appel par défaut entre le code pur et le code natif (ou natif et managé mixte). Quand vous importez (via `dllimport` ) une fonction dans un module de la fonctionnalité **/clr : pure** , assurez-vous que les déclarations de chaque type dans la signature sont identiques à celles du compiland qui exporte la fonction (ce qui est particulièrement attentif aux différences dans les conventions d’appel implicites).

Une fonction membre virtuelle est particulièrement sujette à des résultats inattendus.  Toutefois, même une fonction non virtuelle doit être testée pour s’assurer que vous disposez des résultats corrects. Si vous êtes sûr que vous obtenez les résultats corrects, vous pouvez ignorer cet avertissement.

C4412 est désactivé par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) et [dllexport](../../cpp/dllexport-dllimport.md) .

Pour résoudre cet avertissement, supprimez toutes les fonctions du type.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4412.

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

L’exemple suivant est un fichier d’en-tête qui déclare deux types. Le `Unsafe` type n’est pas sécurisé, car il a une fonction membre.

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

La Convention d’appel par défaut dans une compilation **/clr : pure** est différente d’une compilation native.  Quand C4412. h est inclus, la `Test` valeur par défaut est `__clrcall` . Si vous compilez et exécutez ce programme (n’utilisez pas **/c**), le programme lèvera une exception.

L’exemple suivant génère l’C4412.

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
