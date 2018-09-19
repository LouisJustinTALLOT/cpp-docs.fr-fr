---
title: Séquences de caractères | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cf3b52b8a4e76062d06b0b9ca3d4535b79595c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061511"
---
# <a name="character-sequences"></a>Séquences de caractères

**ANSI 3.8.2** Mappage des séquences de caractères de fichier source

Les instructions de préprocesseur utilisent le même jeu de caractères que les instructions de fichier source, sauf que les séquences d'échappement ne sont pas prises en charge.

Ainsi, pour spécifier le chemin d'accès d'un fichier Include, utilisez une seule barre oblique inverse :

```
#include "path1\path2\myfile"
```

Dans le code source, deux barres obliques inverses sont nécessaires :

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>Voir aussi

[Directives de prétraitement](../c-language/preprocessing-directives.md)