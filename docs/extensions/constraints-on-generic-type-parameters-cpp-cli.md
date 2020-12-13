---
description: 'En savoir plus sur : contraintes sur les paramètres de type générique (C++/CLI)'
title: Contraintes sur les paramètres de type générique (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: c9e340c229736cbe1c679b931e52f68b0971f8f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333745"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Contraintes sur les paramètres de type générique (C++/CLI)

Dans les déclarations de méthode ou de type générique, vous pouvez qualifier un paramètre de type avec des contraintes. Une contrainte est une exigence que les types utilisés comme arguments de type doivent respecter. Par exemple, une contrainte peut indiquer que l'argument de type doit implémenter une certaine interface ou hériter d'une classe spécifique.

Les contraintes sont facultatives ; ne pas spécifier de contrainte sur un paramètre revient à limiter ce paramètre à <xref:System.Object>.

## <a name="syntax"></a>Syntaxe

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Paramètres

*paramètre de type*<br/>
Un des paramètres de type, à limiter.

*constraint list*<br/>
La *liste de contraintes* est une liste séparée par des virgules répertoriant les spécifications de contrainte. La liste peut inclure des interfaces à implémenter par le paramètre de type.

La liste peut également inclure une classe. Pour que l'argument de type satisfasse une contrainte de classe de base, il doit être de la même classe que la contrainte ou dériver de la contrainte.

Vous pouvez également spécifier **gcnew()** pour indiquer que l’argument de type doit disposer d’un constructeur public sans paramètre ; ou **ref class** pour indiquer que l’argument de type doit être un type de référence, y compris tout type de classe, d’interface, de délégué ou de tableau ; ou **value class** pour indiquer que l’argument de type doit être un type de valeur. Tout type valeur, sauf Nullable, \<T> peut être spécifié.

Vous pouvez également spécifier un paramètre générique en tant que contrainte. L’argument de type disponible pour le type que vous contraignez doit être, ou dériver du, type de la contrainte. Il s'agit d'une contrainte de type naked.

## <a name="remarks"></a>Notes

La clause de contrainte se compose de **where** suivi d’un paramètre de type, de deux points (**:**) et de la contrainte, qui spécifie la nature de la restriction sur le paramètre de type. **where** est un mot clé contextuel ; consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md) pour plus d’informations. Séparez par un espace plusieurs clauses de **where**.

Les contraintes sont appliquées aux paramètres de type pour placer des restrictions sur les types qui peuvent être utilisés comme arguments pour un type générique ou une méthode générique.

La classe et les contraintes d’interface spécifient les types d’argument qui doivent être, ou hériter, d’une classe spécifiée ou implémentent une interface spécifiée.

L’application des contraintes sur un type ou une méthode générique permet au code de ce type ou de cette méthode de tirer parti des fonctionnalités connues des types de contraintes. Vous pouvez, par exemple, déclarer une classe générique, de telle sorte que le paramètre de type implémente l’interface `IComparable<T>` :

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

Cette contrainte exige qu’un argument de type utilisé pour `T` implémente `IComparable<T>` au moment de la compilation. Il permet également aux méthodes de l’interface, telles que `CompareTo`, d’être appelées. Aucune conversion n'est nécessaire sur une instance du paramètre de type pour appeler les méthodes d'interface.

Les méthodes statiques dans la classe de l'argument de type ne peuvent pas être appelées par le paramètre de type ; elles peuvent être appelées uniquement par le type réel désigné.

Une contrainte ne peut pas être un type valeur, y compris des types intégrés tels que **`int`** ou **`double`** . Puisque les types de valeur ne peuvent avoir de classes dérivées, seule une classe sera toujours en mesure de satisfaire la contrainte. Dans ce cas, le générique peut être réécrit avec le paramètre de type remplacé par le type de valeur spécifique.

Les contraintes sont requises dans certains cas puisque la compilation n'autorisera pas l'utilisation des méthodes ou autres fonctionnalités d'un type inconnu à moins que les contraintes n'impliquent que le type inconnu prenne en charge les méthodes ou les interfaces.

Plusieurs contraintes pour le même paramètre de type peuvent être spécifiés dans une liste séparée par des virgules

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

Avec plusieurs paramètres de type, utilisez une clause **where** pour chaque paramètre de type. Par exemple :

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

Pour résumer, utilisez les contraintes dans votre code en fonction des règles suivantes :

- Si plusieurs contraintes sont répertoriées, les contraintes peuvent être répertoriées dans un ordre quelconque.

- Les contraintes peuvent être également des types de classe, tels que les classes de base abstraites. Toutefois, les contraintes ne peuvent pas être des types de valeur, ni des classes sealed.

- Les contraintes ne peuvent pas être elles-mêmes des paramètres de type, mais elles peuvent impliquer des paramètres de type dans un type construit ouvert. Par exemple :

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="examples"></a>Exemples

L'exemple suivant illustre l'utilisation de contraintes pour appeler des méthodes d'instance sur des paramètres de type.

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

Lorsqu’un paramètre de type générique est utilisé comme contrainte, il est appelé une contrainte de type naked. Les contraintes de type naked sont utiles lorsqu’une fonction membre avec son propre paramètre de type doit limiter ce paramètre au paramètre de type contenant le type.

Dans l’exemple suivant, `T` est une contrainte de type naked dans le contexte de la méthode `Add`.

Les contraintes de type naked peuvent être également utilisées dans des définitions de classe générique. L'utilité des contraintes de type naked avec les classes génériques est très limitée, car la compilation ne peut rien deviner à propos des contraintes de types naked en dehors du fait qu'elles dérivent de <xref:System.Object>. Utilisez des contraintes de type naked sur les classes génériques dans des scénarios dans lesquels vous souhaitez mettre en application une relation d’héritage entre deux paramètres de type.

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>Voir aussi

[Génériques](generics-cpp-component-extensions.md)
