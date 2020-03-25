---
title: Génériques et modèles (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 567286ee24e9df968b2d352489fe12f2735854eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172345"
---
# <a name="generics-and-templates-ccli"></a>Génériques et modèles (C++/CLI)

Les génériques et les modèles sont des fonctionnalités linguistiques qui prennent en charge les types paramétrables. Cependant, ils sont différents et présentent des utilisations différentes. Cette rubrique offre une vue d’ensemble de ces différences.

Pour plus d’informations, consultez [Windows Runtime et modèles managés](windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Comparaison des modèles et des génériques

Différences principales entre les modèles C++ et les génériques :

- Les génériques sont génériques jusqu’à ce que des types leur soient substitués lors du runtime. Les modèles sont spécialisés au moment de la compilation, ils ne sont toujours pas des types paramétrables lors du runtime.

- Common language runtime prend spécifiquement en charge les génériques dans MSIL. Étant donné que le runtime connaît les génériques, des types spécifiques peuvent être substitués aux types génériques lors du référencement d’un assembly contenant un type générique. En revanche, les modèles se résolvent en types ordinaires au moment de la compilation et les types qui en résultent peuvent ne pas être spécialisés dans d’autres assemblys.

- Les génériques spécialisés dans deux assemblys différents avec les mêmes arguments de type sont du même type. Les modèles spécialisés dans deux assemblys différents avec les mêmes arguments de type sont considérés par le runtime comme types différents.

- Les génériques sont générés sous la forme d’un seul fragment de code exécutable qui est utilisé pour tous les arguments de type référence (cela n’est pas vrai pour les types valeur, qui sont implémentés une fois par type valeur). Le compilateur JIT connaît les génériques et est en mesure d’optimiser le code pour les types référence ou valeur qui sont utilisés comme arguments de type. Les modèles génèrent du code d’exécution distinct pour chaque spécialisation.

- Les génériques n’autorisent pas les paramètres de modèle sans type, tels que `template <int i> C {}`, contrairement aux modèles.

- Les génériques n’autorisent pas la spécialisation explicite (une implémentation personnalisée d’un modèle pour un type spécifique), contrairement aux modèles.

- Les génériques n’autorisent pas la spécialisation partielle (une implémentation personnalisée pour un sous-ensemble des arguments de type), contrairement aux modèles.

- Les génériques n’autorisent pas l’utilisation du paramètre de type comme classe de base pour le type générique, contrairement aux modèles.

- Les modèles prennent en charge les paramètres de modèle à modèle (par exemple, `template<template<class T> class X> class MyClass`), mais ce n’est pas le cas de génériques.

## <a name="combining-templates-and-generics"></a>Combinaison des modèles et des génériques

Les différences fondamentales entre modèles et génériques ont des conséquences en matière de création d’applications qui les combinent. Par exemple, supposons que vous avez une classe de modèle pour laquelle vous souhaitez créer un wrapper générique, afin d’exposer ce modèle comme générique dans d’autres langages. Le générique ne peut pas prendre un paramètre de type puis le transmettre ensuite au modèle, dans la mesure où le modèle a besoin d’avoir ce paramètre de type au moment de la compilation, mais le générique ne résout le paramètre de type qu’au moment de l’exécution. L’imbrication d’un modèle à l’intérieur d’un générique ne fonctionnera pas non plus, car il n’existe aucun moyen de développer les modèles au moment de la compilation pour les types génériques arbitraires qui pourraient être instanciés lors de l’exécution.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre un exemple simple d’utilisation conjointe des modèles et des génériques. Dans cet exemple, la classe de modèle transmet son paramètre au type générique. L’inverse est impossible.

Cet idiome peut être utilisé lorsque vous souhaitez réutiliser une API générique existante avec du code de modèle local à un assembly C++/CLI, ou lorsque vous devez ajouter une couche supplémentaire de paramétrage à un type générique, pour tirer parti de certaines fonctionnalités des modèles non prises en charge par les génériques.

### <a name="code"></a>Code

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>Voir aussi

[Génériques](generics-cpp-component-extensions.md)
