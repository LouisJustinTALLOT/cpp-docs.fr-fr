---
title: Conversion Boxing implicite de Types valeur | Documents Microsoft
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
ms.openlocfilehash: f1f5a455333e5cb40b63d5a5237b2df053cef194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132217"
---
# <a name="implicit-boxing-of-value-types"></a>Conversion boxing implicite de types valeur
La conversion boxing de types valeur a été modifiée à partir des Extensions managées pour C++ vers Visual C++.  
  
 Dans la conception du langage, nous imposée à une position philosophique à la place d’une expérience pratique avec la fonctionnalité et, dans la pratique, il a une erreur. Par analogie, dans la version d’origine plusieurs conception du langage d’héritage, Stroustrup a décidé qu’un sous-objet de classe de base virtuelle n’a pas pu être initialisé dans un constructeur de classe dérivée, et par conséquent, la langue requises que n’importe quelle classe servant de base virtuelle classe doit définir un constructeur par défaut. Il est de ce constructeur par défaut qui peuvent être appelé par dérivation virtuelle suivante.  
  
 Le problème d’une hiérarchie de classe de base virtuelle est que le responsable de l’initialisation du sous-objet virtuel partagé se déplace à chaque dérivation suivante. Par exemple, si une classe de base pour définir dont l’initialisation requiert l’allocation d’une mémoire tampon, la taille spécifiée par l’utilisateur de cette mémoire tampon peut être passé en tant qu’argument au constructeur. Si ensuite fournir deux dérivations virtuelles, les appeler `inputb` et `outputb`, chacune fournit une valeur particulière au constructeur de classe de base. Maintenant, lorsque je dérivée un `in_out` classe à partir des deux `inputb` et `outputb`, aucune de ces valeurs le sous-objet de classe de base virtuelle partagée ne peut raisonnablement être autorisée à évaluer.  
  
 Par conséquent, dans la conception d’origine du langage, Stroustrup interdit l’initialisation explicite d’une classe de base virtuelle dans la liste des membres de l’initialisation du constructeur de classe dérivée. Bien que cela résolve le problème, dans la pratique, l’incapacité de diriger l’initialisation de la classe de base virtuelle révélé impossible. Keith Gorlen, de l’Institut National de la santé, qui avait implémenté une version gratuite de la bibliothèque de collection SmallTalk appelée nihcl, a une voix principe convaincre Stroustrup qu’il devait avec une conception plus souple du langage.  
  
 Un principe de conception hiérarchique orientée objet stipule qu’une classe dérivée doit être concernent uniquement avec l’implémentation non privée de ses classes de base immédiates. Pour prendre en charge une conception d’initialisation souple pour l’héritage virtuel, Stroustrup a été contraint de violer ce principe. La classe la plus dérivée dans une hiérarchie assume la responsabilité pour une initialisation tous les sous-objets virtuels quelle que soit la profondeur dans la hiérarchie, il se produit. Par exemple, `inputb` et `outputb` sont toutes deux chargées d’initialiser explicitement leur classe de base virtuelle immédiate. Lorsque `in_out` dérive les deux `inputb` et `outputb`, `in_out` devient responsable de l’initialisation d’une fois supprimé de classe de base virtuelle, et l’initialisation rendue explicite dans `inputb` et `outputb` est supprimé.  
  
 Cela offre la souplesse nécessaire aux développeurs de langage, mais au prix d’une sémantique compliquée. Cette charge de la complication est ignorée si nous limiter à une classe de base virtuelle pour être sans état et simplement lui permettre de spécifier une interface. Il s’agit d’un idiome de conception recommandé dans C++. Dans la programmation CLR, il est déclenché à la stratégie avec le type d’Interface.  
  
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
  
 Comme vous pouvez le voir, il existe un grand nombre de boxing sur. Type de valeur sous Visual C++, la conversion boxing est implicite :  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types valeur et leurs comportements (C + c++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Conversion boxing](../windows/boxing-cpp-component-extensions.md)