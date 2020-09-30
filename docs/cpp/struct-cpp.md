---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: d0092cf107159f4c84b431f5eeae130df64dc835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507456"
---
# <a name="struct-c"></a>struct (C++)

Le **`struct`** mot clé définit un type structure et/ou une variable d’un type structure.

## <a name="syntax"></a>Syntaxe

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Paramètres

*spécification de modèle*<br/>
Spécifications de modèle facultatives. Pour plus d’informations, consultez [spécifications du modèle](templates-cpp.md).

*modélis*<br/>
**`struct`** Mot clé.

*MS-decl-spec*<br/>
Spécification de classe de stockage facultative. Pour plus d’informations, reportez-vous au mot clé [__declspec](../cpp/declspec.md) .

*étiquette*<br/>
Nom de type donné à la structure. La balise devient un mot réservé dans la portée de la structure. La balise est facultative. Si elle est omise, une structure anonyme est définie. Pour plus d’informations, consultez [types de classes anonymes](../cpp/anonymous-class-types.md).

*base-list*<br/>
Liste facultative des classes ou structures dont dérivent les membres de cette structure. Pour plus d’informations, consultez [classes de base](../cpp/base-classes.md) . Chaque nom de classe de base ou de structure peut être précédé d’un spécificateur d’accès ([public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md)) et du mot clé [Virtual](../cpp/virtual-cpp.md) . Pour plus d’informations, consultez la table accès aux membres dans contrôle de l' [accès aux membres](member-access-control-cpp.md) de la classe.

*Member-List*<br/>
Liste des membres de structure. Pour plus d’informations, consultez [vue d’ensemble des membres de classe](../cpp/class-member-overview.md) . La seule différence ici est que **`struct`** est utilisé à la place de **`class`** .

*declarators*<br/>
Liste des déclarateurs spécifiant les noms de la structure. Les listes des déclarateurs déclarent une ou plusieurs instances du type structure. Les déclarateurs peuvent inclure des listes d’initialiseurs si toutes les données membres de la structure sont **`public`** . Les listes d’initialiseurs sont courantes dans les structures, car les membres de données sont **`public`** par défaut.  Pour plus d’informations, consultez [vue d’ensemble des déclarateurs](./declarations-and-definitions-cpp.md) .

## <a name="remarks"></a>Remarques

Un type structure est un type composite défini par l'utilisateur. Il comprend des champs ou des membres qui peuvent avoir différents types.

En C++, une structure est identique à une classe, sauf que ses membres sont **`public`** par défaut.

Pour plus d’informations sur les classes et les structs managés en C++/CLI, consultez [classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Utilisation d'une structure

En C, vous devez utiliser explicitement le **`struct`** mot clé pour déclarer une structure. En C++, vous n’avez pas besoin d’utiliser le **`struct`** mot clé une fois que le type a été défini.

Vous avez la possibilité de déclarer des variables lorsque le type de structure est défini en plaçant un ou plusieurs noms de variables séparés par des virgules entre l'accolade fermante et le point-virgule.

Les variables de structure peuvent être initialisées. L'initialisation de chaque variable doit être placée entre accolades.

Pour obtenir des informations connexes, consultez [Class](../cpp/class-cpp.md), [Union](../cpp/unions.md)et [enum](../cpp/enumerations-cpp.md).

## <a name="example"></a>Exemple

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
