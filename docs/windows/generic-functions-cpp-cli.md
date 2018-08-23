---
title: Fonctions génériques (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 700c88fa71e82e35602efef768fc5753760a5e1a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593478"
---
# <a name="generic-functions-ccli"></a>Fonctions génériques (C++/CLI)

Une fonction générique est une fonction qui est déclarée avec des paramètres de type. Lorsqu’elle est appelée, les types réels sont utilisés plutôt que les paramètres de type.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="remarks"></a>Notes

Cette fonctionnalité ne s’applique pas à toutes les plateformes.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Cette fonctionnalité n’est pas pris en charge dans le Runtime de Windows.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Une fonction générique est une fonction qui est déclarée avec des paramètres de type. Lorsqu’elle est appelée, les types réels sont utilisés plutôt que les paramètres de type.

### <a name="syntax"></a>Syntaxe

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])  
{function-body}
```

### <a name="parameters"></a>Paramètres

*attributs* (facultatif)  
Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et classes d’attributs, consultez attributs.

*modificateurs* (facultatif)  
Un modificateur de la fonction, comme statique.  **virtuel** n’est pas autorisé dans la mesure où les méthodes virtuelles ne peuvent pas être génériques.

*type de retour*  
Type retourné par la méthode. Si le type de retour est void, aucune valeur de retour n’est requis.

*identifier*  
Nom de la fonction.

*paramètre de type identificateur (s)*  
Liste d’identificateurs séparés par des virgules.

*paramètres-formels* (facultatif)  
Liste de paramètres.

*type de paramètre contraintes clauses*  
Cela indique les restrictions sur les types qui peuvent être utilisés comme arguments de type et prend la forme spécifiée dans [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).

*corps de la fonction*  
Le corps de la méthode, qui peut faire référence aux identificateurs de paramètre de type.

### <a name="remarks"></a>Notes

Fonctions génériques sont des fonctions déclarées avec un paramètre de type générique. Ils peuvent être des méthodes dans une classe ou un struct ou autonome des fonctions. Une déclaration générique unique déclare implicitement une famille de fonctions qui diffèrent uniquement par la substitution d’un autre type réel pour le paramètre de type générique.

Dans Visual C++, les constructeurs de classe ou un struct ne peuvent pas être déclarés avec des paramètres de type générique.

Lorsqu’elle est appelée, le paramètre de type générique est remplacé par un type réel. Le type réel peut être spécifié explicitement dans les crochets angulaires à l’aide d’une syntaxe semblable à un appel de fonction de modèle. Si elle est appelée sans les paramètres de type, le compilateur tente de déduire le type réel à partir des paramètres fournis dans l’appel de fonction. Si l’argument de type prévu ne peut pas être déduit à partir des paramètres utilisés, le compilateur signale une erreur.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre une fonction générique.

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

Fonctions génériques peuvent être surchargées en fonction de la signature ou arité, le nombre de paramètres de type sur une fonction. En outre, les fonctions génériques peuvent être surchargées avec des fonctions non génériques du même nom, tant que les fonctions diffèrent dans certains paramètres de type. Par exemple, les fonctions suivantes peuvent être surchargées :

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

L’exemple suivant utilise une fonction générique pour rechercher le premier élément dans un tableau. Elle déclare `MyClass`, qui hérite de la classe de base `MyBaseClass`. `MyClass` contient une fonction générique, `MyFunction`, qui appelle une autre fonction générique, `MyBaseClassFunction`, au sein de la classe de base. Dans `main`, la fonction générique, `MyFunction`, est appelée à l’aide des arguments de type différents.

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

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)  
[Génériques](../windows/generics-cpp-component-extensions.md)