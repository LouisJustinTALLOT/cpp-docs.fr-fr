---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 6475bc3703ce1bd7cf6103f4be8c12edc36e98b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226006"
---
# <a name="class-c"></a>class (C++)

Le **`class`** mot clé déclare un type de classe ou définit un objet d’un type de classe.

## <a name="syntax"></a>Syntaxe

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>Paramètres

*spécification de modèle*<br/>
Spécifications de modèle facultatives. Pour plus d’informations, consultez [modèles](templates-cpp.md).

*class*<br/>
**`class`** Mot clé.

*MS-decl-spec*<br/>
Spécification de classe de stockage facultative. Pour plus d’informations, reportez-vous au mot clé [__declspec](../cpp/declspec.md) .

*Référence*<br/>
Nom de type donné à la classe. La balise devient un mot réservé dans l’étendue de la classe. La balise est facultative. En cas d’omission, une classe anonyme est définie. Pour plus d’informations, consultez [types de classes anonymes](../cpp/anonymous-class-types.md).

*base-list*<br/>
Liste facultative des classes ou structures dont cette classe dérivera ses membres. Pour plus d’informations, consultez [classes de base](../cpp/base-classes.md) . Chaque nom de classe de base ou de structure peut être précédé d’un spécificateur d’accès ([public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md)) et du mot clé [Virtual](../cpp/virtual-cpp.md) . Pour plus d’informations, consultez la table accès aux membres dans contrôle de l' [accès aux membres](member-access-control-cpp.md) de la classe.

*Member-List*<br/>
Liste des membres de la classe. Pour plus d’informations, consultez [vue d’ensemble des membres de classe](../cpp/class-member-overview.md) .

*declarators*<br/>
Liste des déclarateurs spécifiant les noms d’une ou plusieurs instances du type de classe. Les déclarateurs peuvent inclure des listes d’initialiseurs si toutes les données membres de la classe sont **`public`** . Cela est plus courant dans les structures, dont les membres de données sont **`public`** par défaut, que dans les classes. Pour plus d’informations, consultez [vue d’ensemble des déclarateurs](../cpp/overview-of-declarators.md) .

## <a name="remarks"></a>Notes

Pour plus d’informations sur les classes en général, reportez-vous à l’une des rubriques suivantes :

- [modélis](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Pour plus d’informations sur les classes et les structures managées en C++/CLI et C++/CX, consultez [classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>Exemple

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Classes et structs](../cpp/classes-and-structs-cpp.md)
