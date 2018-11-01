---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: 759ee503acb12f6c1a30fbbfaf87a8f66433e571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463243"
---
# <a name="const-c"></a>const (C++)

Lorsque vous modifiez une déclaration de données, le **const** mot clé spécifie que l’objet ou la variable n’est pas modifiable.

## <a name="syntax"></a>Syntaxe

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>Valeurs const

Le **const** mot clé spécifie que la valeur d’une variable est constante et indique au compilateur d’empêcher le programmeur de le modifier.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

En C++, vous pouvez utiliser la **const** mot clé au lieu du [#define](../preprocessor/hash-define-directive-c-cpp.md) directive de préprocesseur à définir des valeurs constantes. Valeurs définies avec **const** sont soumises à la vérification de type et peut être utilisé à la place d’expressions constantes. En C++, vous pouvez spécifier la taille d’un tableau avec un **const** variable comme suit :

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

En C, les valeurs de constante utilisent par défaut la liaison externe. Elles ne peuvent donc apparaître que dans des fichiers sources. En C++, les valeurs de constante utilisent par défaut la liaison interne, ce qui leur permet d'apparaître dans les fichiers d'en-tête.

Le **const** mot clé peut également être utilisé dans les déclarations de pointeur.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Un pointeur vers une variable déclarée comme **const** peut être affecté qu’à un pointeur qui est également déclaré comme **const**.

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

Vous pouvez utiliser des pointeurs vers des données constantes comme paramètres de fonction pour empêcher la fonction de modifier un paramètre passé par l'intermédiaire d'un pointeur.

Pour les objets qui sont déclarés comme **const**, vous pouvez uniquement appeler constante fonctions membres. Cela garantit que l'objet constant n'est jamais modifié.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Vous pouvez appeler des fonctions membres de constante ou non constante pour un objet non constant. Vous pouvez aussi surcharger une fonction membre en utilisant le **const** mot-clé ; ainsi, une version différente de la fonction à appeler pour les objets constants et.

Vous ne pouvez pas déclarer des constructeurs ou les destructeurs avec le **const** mot clé.

## <a name="const-member-functions"></a>Fonctions membres const

Déclaration d’une fonction membre avec le **const** mot clé spécifie que la fonction est une fonction « read-only » qui ne modifie pas l’objet pour lequel elle est appelée. Une fonction membre constante ne peut pas modifier les membres de données non statiques ou appeler des fonctions qui ne sont pas constantes membres. Pour déclarer une fonction membre constante, placez le **const** mot clé après la parenthèse fermante de la liste d’arguments. Le **const** mot clé est requis dans la déclaration et la définition.

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>Différences entre const de C et C++

Lorsque vous déclarez une variable en tant que **const** dans un fichier de code source C, vous procédez comme suit :

```cpp
const int i = 2;
```

Vous pouvez ensuite utiliser cette variable dans un autre module comme suit :

```cpp
extern const int i;
```

Mais pour obtenir le même comportement en C++, vous devez déclarer votre **const** variable en tant que :

```cpp
extern const int i = 2;
```

Si vous souhaitez déclarer une **extern** variable dans un fichier de code source C++ pour une utilisation dans un fichier de code source C, utilisez :

```cpp
extern "C" const int x=10;
```

pour empêcher que le compilateur C++ altère les noms.

## <a name="remarks"></a>Notes

Lorsque vous suivez la liste des paramètres d’une fonction membre, le **const** mot clé spécifie que la fonction ne modifie pas l’objet pour lequel il est appelé.

Pour plus d’informations sur **const**, consultez les rubriques suivantes :

- [const et volatile, pointeurs](../cpp/const-and-volatile-pointers.md)

- [Qualificateurs de type (référence du langage C)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)