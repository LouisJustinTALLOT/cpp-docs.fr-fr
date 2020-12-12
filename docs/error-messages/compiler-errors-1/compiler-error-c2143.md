---
description: 'En savoir plus sur : erreur du compilateur C2143'
title: Erreur du compilateur C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 4218a14520016ef7b9180c2f5c8c7ddee55ffec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235513"
---
# <a name="compiler-error-c2143"></a>Erreur du compilateur C2143

erreur de syntaxe : 'TOKEN1 'manquant avant’Token2 '

Le compilateur attendait un jeton spécifique (autrement dit, un élément de langage autre qu’un espace blanc) et un autre jeton a été trouvé à la place.

Vérifiez la [Référence du langage C++](../../cpp/cpp-language-reference.md) pour déterminer si le code est syntaxiquement incorrect. Étant donné que le compilateur peut signaler cette erreur après avoir rencontré la ligne à l’origine du problème, vérifiez plusieurs lignes de code qui précèdent l’erreur.

C2143 peut se produire dans différentes situations.

Cela peut se produire lorsqu’un opérateur qui peut qualifier un nom ( `::` , `->` et `.` ) doit être suivi du mot clé **`template`** , comme dans cet exemple :

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

Par défaut, C++ part du principe que `Ty::PutFuncType` n’est pas un modèle ; par conséquent, le code suivant `<` est interprété comme un signe « inférieur à ».  Vous devez indiquer explicitement au compilateur qu' `PutFuncType` il s’agit d’un modèle afin qu’il puisse analyser correctement le Chevron. Pour corriger cette erreur, utilisez le **`template`** mot clé sur le nom du type dépendant, comme illustré ici :

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 peut se produire lorsque **/CLR** est utilisé et qu’une **`using`** directive contient une erreur de syntaxe :

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

Cela peut également se produire lorsque vous essayez de compiler un fichier de code source à l’aide de la syntaxe CLR sans également utiliser **/CLR**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

Le premier caractère autre qu’un espace blanc qui suit une **`if`** instruction doit être une parenthèse ouvrante. Le compilateur ne peut pas traduire autre chose :

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 peut se produire lorsqu’une accolade fermante, une parenthèse ou un point-virgule est manquante sur la ligne où l’erreur est détectée ou sur l’une des lignes juste au-dessus :

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

Ou lorsqu’il existe une balise non valide dans une déclaration de classe :

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

Ou lorsqu’une étiquette n’est pas attachée à une instruction. Si vous devez placer une étiquette seule, par exemple à la fin d’une instruction composée, attachez-la à une instruction null :

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

L’erreur peut se produire lorsqu’un appel non qualifié est effectué à un type dans la bibliothèque C++ standard :

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

Ou il manque un **`typename`** mot clé :

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

Ou si vous essayez de définir une instanciation explicite :

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

Dans un programme C, les variables doivent être déclarées au début de la fonction, et elles ne peuvent pas être déclarées une fois que la fonction a exécuté des instructions de non-déclaration.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
