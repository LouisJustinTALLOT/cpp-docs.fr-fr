---
title: Fonctions membres spéciales | Microsoft Docs
ms.custom: ''
ms.date: 12/06/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdc9ed6f4cae208a7edae412debe0a07870ea06e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112081"
---
# <a name="special-member-functions"></a>Fonctions membres spéciales

Le *fonctions membres spéciales* classe (ou struct) est des fonctions membres que, dans certains cas, le compilateur génère automatiquement pour vous. Ces fonctions sont le [constructeur par défaut](constructors-cpp.md#default_constructors), le [destructeur](destructors-cpp.md), le [constructeur de copie et l’opérateur d’assignation de copie](copy-constructors-and-copy-assignment-operators-cpp.md)et le [constructeur de déplacement et opérateur d’assignation de déplacement](move-constructors-and-move-assignment-operators-cpp.md). Si votre classe ne définit pas une ou plusieurs des fonctions membres spéciales, puis le compilateur peut implicitement déclarer et définir les fonctions qui sont utilisées. Les implémentations générées par le compilateur sont appelées les *par défaut* fonctions membres spéciales. Le compilateur ne génère pas de fonctions si elles ne sont pas nécessaires.

Vous pouvez déclarer explicitement une fonction membre spéciale de valeur par défaut à l’aide de la **= valeur par défaut** mot clé. Ainsi, le compilateur définir la fonction uniquement si nécessaire, de la même façon, comme si la fonction n’a pas été déclarée du tout.

Dans certains cas, le compilateur peut générer *supprimé* fonctions membres spéciales, ce qui ne sont pas définis et par conséquent pas être appelée. Cela peut se produire dans les cas où un appel à une fonction membre spéciale particulier sur une classe n’est pas judicieux, étant donné les autres propriétés de la classe. Pour empêcher explicitement la génération automatique d’une fonction membre spéciale, vous pouvez la déclarer comme étant supprimé à l’aide de la **= suppression** mot clé.

Le compilateur génère un *constructeur par défaut*, un constructeur qui n’accepte aucun argument, uniquement lorsque vous avez déclaré pas de tout autre constructeur. Si vous avez déclaré qu’un constructeur qui accepte des paramètres, le code qui tente d’appeler un constructeur par défaut, le compilateur produire un message d’erreur. Le constructeur par défaut de généré par le compilateur effectue simple member-wise [par défaut de l’initialisation](initializers.md#default_initialization) de l’objet. Initialisation par défaut laisse toutes les variables membres dans un état indéterminé.

Le destructeur par défaut effectue une destruction membre à membre de l’objet. Il est virtuel uniquement si un destructeur de classe de base est virtuel.

La copie par défaut et construction de déplacement et les opérations d’assignation de membre à membre de modèle de bit effectuent copie ou déplace des membres de données non statiques. Déplacer les opérations sont générées uniquement lorsqu’aucun destructeur ou les opérations de déplacement ou de copie ne sont déclarées. Un constructeur de copie par défaut est généré uniquement lorsqu’aucun constructeur de copie n’est déclaré. Il est implicitement supprimé si une opération de déplacement est déclarée. Un opérateur d’assignation de copie par défaut est généré uniquement lorsque aucun opérateur d’assignation de copie n’est déclaré explicitement. Il est implicitement supprimé si une opération de déplacement est déclarée.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](cpp-language-reference.md)