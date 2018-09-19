---
title: Test de caractère | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c558c5d32f75561d5722a656450d5f18f5166a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084937"
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