---
description: 'En savoir plus sur : vue d’ensemble des génériques en C++/CLI'
title: Vue d’ensemble des génériques dans C++/CLI
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 4b84d16f7d76824f732865e3bf8b7bbfe674a1bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274149"
---
# <a name="overview-of-generics-in-ccli"></a>Vue d’ensemble des génériques dans C++/CLI

Les génériques sont des types paramétrables pris en charge par le Common Language Runtime. Un type paramétrable est un type est défini avec un paramètre de type inconnu qui est spécifié lorsque le générique est utilisé.

## <a name="why-generics"></a>Pourquoi génériques ?

C++ prend en charge les modèles, et les modèles comme les génériques prennent en charge les types paramétrables pour créer des classes de collections typées. Toutefois, les modèles fournissent le paramétrage au moment de la compilation. Vous ne pouvez pas référencer un assembly qui contient une définition de modèle et créer des spécialisations du modèle. Une fois compilé, un modèle spécialisé ressemble à n'importe quelle classe ou méthode. En revanche, les génériques sont émis dans le langage MSIL en tant que type paramétré connu par le runtime pour être un type paramétré ; le code source qui référence un assembly contenant un type générique peut créer des spécialisations de type générique. Pour plus d’informations sur la comparaison des modèles et génériques Visual C++ standard, consultez [Génériques et modèles (C++/CLI)](generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Fonctions et types génériques

Les types de classe, à condition qu'ils soient des types managés, peuvent être génériques. Par exemple, une classe `List`. Le type d'un objet de la liste serait le paramètre de type. Si vous avez besoin d’une classe `List` pour différents types d’objets, avant les génériques, vous devez peut-être utiliser `List` qui prend `System::Object` comme type d’élément. Mais cela autoriserait l'utilisation de tout objet (y compris les objets du mauvais type) dans la liste. Une telle liste serait appelée une classe de collection non typée. Au mieux, vous pouvez vérifier le type au moment de l'exécution et lever une exception. Ou, vous pouvez utiliser un modèle, qui perdrait sa qualité générique une fois compilé dans un assembly. Les consommateurs de votre assembly ne peuvent pas créer leurs propres spécialisations du modèle. Les génériques vous permettent de créer des classes de collection typées, supposons `List<int>` (lecture en tant que « liste int ») et `List<double>` (« Liste de double ») qui génèrent une erreur au moment de la compilation si vous avez essayé de mettre un type dans la collection typée pour lequel la collection n’a pas été conçue. En outre, ces types restent génériques une fois qu'ils sont compilés.

Vous trouverez une description de la syntaxe des classes génériques dans [Classes génériques (C++/CLI)](generic-classes-cpp-cli.md). Un nouvel espace de noms, <xref:System.Collections.Generic>, introduit un ensemble de types de collections paramétrés, dont <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.LinkedList%601>.

Les fonctions membres de classes statiques et d'instance, les délégués, et les fonctions globales peuvent également être génériques. Les fonctions génériques peuvent être nécessaires si les paramètres de la fonction sont de type inconnu, ou si la fonction elle-même doit utiliser les types génériques. Dans de nombreux cas où `System::Object` a peut-être été utilisé dans le passé comme paramètre pour un type d’objet inconnu, un paramètre de type générique peut être utilisé à la place, autorisant un code de type plus sécurisé. Toute tentative de transmission d'un type pour lequel la fonction n'a pas été conçue est marquée comme une erreur au moment de la compilation. En utilisant `System::Object` comme paramètre de fonction, le passage discret d’un objet pour lequel la fonction n’a pas été pas conçue ne serait pas détecté. Vous devriez alors convertir le type d’objet inconnu en un type spécifique dans le corps de la fonction et envisager la possibilité d’une InvalidCastException. Avec un code générique, la tentative de transmission d'un objet à la fonction provoquerait un conflit de type de façon à garantir le type correct du corps de la fonction.

Les mêmes avantages s'appliquent aux classes de collection basées sur les génériques. Les classes de collection dans le passé emploieraient `System::Object` pour stocker les éléments dans une collection. L’insertion des objets d’un type pour lequel la collection n’a pas été conçue n’était pas indiquée au moment de la compilation, ni même lorsque les objets furent insérés. Généralement, un objet serait converti en un autre type lors de son accès dans la collection. Ce ne serait qu'en cas d'échec que le type inattendu serait détecté. Les génériques résolvent ce problème au moment de la compilation en détectant tout code insérant un type qui ne correspond pas (ou se convertit implicitement en) au type de paramètre de la collection générique.

