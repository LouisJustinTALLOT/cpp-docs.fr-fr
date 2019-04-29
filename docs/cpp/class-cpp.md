---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c4ef9690a41737147354ee0976f6912c4711ff67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331075"
---
# <a name="class-c"></a>class (C++)

Le **classe** mot clé déclare un type de classe ou définit un objet d’un type de classe.

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

*template-spec*<br/>
Spécifications de modèle facultatives. Pour plus d’informations, consultez [modèles](templates-cpp.md).

*class*<br/>
Le **classe** mot clé.

*ms-decl-spec*<br/>
Spécification de classe de stockage facultative. Pour plus d’informations, reportez-vous à la [__declspec](../cpp/declspec.md) mot clé.

*tag*<br/>
Le nom de type donné à la classe. L’étiquette devient un mot réservé dans l’étendue de la classe. La balise est facultative. Si omis, une classe anonyme est définie. Pour plus d’informations, consultez [des Types de classe anonymes](../cpp/anonymous-class-types.md).

*base-list*<br/>
Liste facultative des classes ou structures de que cette classe dérive ses membres à partir. Consultez [des Classes de Base](../cpp/base-classes.md) pour plus d’informations. Chaque nom de classe ou une structure de base peut être précédée d’un spécificateur d’accès ([public](../cpp/public-cpp.md), [privé](../cpp/private-cpp.md), [protégé](../cpp/protected-cpp.md)) et le [virtuels](../cpp/virtual-cpp.md) mot clé. Consultez le tableau de l’accès aux membres de [contrôle de l’accès aux membres de classe](member-access-control-cpp.md) pour plus d’informations.

*member-list*<br/>
Liste des membres de classe. Reportez-vous à [vue d’ensemble des membres de classe](../cpp/class-member-overview.md) pour plus d’informations.

*declarators*<br/>
Liste des déclarateurs spécifiant les noms d’une ou plusieurs instances du type classe. Déclarateurs peuvent inclure des listes d’initialiseurs si tous les membres de données de la classe sont **public**. Cela est plus courant dans les structures, dont les données membres sont **public** par défaut, que dans les classes. Consultez [vue d’ensemble des déclarateurs](../cpp/overview-of-declarators.md) pour plus d’informations.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les classes en général, consultez une des rubriques suivantes :

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Pour plus d’informations sur les classes managées et les structures en C / c++ / CLI et c++ / CX, consultez [Classes et Structs](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>Exemple

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
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