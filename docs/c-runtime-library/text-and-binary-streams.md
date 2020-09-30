---
title: Flux texte et binaires
description: Description des flux texte et binaires dans la bibliothèque Runtime C de Microsoft.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 522e4d5f119e4415694b59b2b08141a45f06fe5a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589612"
---
# <a name="text-and-binary-streams"></a>Flux texte et binaires

Un flux de texte se compose d'une ou de plusieurs lignes de texte qui peuvent être écrites sur un affichage orienté texte afin qu'elles puissent être lues. Lors de la lecture d'un flux de texte, le programme lit `NL` (saut de ligne) à la fin de chaque ligne. Lors de l'écriture dans un flux de texte, le programme écrit `NL` pour signaler la fin d'une ligne. Pour faire correspondre différentes conventions dans les environnements cibles pour représenter le texte contenu dans les fichiers, les fonctions de la bibliothèque peuvent modifier le nombre et les représentations des caractères transmis entre le programme et un flux de texte.

Le positionnement dans un flux de texte est limité. Vous pouvez obtenir l'indicateur de position de fichier actuel en appelant [fgetpos](../c-runtime-library/reference/fgetpos.md) ou [ftell](../c-runtime-library/reference/ftell-ftelli64.md). Vous pouvez positionner un flux de texte à un emplacement obtenu de cette façon, ou au début ou à la fin du flux, en appelant [fsetpos](../c-runtime-library/reference/fsetpos.md) ou [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Tout autre changement de position risque de ne pas être pris en charge.

Pour une portabilité maximale, le programme ne doit pas écrire :

- Fichiers vides.
- Espaces à la fin d'une ligne.
- Lignes partielles (en omettant `NL` à la fin d'un fichier).
- Caractères autres que les caractères imprimables, NL et `HT` (tabulation horizontale).

Si vous suivez ces règles, la séquence de caractères que vous lisez à partir d'un flux de texte (en tant que caractères octets ou multioctets) correspond à la séquence de caractères que vous avez écrits dans le flux de texte lors de la création du fichier. Sinon, les fonctions de la bibliothèque peuvent supprimer un fichier créé s'il est vide lorsque vous le fermez. Elles peuvent également modifier ou supprimer les caractères que vous écrivez dans le fichier.

Un flux binaire se compose d'un ou de plusieurs octets d'informations aléatoires. Vous pouvez écrire la valeur stockée dans un objet aléatoire dans un flux binaire (orienté octet) et lire exactement le contenu stocké dans l'objet lors de son écriture. Les fonctions de la bibliothèque ne modifient pas les octets transmis entre le programme et un flux binaire. Toutefois, ils peuvent ajouter un nombre arbitraire d' `NULL` octets au fichier que vous écrivez avec un flux binaire. Le programme doit traiter ces octets supplémentaires `NULL` à la fin du flux binaire.

Le positionnement dans un flux binaire est bien défini, à l’exception du positionnement par rapport à la fin du flux. Vous pouvez obtenir et modifier l'indicateur de position de fichier actuel de la même manière que pour un flux de texte. Les offsets utilisés par [ftell](../c-runtime-library/reference/ftell-ftelli64.md) et [fseek](../c-runtime-library/reference/fseek-fseeki64.md) Count octets à partir du début du flux (qui est l’octet zéro), de sorte que l’arithmétique d’entiers sur ces décalages génère des résultats prévisibles.

Un flux d'octets traite un fichier comme une séquence d'octets. Dans le programme, le flux ressemble à la même séquence d'octets, à l'exception des modifications possibles décrites ci-dessus.

## <a name="see-also"></a>Voir aussi

[Fichiers et flux](../c-runtime-library/files-and-streams.md)
