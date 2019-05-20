---
title: Fonctions génériques (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516374"
---
# <a name="generic-functions-ccli"></a>Fonctions génériques (C++/CLI)

Une fonction générique est une fonction déclarée avec des paramètres de type. Lorsqu’elle est appelée, les types réels sont utilisés plutôt que les paramètres de type.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="remarks"></a>Remarques

Cette fonctionnalité ne s’applique pas à toutes les plateformes.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Remarques

Cette fonctionnalité n’est pas prise en charge dans Windows Runtime.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Une fonction générique est une fonction déclarée avec des paramètres de type. Lorsqu’elle est appelée, les types réels sont utilisés plutôt que les paramètres de type.

### <a name="syntax"></a>Syntaxe

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Paramètres

*Attributs*<br/>
(Facultatif) Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et les classes d’attributs, consultez Attributs.

*modifiers*<br/>
(Facultatif) Un modificateur de la fonction, tel que static.  **virtual** n’est pas autorisé dans la mesure où les méthodes virtuelles peuvent ne pas être génériques.

*return-type*<br/>
Type retourné par la méthode. Si le type de retour spécifié est vide, aucune valeur de retour n’est requise.

*identifier*<br/>
Nom de la fonction.

*type-parameter identifier(s)*<br/>
Liste d’identificateurs séparés par des virgules.

*formal-parameters*<br/>
(Facultatif) Liste de paramètres.

*type-parameter-constraints-clauses*<br/>
Spécifie les restrictions sur les types qui peuvent être utilisés comme arguments de type, et prend la forme spécifiée dans [Contraintes sur les paramètres de type générique (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

*function-body*<br/>
Le corps de la méthode, qui peut se référer aux identificateurs de paramètre de type.

### <a name="remarks"></a>Remarques

Les fonctions génériques sont des fonctions déclarées avec un paramètre de type générique. Il peut s’agir de méthodes dans une classe ou un struct, ou de fonctions autonomes. Une déclaration générique unique déclare implicitement une famille de fonctions qui diffèrent uniquement par la substitution d’un autre type réel au paramètre de type générique.

Une classe ou un constructeur de struct ne peut pas être déclaré(e) avec des paramètres de type générique.

Lorsqu’il est appelé, le paramètre de type générique est remplacé par un type réel. Le type réel peut être spécifié explicitement entre chevrons (< >) à l’aide d’une syntaxe semblable à celle d’un appel de fonction de modèle. Si la fonction est appelée sans les paramètres de type, le compilateur tente de déduire le type réel à partir des paramètres fournis dans l’appel de fonction. Si l’argument de type prévu ne peut pas être déduit des paramètres utilisés, le compilateur signale une erreur.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre comment créer une fonction générique.

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

Les fonctions génériques peuvent être surchargées en fonction de la signature ou de l’arité (le nombre de paramètres de type d’une fonction). En outre, les fonctions génériques peuvent être surchargées avec des fonctions non génériques du même nom, tant que les fonctions diffèrent pour certains paramètres de type. Par exemple, les fonctions suivantes peuvent être surchargées :

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

L’exemple suivant utilise une fonction générique pour rechercher le premier élément d’un tableau. Il déclare `MyClass`, qui hérite de la classe de base `MyBaseClass`. `MyClass` contient une fonction générique, `MyFunction`, qui appelle une autre fonction générique, `MyBaseClassFunction`, dans la classe de base. Dans `main`, la fonction générique, `MyFunction`, est appelée à l’aide de différents arguments de type.

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Génériques](generics-cpp-component-extensions.md)
