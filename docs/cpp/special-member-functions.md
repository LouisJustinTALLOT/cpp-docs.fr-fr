---
description: 'En savoir plus sur : fonctions membres spéciales'
title: Fonctions membres spéciales
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: ab3b5be3c7006729e135cc273e9b7856adbd3252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113829"
---
# <a name="special-member-functions"></a>Fonctions membres spéciales

Les *fonctions membres spéciales* sont des fonctions membres de classe (ou struct) qui, dans certains cas, sont générées automatiquement par le compilateur. Ces fonctions sont le [constructeur par défaut](constructors-cpp.md#default_constructors), le [destructeur](destructors-cpp.md), le [constructeur de copie et l’opérateur d’assignation de copie](copy-constructors-and-copy-assignment-operators-cpp.md), ainsi que le constructeur de [déplacement et l’opérateur d’assignation de déplacement](move-constructors-and-move-assignment-operators-cpp.md). Si votre classe ne définit pas une ou plusieurs des fonctions membres spéciales, le compilateur peut déclarer et définir implicitement les fonctions utilisées. Les implémentations générées par le compilateur sont appelées fonctions membres spéciales *par défaut* . Le compilateur ne génère pas de fonctions s’ils ne sont pas nécessaires.

Vous pouvez déclarer explicitement une fonction membre spéciale par défaut à l’aide du mot clé **= default** . En conséquence, le compilateur définit la fonction uniquement si nécessaire, de la même façon que si la fonction n’a pas été déclarée.

Dans certains cas, le compilateur peut générer des fonctions membres spéciales *supprimées* , qui ne sont pas définies et ne peuvent donc pas être appelées. Cela peut se produire dans les cas où un appel à une fonction membre spéciale particulière sur une classe n’a pas de sens, étant donné les autres propriétés de la classe. Pour empêcher explicitement la génération automatique d’une fonction membre spéciale, vous pouvez la déclarer comme supprimée à l’aide du mot clé **= Delete** .

Le compilateur génère un *constructeur par défaut*, un constructeur qui ne prend pas d’arguments, uniquement lorsque vous n’avez pas déclaré d’autre constructeur. Si vous avez déclaré uniquement un constructeur qui accepte des paramètres, le code qui tente d’appeler un constructeur par défaut provoque la génération d’un message d’erreur par le compilateur. Le constructeur par défaut généré par le compilateur effectue une [initialisation par défaut](initializers.md#default_initialization) simple au niveau du membre de l’objet. L’initialisation par défaut laisse toutes les variables membres dans un état indéterminé.

Le destructeur par défaut effectue une destruction au niveau des membres de l’objet. Elle est virtuelle uniquement si un destructeur de classe de base est virtuel.

La construction de copie et de déplacement par défaut et les opérations d’assignation effectuent des copies de modèle de bit au niveau des membres ou des déplacements de données membres non statiques. Les opérations de déplacement sont générées uniquement quand aucun destructeur, aucune opération de déplacement ou de copie n’est déclarée. Un constructeur de copie par défaut est généré uniquement quand aucun constructeur de copie n’est déclaré. Elle est implicitement supprimée si une opération de déplacement est déclarée. Un opérateur d’assignation de copie par défaut est généré uniquement quand aucun opérateur d’assignation de copie n’est déclaré explicitement. Elle est implicitement supprimée si une opération de déplacement est déclarée.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](cpp-language-reference.md)
