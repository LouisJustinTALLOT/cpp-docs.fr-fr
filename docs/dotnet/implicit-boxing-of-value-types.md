---
title: Conversion Boxing implicite de Types valeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387586"
---
# <a name="implicit-boxing-of-value-types"></a>Conversion boxing implicite de types valeur

Le boxing des types valeur a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Dans la conception du langage, nous imposées à une position théorique à la place d’une expérience pratique avec la fonctionnalité et, dans la pratique, il était une erreur. Par analogie, dans la version d’origine plusieurs conception du langage de l’héritage, Stroustrup a décidé qu’un sous-objet de classe de base virtuelle n’a pas pu être initialisé dans un constructeur de classe dérivée, et par conséquent le langage nécessitait que n’importe quelle classe servant de base virtuelle classe doit définir un constructeur par défaut. Il est à ce constructeur par défaut qui peuvent être appelé par dérivation virtuelle suivante.

Le problème d’une hiérarchie de classe de base virtuelle est que la responsabilité de l’initialisation du sous-objet virtuel partagé décale à chaque dérivation suivante. Par exemple, si je définis une classe de base pour lequel l’initialisation nécessite l’allocation d’une mémoire tampon, la taille spécifiée par l’utilisateur de cette mémoire tampon peut être passé en tant qu’argument au constructeur. Si je fournis ensuite deux dérivations virtuelles, les appeler `inputb` et `outputb`, chacune fournit une valeur particulière au constructeur de classe de base. Maintenant, lorsque je l’ai dérivée un `in_out` classe à partir des deux `inputb` et `outputb`, aucune de ces valeurs le sous-objet de classe de base virtuelle partagée ne peut raisonnablement être autorisée à évaluer.

Par conséquent, dans la conception du langage d’origine, Stroustrup refusait l’initialisation explicite d’une classe de base virtuelle dans la liste d’initialisation de membre du constructeur de classe dérivée. Bien que cela a résolu le problème, dans la pratique, l’incapacité de diriger l’initialisation de la classe de base virtuelle révélé impossible. Keith Gorlen de l’Institut National de la santé, qui avait implémenté une version gratuite de la bibliothèque de collection SmallTalk appelée nihcl, a été une voix principe convaincre Stroustrup qu’il devait afin de proposer une conception plus souple du langage.

Un principe de conception hiérarchique orientée objet stipule qu’une classe dérivée doit être concernent uniquement avec l’implémentation non privée de ses classes de base immédiates. Pour prendre en charge une conception d’initialisation souple pour l’héritage virtuel, Stroustrup a été contraint de violer ce principe. La classe la plus dérivée dans une hiérarchie assume la responsabilité de toute initialisation de sous-objet virtuel quel que soit la profondeur dans la hiérarchie, il se produit. Par exemple, `inputb` et `outputb` sont tous deux chargées d’initialiser explicitement leur classe de base virtuelle immédiate. Lorsque `in_out` dérive les deux `inputb` et `outputb`, `in_out` devient responsable de l’initialisation d’une fois effacé la classe de base virtuelle et l’initialisation rendues explicite dans `inputb` et `outputb` est supprimé.

Cela offre la souplesse nécessaire aux développeurs de langage, mais au prix d’une sémantique compliquée. Ce fardeau de complication est ignoré si nous limiter à une classe de base virtuelle pour être sans état et simplement lui permettre de spécifier une interface. Il s’agit d’un idiome de conception recommandé dans C++. Au sein de la programmation CLR, il est déclenché à la stratégie avec le type d’Interface.

Voici un exemple de code simple - et dans ce cas, la conversion boxing explicite est inutile :

```
// Managed Extensions for C++ requires explicit __box operation
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };
Object* myObjArray __gc[] = {
   __box(26), __box(27), __box(28), __box(29), __box(30)
};

Console::WriteLine( "{0}\t{1}\t{2}", __box(0),
   __box(my1DIntArray->GetLowerBound(0)),
   __box(my1DIntArray->GetUpperBound(0)) );
```

Comme vous pouvez le voir, il est beaucoup de boxing passe. Type de valeur sous Visual C++, le boxing est implicit :

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>Voir aussi

[Types valeur et leurs comportements (C++-CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Conversion boxing](../windows/boxing-cpp-component-extensions.md)