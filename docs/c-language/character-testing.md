---
title: Test de caractère
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740097"
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
