---
title: Résolution de surcharge des appels de modèles de fonctions
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: a736e89565bb7ab6bc49c3c0f65d12fc9508200c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484264"
---
# <a name="overload-resolution-of-function-template-calls"></a>Résolution de surcharge des appels de modèles de fonctions

Un modèle de fonction peut surcharger des fonctions non basées sur un modèle du même nom. Dans ce scénario, les appels de fonction sont résolus d’abord en utilisant la déduction de l’argument template pour instancier le modèle de fonction avec une seule spécialisation. Si la déduction d’argument template échoue, les autres surcharges de fonction sont prises en compte pour résoudre l’appel. Ces autres surcharges, également connues comme étant l'ensemble de candidats, incluent des fonctions non basées sur un modèle et d'autres modèles de fonctions instanciés. Si la déduction d’arguments template réussit, la fonction générée est comparée aux autres fonctions pour déterminer la meilleure correspondance, d’après les règles relative à la résolution de la surcharge. Pour plus d’informations, consultez [surcharge de fonction](function-overloading.md).

## <a name="example"></a>Exemple

Si une fonction non basée sur un modèle est une correspondance également correcte par rapport à une fonction de modèle, c’est elle qui est choisie (sauf si les arguments template ont été explicitement spécifiés), comme dans l’appel `f(1, 1)` illustré dans l’exemple suivant.

```cpp
// template_name_resolution9.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }
void f(char, char) { cout << "f(char, char)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   f(1, 1);   // Equally good match; choose the nontemplate function.
   f('a', 1); // Chooses the template function.
   f<int, int>(2, 2);  // Template arguments explicitly specified.
}
```

```Output
f(int, int)
void f(T1, T2)
void f(T1, T2)
```

## <a name="example"></a>Exemple

L'exemple suivant montre que la fonction de modèle à correspondance exacte est privilégiée si la fonction non basée sur un modèle requiert une conversion.

```cpp
// template_name_resolution10.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   long l = 0;
   int i = 0;
   // Call the template function f(long, int) because f(int, int)
   // would require a conversion from long to int.
   f(l, i);
}
```

```Output
void f(T1, T2)
```

## <a name="see-also"></a>Voir aussi

[Résolution de noms](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)