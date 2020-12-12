---
description: 'En savoir plus sur : test de caractères'
title: Test de caractère
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b7d73bce671787622814e11d8f3add7a1092572a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190534"
---
# <a name="character-testing"></a>Test de caractère

**ANSI 4.3.1** Jeux de caractères testés par les `isalnum` fonctions, `isalpha` , `iscntrl` , `islower` , `isprint` et `isupper`

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

[Fonctions de la bibliothèque](../c-language/library-functions.md)
