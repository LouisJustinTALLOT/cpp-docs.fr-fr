---
title: Incrémentation et décrémentation de pointeurs
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: 1899e3153300bbfbfce068d29351de601f336b6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567087"
---
# <a name="incrementing-and-decrementing-pointers"></a>Incrémentation et décrémentation de pointeurs

Utilisez les conseils suivants :

- Pointer vers les octets de tête, pas les octets de Queue. Il est généralement déconseillé d’avoir un pointeur vers un octet de fin. Il est plus sûr d’analyser une chaîne vers l’avant, plutôt que dans l’ordre inverse.

- Il existe des fonctions incrémenter/décrémenter des pointeurs et des macros disponibles pour déplacement d’un caractère entier :

    ```cpp
    sz1++;
    ```

   devient :

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   Le `_mbsinc` et `_mbsdec` fonctions correctement incrémenter et décrémenter dans `character` unités, quelles que soient la taille des caractères.

- Pour décréments, vous avez besoin d’un pointeur vers le début de la chaîne, comme dans l’exemple suivant :

    ```cpp
    sz2--;
    ```

   devient :

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   Vous pouvez également votre pointeur d’en-tête peut être un caractère valide dans la chaîne, telles que :

    ```cpp
    sz2Head < sz2
    ```

   Vous devez disposer d’un pointeur vers un octet de tête valide connu.

- Vous pouvez souhaiter conserver un pointeur vers le caractère précédent pour des appels plus rapides à `_mbsdec`.

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Indices d’octets](../text/byte-indices.md)