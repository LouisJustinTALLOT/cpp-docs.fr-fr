---
title: Utilisation d'opérateurs d'extraction
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 1fc6ffd2f033dfe3df60260f734d93b79d6824f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362424"
---
# <a name="using-extraction-operators"></a>Utilisation d'opérateurs d'extraction

L’opérateur d’extraction (`>>`), préprogrammé pour tous les types de données C++ standard, représente le moyen le plus simple pour obtenir des octets à partir d’un objet de flux d’entrée.

Les opérateurs d’extraction d’entrée de texte mis en forme dépendent de l’espace blanc pour séparer les valeurs des données entrantes. Cela n’est pas pratique lorsqu’un champ de texte contient plusieurs mots ou lorsque des virgules séparent les nombres. Dans ce cas, une solution consiste à utiliser la fonction membre d’entrée sans mise en forme [istream::getline](../standard-library/basic-istream-class.md#getline) pour lire un bloc de texte incluant des espaces blancs, puis analyser le bloc avec des fonctions spéciales. Une autre méthode consiste à dériver une classe de flux d’entrée avec une fonction membre telle que `GetNextToken`, qui peut appeler des membres istream pour extraire et mettre en forme les données caractères.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)<br/>
