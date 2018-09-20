---
title: Substitution explicite d’un membre d’Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409023"
---
# <a name="explicit-override-of-an-interface-member"></a>Substitution explicite d'un membre d'interface

La syntaxe de déclaration d’une substitution explicite d’un membre d’interface dans une classe a changé entre les Extensions managées pour C++ vers Visual C++.

Vous souhaitez souvent fournir deux instances d’un membre d’interface dans une classe qui implémente l’interface - un est utilisé lorsque les objets de classe sont manipulés via un handle d’interface et celle qui est utilisée lorsque les objets de classe sont utilisés via l’interface de classe. Exemple :

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

Dans les Extensions managées nous cela en fournissant une déclaration explicite de la méthode d’interface avec le nom de méthode qualifié avec le nom de l’interface. L’instance de classe spécifique n’est pas qualifié. Cela vous évite de devoir effectuer un downcast la valeur de retour de `Clone`, dans cet exemple, lorsqu’elle est appelée explicite via une instance de `R`.

Dans la nouvelle syntaxe, un mécanisme général de substitution a été introduit qui remplace la syntaxe des Extensions managées. Notre exemple est réécrite comme suit :

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

Cette révision exige que le membre d’interface explicitement substitué soit donné un nom unique au sein de la classe. Ici, j’ai fourni le nom encombrant de `InterfaceClone`. Le comportement est toujours le même : un appel via la `ICloneable` interface appelle la renommée `InterfaceClone`, tandis qu’un appel via un objet de type `R` appelle la seconde `Clone` instance.

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[Substitutions explicites](../windows/explicit-overrides-cpp-component-extensions.md)