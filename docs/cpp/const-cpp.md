---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: cc1f117cc5f26edf9cd85461281b925c97fa5225
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180302"
---
# <a name="const-c"></a>const (C++)

Lors de la modification d’une déclaration de données, le mot clé **const** spécifie que l’objet ou la variable n’est pas modifiable.

## <a name="syntax"></a>Syntaxe

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>Valeurs const

Le mot clé **const** spécifie que la valeur d’une variable est constante et indique au compilateur d’empêcher le programmeur de le modifier.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

Dans C++, vous pouvez utiliser le mot clé **const** au lieu de la directive de préprocesseur [#define](../preprocessor/hash-define-directive-c-cpp.md) pour définir des valeurs constantes. Les valeurs définies avec **const** sont soumises à la vérification de type et peuvent être utilisées à la place d’expressions constantes. Dans C++, vous pouvez spécifier la taille d’un tableau avec une variable **const** comme suit :

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

En C, les valeurs de constante utilisent par défaut la liaison externe. Elles ne peuvent donc apparaître que dans des fichiers sources. En C++, les valeurs de constante utilisent par défaut la liaison interne, ce qui leur permet d'apparaître dans les fichiers d'en-tête.

Le mot clé **const** peut également être utilisé dans les déclarations de pointeur.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Un pointeur vers une variable déclarée comme **const** peut uniquement être assigné à un pointeur qui est également déclaré comme **const**.

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

Pour les objets déclarés comme **const**, vous pouvez uniquement appeler des fonctions membres constantes. Cela garantit que l'objet constant n'est jamais modifié.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Vous pouvez appeler des fonctions membres de constante ou non constante pour un objet non constant. Vous pouvez également surcharger une fonction membre à l’aide du mot clé **const** ; Cela permet d’appeler une version différente de la fonction pour les objets constants et non constants.

Vous ne pouvez pas déclarer de constructeurs ou de destructeurs avec le mot clé **const** .

## <a name="const-member-functions"></a>Fonctions membres const

La déclaration d’une fonction membre avec le mot clé **const** spécifie que la fonction est une fonction « en lecture seule » qui ne modifie pas l’objet pour lequel elle est appelée. Une fonction membre constante ne peut pas modifier les données membres non statiques, ni appeler les fonctions membres qui ne sont pas constantes. Pour déclarer une fonction membre constante, placez le mot clé **const** après la parenthèse fermante de la liste d’arguments. Le mot clé **const** est obligatoire dans la déclaration et la définition.

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

## <a name="c-and-c-const-differences"></a>Différences C C++ et const

Quand vous déclarez une variable comme **const** dans un fichier de code source C, vous procédez comme suit :

```cpp
const int i = 2;
```

Vous pouvez ensuite utiliser cette variable dans un autre module comme suit :

```cpp
extern const int i;
```

Mais pour avoir le même comportement dans C++, vous devez déclarer votre variable **const** comme suit :

```cpp
extern const int i = 2;
```

Si vous souhaitez déclarer une variable **externe** dans un C++ fichier de code source pour une utilisation dans un fichier de code source C, utilisez :

```cpp
extern "C" const int x=10;
```

pour empêcher que le compilateur C++ altère les noms.

## <a name="remarks"></a>Notes

Lorsque vous suivez la liste de paramètres d’une fonction membre, le mot clé **const** spécifie que la fonction ne modifie pas l’objet pour lequel elle est appelée.

Pour plus d’informations sur **const**, consultez les rubriques suivantes :

- [const et volatile, pointeurs](../cpp/const-and-volatile-pointers.md)

- [Qualificateurs de type (référence du langage C)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
