---
title: Séquences de caractères
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312685"
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
