---
description: 'En savoir plus sur : incrémentation et décrémentation de pointeurs'
title: Incrémentation et décrémentation de pointeurs
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: 3c333c11c5a0b68bf013dbd374eb1cc4e5f00abc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207317"
---
# <a name="incrementing-and-decrementing-pointers"></a>Incrémentation et décrémentation de pointeurs

Utilisez les conseils suivants :

- Pointez sur octets de tête, et non sur octets de fin. Il est généralement risqué d’avoir un pointeur vers un octet de fin. Il est généralement plus sûr d’analyser une chaîne vers l’avant plutôt que vers l’arrière.

- Des fonctions et des macros d’incrémentation/décrémentation de pointeur sont disponibles qui se déplacent sur un caractère entier :

    ```cpp
    sz1++;
    ```

   devient :

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   Les `_mbsinc` `_mbsdec` fonctions et incrémentent et décrémentent correctement les `character` unités, quelle que soit la taille des caractères.

- Pour les décrémentations, vous avez besoin d’un pointeur vers le début de la chaîne, comme dans l’exemple suivant :

    ```cpp
    sz2--;
    ```

   devient :

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   En guise d’alternative, votre pointeur d’en-tête peut être un caractère valide dans la chaîne, de sorte que :

    ```cpp
    sz2Head < sz2
    ```

   Vous devez avoir un pointeur vers un octet de tête valide connu.

- Vous pouvez conserver un pointeur vers le caractère précédent pour des appels plus rapides à `_mbsdec` .

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Indices d’octets](../text/byte-indices.md)
