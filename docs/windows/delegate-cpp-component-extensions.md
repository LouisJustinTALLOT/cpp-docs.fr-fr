---
title: délégué (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 7c58a5b239e91fd3e15f806049e4f71635aebb73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584121"
---
# <a name="delegate--ccli-and-ccx"></a>délégué (C++ / c++ / CLI et c++ / CX)

Déclare un type qui représente un pointeur de fonction.

## <a name="all-runtimes"></a>Tous les runtimes

Le Windows Runtime et le common language runtime prend en charge les délégués.

### <a name="remarks"></a>Notes

**délégué** est un mot clé contextuel. Pour plus d’informations, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).

Pour détecter au moment de la compilation si un type est un délégué, utilisez le `__is_delegate()` trait de type. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

C++ / c++ / CX prend en charge les délégués avec la syntaxe suivante.

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

*access*<br/>
(facultatif) L’accessibilité du délégué, qui peut être **public** (la valeur par défaut) ou **privé**. Le prototype de fonction peut également être qualifié avec le **const** ou **volatile** mots clés.

*type de retour*<br/>
Le type de retour du prototype de fonction.

*identificateur de type de délégué*<br/>
Le nom du type délégué déclaré.

*Paramètres*<br/>
(Facultatif) Les types et les identificateurs du prototype de fonction.

### <a name="remarks"></a>Notes

Utilisez le *identificateur de type de délégué* pour déclarer un événement avec le même prototype que le délégué. Pour plus d’informations, consultez [délégués (C++ / c++ / CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Configuration requise

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

*access*<br/>
(facultatif) L’accessibilité du délégué en dehors de l’assembly peut être public ou privé.  La valeur par défaut est privé.  À l’intérieur d’une classe, un délégué peut avoir n’importe quelle accessibilité.

*function_declaration*<br/>
La signature de la fonction qui peut être liée au délégué. Le type de retour d’un délégué peut être n’importe quel type managé. Pour des raisons de l’interopérabilité, il est recommandé que le type de retour d’un délégué d’être un type CLS.

Pour définir un délégué indépendant, le premier paramètre dans *function_declaration* doivent être du type de la **cela** pointeur pour l’objet.

### <a name="remarks"></a>Notes

Les délégués sont multicast : « pointeur de fonction » peut être lié à une ou plusieurs méthodes dans une classe managée. Le **déléguer** mot clé définit un type de délégué multicast avec une signature de méthode spécifique.

Un délégué peut également être lié à une méthode d’une classe value, tel qu’une méthode statique.

Un délégué a les caractéristiques suivantes :

- Il hérite de `System::MulticastDelegate`.

- Elle possède un constructeur qui accepte deux arguments : un pointeur vers une classe managée ou NULL (dans le cas de liaison à une méthode statique) et une méthode qualifiée complet du type spécifié.

- Elle possède une méthode appelée `Invoke`, dont la signature correspond à la signature déclarée du délégué.

Lorsqu’un délégué est appelé, son ou les fonctions sont appelées dans l’ordre qu’ils ont été attachés.

La valeur de retour d’un délégué est la valeur de retour à partir de sa dernière fonction membre attaché.

Les délégués ne peut pas être surchargés.

Les délégués peuvent être liés ou détachées.

Lorsque vous instanciez un délégué lié, le premier argument doit être une référence d’objet. Le deuxième argument d’une instanciation de délégué doit être l’adresse d’une méthode d’un objet de classe managée ou un pointeur à une méthode d’un type valeur. Le deuxième argument d’une instanciation de délégué doit nommer la méthode avec la syntaxe de portée de classe complet et appliquer l’opérateur address-of.

Lorsque vous instanciez un délégué indépendant, le premier argument doit être l’adresse d’une méthode d’un objet de classe managée ou un pointeur vers une méthode d’un type valeur. L’argument doit nommer la méthode avec la syntaxe de portée de classe complet et appliquer l’opérateur address-of.

Lorsque vous créez un délégué à une fonction statique ou globale, qu’un seul paramètre est obligatoire : la fonction (le cas échéant, l’adresse de la fonction).

Pour plus d’informations sur les délégués, consultez

- [Guide pratique pour définir et utiliser des délégués (C++-CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Délégués génériques (C++/CLI)](../windows/generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Configuration requise

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

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)