Pour obtenir une description de la syntaxe, consultez [Fonctions génériques (C++/CLI)](generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminologie utilisée avec les génériques

### <a name="type-parameters"></a>Paramètres de type

Une déclaration générique contient un ou plusieurs types inconnus, tels que les *paramètres de type*. Les paramètres de type ont un nom qui représente le type dans le corps de la déclaration générique. Le type de paramètre est utilisé comme type dans le corps de la déclaration générique. La déclaration générique pour `List<T>` contient le paramètre de type T.

### <a name="type-arguments"></a>Arguments de type

L’*argument de type* est le type actuel utilisé à la place du paramètre de type lorsque le générique est spécialisé pour un type voire des types spécifiques. Par exemple, **`int`** est l’argument de type dans `List<int>` . Les types de valeur et les types de handle sont les seuls types autorisés en tant qu’argument de type générique.

### <a name="constructed-type"></a>Type construit

Un type construit à partir d’un type générique s’appelle un *type construit*. Un type pas entièrement précisé, par exemple `List<T>`, est un *type construit ouvert* ; un type entièrement précisé, par exemple `List<double>,`, est un *type construit fermé* ou *type spécial*. Les types construits ouverts peuvent être utilisés dans la définition d'autres types ou méthodes génériques et ne peuvent pas être entièrement spécifiés jusqu'à ce que le générique joint soit lui-même spécifié. Voici un exemple d'utilisation d'un type construit ouvert comme classe de base pour un générique :

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Contrainte

Une contrainte est une restriction sur les types qui peuvent être utilisés comme paramètre de type. Par exemple, une classe générique donnée pourrait accepter uniquement les classes qui héritent d'une classe spécifiée, ou pourrait implémenter une interface spécifiée. Pour plus d’informations, consultez [Contraintes sur les paramètres de type générique (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Types de référence et types de valeur

Les types de handle et les types de valeur peuvent être utilisés comme des arguments de type. Dans la définition générique, dans laquelle chaque type peut être utilisé, la syntaxe est celle des types de référence. Par exemple, l’opérateur `->` est utilisé pour accéder aux membres du type du paramètre de type, peu importe si le type est éventuellement utilisé ou pas comme type de référence ou type de valeur. Lorsqu'un type de valeur est utilisé comme argument type, le runtime génère du code qui utilise les types de valeur directement sans avoir à évaluer les types de valeur.

Lorsque vous utilisez un type de référence comme argument de type générique, utilisez la syntaxe du handle. Lorsque vous utilisez un type de valeur comme argument de type générique, utilisez directement le nom du type.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>Paramètres de type

Les paramètres de type dans une classe générique sont traités comme les autres identificateurs. Cela dit, parce que le type est inconnu, il y a des limites quant à leur utilisation. Par exemple, vous ne pouvez pas utiliser de membres, ni de méthodes de classe du paramètre de type à moins que le paramètre de type ne soit connu pour prendre en charge ces membres. Autrement dit, pour accéder à un membre via le paramètre de type, vous devez ajouter le type contenant le membre à la liste de contraintes du paramètre de type.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

Ces restrictions s'appliquent aux opérateurs également. Un paramètre de type générique sans contrainte ne peut pas utiliser les opérateurs `==` et `!=` pour comparer deux instances du paramètre de type, au cas où le type ne prendrait pas en charge ces opérateurs. Ces contrôles sont nécessaires pour les génériques, mais pas pour les modèles, car les génériques peuvent être spécialisés pendant l'exécution avec n'importe quelle classe satisfaisant aux contraintes, lorsqu'il est trop tard pour vérifier l'utilisation de membres non valides.

Une instance par défaut du paramètre de type peut être créée à l'aide de l'opérateur `()`. Par exemple :

`T t = T();`

où `T` est un paramètre de type dans une classe générique ou une définition de méthode générique, initialise la variable à sa valeur par défaut. Si `T` est une classe ref, il s'agit d'un pointeur null ; si `T` est une classe de valeur, l'objet est initialisé sur zéro. C’est ce qu’on appelle un *initialiseur par défaut*.

## <a name="see-also"></a>Voir aussi

[Génériques](generics-cpp-component-extensions.md)
