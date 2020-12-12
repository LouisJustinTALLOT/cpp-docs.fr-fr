---
description: 'En savoir plus sur : séquences de caractères'
title: Séquences de caractères
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: ac5642371389047bd8ce3a83e02dc13802167dc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305076"
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
