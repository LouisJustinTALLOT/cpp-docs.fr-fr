---
title: Double conversion de code (thunking) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 89cca9ef42910d295cbae8bb677fb51927dbcdd2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988529"
---
# <a name="double-thunking-c"></a>Double conversion de code (thunking) (C++)

Le double médiateur fait référence à la perte de performances que vous pouvez rencontrer quand un appel de fonction dans un contexte managé C++ appelle une fonction Visual managée et où l’exécution du programme appelle le point d’entrée natif de la fonction pour appeler la fonction managée. Cette rubrique explique où se produit le double médiateur et comment vous pouvez l’éviter pour améliorer les performances.

## <a name="remarks"></a>Notes

Par défaut, lors de la compilation avec **/CLR**, la définition d’une fonction managée force le compilateur à générer un point d’entrée managé et un point d’entrée natif. Cela permet d’appeler la fonction managée à partir de sites d’appel natifs et managés. Toutefois, lorsqu’il existe un point d’entrée natif, il peut s’agir du point d’entrée de tous les appels à la fonction. Si une fonction appelante est managée, le point d’entrée natif appellera ensuite le point d’entrée managé. En effet, deux appels sont requis pour appeler la fonction (par conséquent, le double médiateur). Par exemple, les fonctions virtuelles sont toujours appelées par le biais d’un point d’entrée natif.

Une solution consiste à dire au compilateur de ne pas générer de point d’entrée natif pour une fonction managée, que la fonction sera appelée uniquement à partir d’un contexte managé, à l’aide de la Convention d’appel [__clrcall](../cpp/clrcall.md) .

De même, si vous exportez ([dllexport, DllImport](../cpp/dllexport-dllimport.md)) une fonction managée, un point d’entrée natif est généré et toute fonction qui importe et appelle cette fonction appellera via le point d’entrée natif. Pour éviter le double médiateur dans cette situation, n’utilisez pas de sémantique d’exportation/importation native. référencez simplement les métadonnées par le biais de `#using` (consultez [#using directive](../preprocessor/hash-using-directive-cpp.md)).

Le compilateur a été mis à jour pour réduire le double médiateur inutile. Par exemple, toute fonction avec un type managé dans la signature (y compris le type de retour) est marquée implicitement comme `__clrcall`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant illustre le double médiateur. En cas de compilation native (sans **/CLR**), l’appel à la fonction virtuelle dans `main` génère un appel au constructeur de copie de `T`et un appel au destructeur. Un comportement similaire est obtenu lorsque la fonction virtuelle est déclarée avec **/CLR** et `__clrcall`. Toutefois, quand elle vient d’être compilée avec **/CLR**, l’appel de fonction génère un appel au constructeur de copie, mais il existe un autre appel au constructeur de copie en raison du thunk natif à managé.

### <a name="code"></a>Code

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Sortie exemple

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple précédent a montré l’existence d’un double médiateur. Cet exemple illustre son effet. La boucle `for` appelle la fonction virtuelle et le programme signale la durée d’exécution. Le temps le plus lent est signalé lorsque le programme est compilé avec **/CLR**. Les temps les plus rapides sont signalés lors de la compilation sans **/CLR** ou si la fonction virtuelle est déclarée avec `__clrcall`.

### <a name="code"></a>Code

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Sortie exemple

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
