---
title: Définition d'un flux
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
ms.openlocfilehash: 9b8821861baed53880a00695204a4555994dccb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410809"
---
# <a name="what-a-stream-is"></a>Définition d'un flux

Comme C, C++ n’a pas de capacité intégrée d’entrée/sortie. Tous les compilateurs C++, toutefois, sont fournis avec un package systématique et orienté objet d’E/S, appelé classes iostream. Le flux est le concept central de ces classes iostream. Vous pouvez considérer un objet de flux comme un fichier intelligent qui agit comme une source et une destination pour les octets. Les caractéristiques d’un flux sont déterminées par sa classe et par des opérateurs d’insertion et d’extraction personnalisés.

Au moyen de pilotes de périphérique, le système d’exploitation MS-DOS traite le clavier, l’écran, l’imprimante et les ports de communication en tant que fichiers étendus. Les classes iostream interagissent avec ces fichiers étendus. Les classes intégrées prennent en charge la lecture et l’écriture dans la mémoire avec une syntaxe identique à celle des E/S de disque, ce qui facilite la dérivation des classes de flux.

## <a name="in-this-section"></a>Dans cette section

[Alternatives d’entrée/sortie](../standard-library/input-output-alternatives.md)

## <a name="see-also"></a>Voir aussi

[iostream, programmation](../standard-library/iostream-programming.md)<br/>
