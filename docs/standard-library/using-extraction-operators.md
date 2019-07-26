---
title: Utilisation d'opérateurs d'extraction
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 7950984973f8df236905128ce4b5336ecb874b7f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458036"
---
# <a name="using-extraction-operators"></a>Utilisation d'opérateurs d'extraction

L’opérateur d’extraction (`>>`), préprogrammé pour tous les types de données C++ standard, représente le moyen le plus simple pour obtenir des octets à partir d’un objet de flux d’entrée.

Les opérateurs d’extraction d’entrée de texte mis en forme dépendent de l’espace blanc pour séparer les valeurs des données entrantes. Cela n’est pas pratique lorsqu’un champ de texte contient plusieurs mots ou lorsque des virgules séparent les nombres. Dans ce cas, une solution consiste à utiliser la fonction membre d’entrée sans mise en forme [istream::getline](../standard-library/basic-istream-class.md#getline) pour lire un bloc de texte incluant des espaces blancs, puis analyser le bloc avec des fonctions spéciales. Une autre méthode consiste à dériver une classe de flux d’entrée avec une fonction membre telle que `GetNextToken`, qui peut appeler des membres istream pour extraire et mettre en forme les données caractères.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
