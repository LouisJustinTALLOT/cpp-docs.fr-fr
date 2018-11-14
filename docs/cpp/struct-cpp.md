---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: 9b70a4caea2b9aa5d86c0e97b97eae784594ec87
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326106"
---
# <a name="struct-c"></a>struct (C++)

Le **struct** mot clé définit un type structure et/ou une variable d’un type structure.

## <a name="syntax"></a>Syntaxe

```
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Paramètres

*spécifications de modèle*<br/>
Spécifications de modèle facultatives. Pour plus d’informations, consultez [spécifications de modèle](templates-cpp.md).

*struct*<br/>
Le **struct** mot clé.

*MS-decl-spec*<br/>
Spécification de classe de stockage facultative. Pour plus d’informations, reportez-vous à la [__declspec](../cpp/declspec.md) mot clé.

*Balise*<br/>
Nom de type donné à la structure. L’étiquette devient un mot réservé dans la portée de la structure. L’étiquette est facultative. Si elle est omise, une structure anonyme est définie. Pour plus d’informations, consultez [des Types de classe anonymes](../cpp/anonymous-class-types.md).

*liste de base*<br/>
Liste facultative des classes ou structures dont dérivent les membres de cette structure. Consultez [des Classes de Base](../cpp/base-classes.md) pour plus d’informations. Chaque nom de classe ou une structure de base peut être précédée d’un spécificateur d’accès ([public](../cpp/public-cpp.md), [privé](../cpp/private-cpp.md), [protégé](../cpp/protected-cpp.md)) et le [virtuels](../cpp/virtual-cpp.md) mot clé. Consultez le tableau de l’accès aux membres de [contrôle de l’accès aux membres de classe](member-access-control-cpp.md) pour plus d’informations.

*liste des membres*<br/>
Liste des membres de structure. Reportez-vous à [vue d’ensemble des membres de classe](../cpp/class-member-overview.md) pour plus d’informations. La seule différence ici est que **struct** est utilisé à la place de **classe**.

*déclarateurs*<br/>
Liste des déclarateurs spécifiant les noms de la classe. Les listes des déclarateurs déclarent une ou plusieurs instances du type structure. Déclarateurs peuvent inclure des listes d’initialiseurs si tous les membres de données de la classe sont **public**. Listes d’initialiseurs sont fréquentes dans les structures, car les données membres sont **public** par défaut.  Consultez [vue d’ensemble des déclarateurs](../cpp/overview-of-declarators.md) pour plus d’informations.

## <a name="remarks"></a>Notes

Un type structure est un type composite défini par l'utilisateur. Il comprend des champs ou des membres qui peuvent avoir différents types.

En C++, une structure est identique à une classe sauf que ses membres sont **public** par défaut.

Pour plus d’informations sur les classes et structures managées, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Utilisation d'une structure

En C, vous devez utiliser explicitement le **struct** mot clé pour déclarer une structure. En C++, vous n’avez pas besoin d’utiliser le **struct** mot clé une fois que le type a été défini.

Vous avez la possibilité de déclarer des variables lorsque le type de structure est défini en plaçant un ou plusieurs noms de variables séparés par des virgules entre l'accolade fermante et le point-virgule.

Les variables de structure peuvent être initialisées. L'initialisation de chaque variable doit être placée entre accolades.

Pour plus d’informations, consultez [classe](../cpp/class-cpp.md), [union](../cpp/unions.md), et [enum](../cpp/enumerations-cpp.md).

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