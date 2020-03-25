---
title: Résumé des règles de portée
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: 1f8b79c637662d79051b72e6aabefc99c450bdc5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160877"
---
# <a name="summary-of-scope-rules"></a>Résumé des règles de portée

L'utilisation d'un nom doit être non équivoque dans sa portée (jusqu'au point où la surcharge est déterminée). Si le nom indique une fonction, celle-ci doit être non équivoque en ce qui concerne le nombre et le type de paramètres. Si le nom n’est pas ambigu, les règles d' [accès aux membres](../cpp/member-access-control-cpp.md) sont appliquées.

## <a name="constructor-initializers"></a>Initialiseurs de constructeur

Les [initialiseurs de constructeur](constructors-cpp.md#member_init_list) sont évalués dans la portée du bloc le plus à l’extérieur du constructeur pour lequel ils sont spécifiés. Par conséquent, ils peuvent utiliser les noms de paramètres du constructeur.

## <a name="global-names"></a>Noms globaux

Un nom d'objet, de fonction ou d'énumérateur est global s'il est placé en dehors de toute fonction ou classe ou préfixé par l'opérateur de portée unaire globale (`::`), et s'il n'est pas utilisé conjointement avec l'un des opérateurs binaires suivants :

- Résolution de portée (`::`)

- Sélection de membres pour les objets et les références ( **.** )

- Sélection de membres pour les pointeurs ( **->** )

## <a name="qualified-names"></a>Noms qualifiés

Les noms utilisés avec l'opérateur binaire de résolution de portée (`::`) sont appelés des noms qualifiés. Le nom spécifié après l'opérateur binaire de résolution de portée doit être membre de la classe spécifiée à gauche de l'opérateur ou membre d'une ou plusieurs de ses classes de base.

Noms spécifiés après l’opérateur de sélection de membres ( **.** ou **->** ) doit être membre du type de classe de l’objet spécifié à gauche de l’opérateur ou des membres de ses classes de base. Les noms spécifiés à droite de l’opérateur de sélection de membres ( **->** ) peuvent également être des objets d’un autre type de classe, à condition que la partie gauche de **->** soit un objet de classe et que la classe définisse un opérateur de sélection de membres surchargé ( **->** ) qui prend la valeur d’un pointeur vers un autre type de classe. (Cette configuration est décrite plus en détail dans [accès aux membres de classe](../cpp/member-access.md).)

Le compilateur recherche les noms dans l'ordre suivant et s'arrête après avoir trouvé le nom :

1. Portée de bloc active si le nom est utilisé dans une fonction. Sinon, portée globale.

1. Vers l’extérieur dans chaque portée de bloc englobante, notamment la portée de fonction externe (qui inclut des paramètres de fonction).

1. Si le nom est utilisé dans une fonction membre, il est recherché dans la portée de la classe.

1. Le nom est recherché dans les classes de base de la classe.

1. La recherche est effectuée dans la portée de classe imbriquée englobante (le cas échéant) et ses bases. La recherche se poursuit jusqu'à atteindre la portée de classe englobante externe.

1. La recherche est effectuée dans la portée globale.

Toutefois, vous pouvez apporter des modifications à cet ordre de recherche comme suit :

1. Les noms précédés de `::` forcent la recherche à commencer au niveau de la portée globale.

1. Les noms précédés par les mots clés **Class**, **struct**et **Union** forcent le compilateur à rechercher uniquement les noms de **classes**, de **structures**ou d' **unions** .

1. Les noms sur le côté gauche de l’opérateur de résolution de portée (`::`) peuvent être uniquement des noms de **classe**, de **struct**, d' **espace de noms**ou d' **Union** .

Si le nom fait référence à un membre non statique mais est utilisé dans une fonction membre statique, un message d'erreur est généré. De même, si le nom fait référence à un membre non statique dans une classe englobante, un message d’erreur est généré, car les classes incluses n’ont pas **de classe** englobante.

## <a name="function-parameter-names"></a>Noms de paramètres de fonction

Les noms de paramètres de fonction dans les définitions de fonction sont considérés comme étant dans la portée du bloc le plus à l'extérieur de la fonction. Par conséquent, il s'agit de noms régionaux. Ils se trouvent hors de portée lors de la sortie de la fonction.

Les noms de paramètres de fonction dans les déclarations de fonctions (prototypes) sont dans la portée locale de la déclaration et sortent de la portée à la fin de la déclaration.

Les paramètres par défaut sont dans la portée du paramètre pour lequel ils sont la valeur par défaut, comme décrit dans les deux paragraphes précédents. Toutefois, ils ne peuvent pas accéder à des variables locales ou à des membres de classes non statiques. Les paramètres par défaut sont évalués au point de l'appel de fonction, mais ils sont évalués dans la portée d'origine de la déclaration de fonction. Par conséquent, les paramètres par défaut pour les fonctions membres sont toujours évalués dans la portée de classe.

## <a name="see-also"></a>Voir aussi

[Héritage](../cpp/inheritance-cpp.md)
