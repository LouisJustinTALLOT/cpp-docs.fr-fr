---
title: Résumé des règles de portée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ce7c57688fae22c3bba844cff480ae3aec03785
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028136"
---
# <a name="summary-of-scope-rules"></a>Résumé des règles de portée
L'utilisation d'un nom doit être non équivoque dans sa portée (jusqu'au point où la surcharge est déterminée). Si le nom indique une fonction, celle-ci doit être non équivoque en ce qui concerne le nombre et le type de paramètres. Si le nom n’est pas ambigu, [accès au membre](../cpp/member-access-control-cpp.md) les règles sont appliquées.  
  
## <a name="constructor-initializers"></a>Initialiseurs de constructeur  
 Initialiseurs de constructeur (décrit dans [initialisation des Bases et membres](http://msdn.microsoft.com/2f71377e-2b6b-49da-9a26-18e9b40226a1)) sont évalués dans la portée du bloc extérieur du constructeur pour lequel elles sont spécifiées. Par conséquent, ils peuvent utiliser les noms de paramètres du constructeur.  
  
## <a name="global-names"></a>Noms globaux  
 Un nom d'objet, de fonction ou d'énumérateur est global s'il est placé en dehors de toute fonction ou classe ou préfixé par l'opérateur de portée unaire globale (`::`), et s'il n'est pas utilisé conjointement avec l'un des opérateurs binaires suivants :  
  
-   Résolution de portée (`::`)  
  
-   Sélection de membres pour les objets et les références (**.**)  
  
-   Sélection de membres pour les pointeurs (**->**)  
  
## <a name="qualified-names"></a>Noms qualifiés  
 Les noms utilisés avec l'opérateur binaire de résolution de portée (`::`) sont appelés des noms qualifiés. Le nom spécifié après l’opérateur binaire de résolution de portée doit être membre de la classe spécifiée à gauche de l’opérateur ou membre d’une ou plusieurs de ses classes de base.  
  
 Les noms spécifiés après l’opérateur de sélection de membre (**.** ou **->**) doivent être membres du type de classe de l’objet spécifié à gauche de l’opérateur ou membres de ses classes de base. Les noms spécifiés sur la droite de l’opérateur de sélection de membre (**->**) peut également être des objets d’un autre type de classe, à condition que le côté gauche de **->** est un objet de classe et que la classe définit un opérateur de sélection de membre surchargé (**->**) qui prend la valeur en un pointeur vers un autre type de classe. (Cette disposition est décrite plus en détail dans [accès aux membres de classe](../cpp/member-access.md).)  
  
 Le compilateur recherche les noms dans l'ordre suivant et s'arrête après avoir trouvé le nom :  
  
1.  Portée de bloc active si le nom est utilisé dans une fonction. Sinon, portée globale.  
  
2.  Vers l'extérieur dans chaque portée de bloc englobante, notamment la portée de fonction externe (qui inclut des paramètres de fonction).  
  
3.  Si le nom est utilisé dans une fonction membre, il est recherché dans la portée de la classe.  
  
4.  Le nom est recherché dans les classes de base de la classe.  
  
5.  La recherche est effectuée dans la portée de classe imbriquée englobante (le cas échéant) et ses bases. La recherche se poursuit jusqu'à atteindre la portée de classe englobante externe.  
  
6.  La recherche est effectuée dans la portée globale.  
  
 Toutefois, vous pouvez apporter des modifications à cet ordre de recherche comme suit :  
  
1.  Les noms précédés de `::` forcent la recherche à commencer au niveau de la portée globale.  
  
2.  Les noms précédés du **classe**, **struct**, et **union** mots clés forcent le compilateur pour rechercher uniquement les **classe**,  **struct**, ou **union** noms.  
  
3.  Les noms sur le côté gauche de l’opérateur de résolution de portée (`::`) peut uniquement être **classe**, **struct**, **espace de noms**, ou **union**noms.  
  
 Si le nom fait référence à un membre non statique mais est utilisé dans une fonction membre statique, un message d'erreur est généré. De même, si le nom fait référence à un membre non statique d’une classe englobante, un message d’erreur est généré, car les classes englobées n’ont pas de classe englobante **cela** pointeurs.  
  
## <a name="function-parameter-names"></a>Noms de paramètres de fonction  
 Les noms de paramètres de fonction dans les définitions de fonction sont considérés comme étant dans la portée du bloc le plus à l'extérieur de la fonction. Par conséquent, il s'agit de noms régionaux. Ils se trouvent hors de portée lors de la sortie de la fonction.  
  
 Les noms de paramètres de fonction dans les déclarations de fonctions (prototypes) sont dans la portée locale de la déclaration et sortent de la portée à la fin de la déclaration.  
  
 Les paramètres par défaut sont dans la portée du paramètre pour lequel ils sont la valeur par défaut, comme décrit dans les deux paragraphes précédents. Toutefois, ils ne peuvent pas accéder à des variables locales ou à des membres de classes non statiques. Les paramètres par défaut sont évalués au point de l'appel de fonction, mais ils sont évalués dans la portée d'origine de la déclaration de fonction. Par conséquent, les paramètres par défaut pour les fonctions membres sont toujours évalués dans la portée de classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Héritage](../cpp/inheritance-cpp.md)