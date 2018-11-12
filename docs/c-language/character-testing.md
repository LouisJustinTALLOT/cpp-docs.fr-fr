---
title: Test de caractère
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: 31a90f28d710ffc1b58f9c6b3fcfd01fd8d2d00c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523199"
---
# <a name="character-testing"></a>Test de caractère

**ANSI 4.3.1** Les jeux de caractères testés par les fonctions `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint` et `isupper`

La liste suivante décrit ces fonctions telles qu'elles sont implémentées par le compilateur Microsoft C.

|Fonction|Tests des|
|--------------|---------------|
|`isalnum`|Caractères 0 à 9, A-Z, a-z ASCII 48-57, 65-90, 97-122|
|`isalpha`|Caractères A-Z, a-z ASCII 65-90, 97-122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|Caractères a-z ASCII 97-122|
|`isprint`|Caractères A-Z, a-z, 0-9, ponctuation, espace ASCII 32-126|
|`isupper`|Caractères A-Z ASCII 65-90|

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)