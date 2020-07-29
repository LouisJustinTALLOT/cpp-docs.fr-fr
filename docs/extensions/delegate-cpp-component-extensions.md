---
title: délégué (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 77cd17eb8c164a08af9ec783f8aba422785609b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219727"
---
# <a name="delegate--ccli-and-ccx"></a>délégué (C++/CLI et C++/CX)

Déclare un type qui représente un pointeur de fonction.

## <a name="all-runtimes"></a>Tous les runtimes

Le Windows Runtime et le Common Language Runtime prennent en charge les délégués.

### <a name="remarks"></a>Notes

**delegate** est un mot clé contextuel. Pour plus d’informations, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

Vous pouvez détecter, au moment de la compilation, si un type est délégué, avec le trait de type `__is_delegate()`. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

C++/CX prend en charge les délégués avec la syntaxe suivante.

### <a name="syntax"></a>Syntaxe

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>Paramètres

*accéder*<br/>
facultatif Accessibilité du délégué, qui peut être **`public`** (valeur par défaut) ou **`private`** . Le prototype de fonction peut également être qualifié avec **`const`** les **`volatile`** Mots clés ou.

*type de retour*<br/>
Le type de retour du prototype de fonction.

*delegate-type-identifier*<br/>
Le nom du type de délégué déclaré.

*parameters*<br/>
(Facultatif) Les types et identificateurs du prototype de fonction.

### <a name="remarks"></a>Notes

Utilisez *delegate-type-identifier* pour déclarer un événement avec le même prototype que le délégué. Pour plus d’informations, consultez [Délégués (C++/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Le common language runtime prend en charge les délégués avec la syntaxe suivante.

### <a name="syntax"></a>Syntaxe

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Paramètres

*accéder*<br/>
(facultatif) L’accessibilité du délégué hors de l’assembly, qui peut être public ou private.  La valeur par défaut est private.  À l’intérieur d’une classe, un délégué peut disposer de n’importe quelle accessibilité.

*function_declaration*<br/>
La signature de la fonction pouvant être liée au délégué. Le type de retour d’un délégué peut être n’importe quel type managé. Pour des raisons d’interopérabilité, il est recommandé que le type de retour d’un délégué soit un type CLS.

Pour définir un délégué indépendant, le premier paramètre de *function_declaration* doit être le type du **`this`** pointeur pour l’objet.

### <a name="remarks"></a>Notes

Les délégués sont multidiffusion : le « pointeur de fonction » peut être lié à une ou plusieurs méthodes dans une classe managée. Le mot clé **delegate** définit un type de délégué multidiffusion avec une signature de méthode spécifique.

Un délégué peut également être lié à une méthode d’une classe value, par exemple une méthode static.

Ce délégué présente les caractéristiques suivantes :

- Hérite de `System::MulticastDelegate`.

- Il possède un constructeur qui accepte deux arguments : un pointeur vers une classe managée ou NULL (dans le cas d’une liaison à une méthode statique) et une méthode complète du type spécifié.

- Elle possède une méthode appelée `Invoke`, dont la signature correspond à la signature déclarée du délégué.

Lorsqu’un délégué est appelé, sa ou ses fonctions sont appelées dans l’ordre dans lequel elles ont été attachées.

La valeur de retour d’un délégué est la valeur de retour de sa dernière fonction membre attachée.

Les délégués ne peuvent pas être surchargés.

Les délégués peuvent être dépendants ou indépendants.

Lorsque vous instanciez un délégué dépendant, le premier argument doit être une référence d’objet. Le deuxième argument d’une instanciation de délégué doit être l’adresse d’une méthode d’un objet de classe managée ou un pointeur vers une méthode de type valeur. Le deuxième argument d’une instanciation de délégué doit nommer la méthode avec la syntaxe de portée de classe complète et appliquer l’opérateur address-of.

Lorsque vous instanciez un délégué indépendant, le premier argument doit être l’adresse d’une méthode d’un objet de classe managée ou un pointeur vers une méthode de type valeur. L’argument doit nommer la méthode avec la syntaxe de portée de classe complète et appliquer l’opérateur address-of.

Lorsque vous créez un délégué pour une fonction static ou global, un seul paramètre est obligatoire : la fonction (en option, l’adresse de la fonction).

Pour plus d’informations sur les délégués, consultez

- [Comment : définir et utiliser des délégués (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Délégués génériques (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant montre comment déclarer, initialiser et appeler des délégués.

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
