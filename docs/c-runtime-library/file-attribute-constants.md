---
description: En savoir plus sur les constantes d’attribut de fichier
title: Constantes d'attributs de fichier
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 8b57549b4a21cc5d699f933009c575b3f3fca81d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306363"
---
# <a name="file-attribute-constants"></a>Constantes d'attributs de fichier

## <a name="syntax"></a>Syntaxe

```
#include <io.h>
```

## <a name="remarks"></a>Notes

Ces constantes spécifient les attributs actuels du fichier ou du répertoire spécifié par la fonction.

Les attributs sont représentés par les constantes manifestes suivantes :

|Constante|Description|
|-|-|
|`_A_ARCH`| Archive. Défini chaque fois que le fichier est modifié et supprimé par la commande BACKUP. Valeur : 0x20|
|`_A_HIDDEN`| Fichier caché. Normalement non utilisé avec la commande DIR, sauf si l’option /AH est utilisée. Retourne des informations sur les fichiers normaux, ainsi que les fichiers avec cet attribut. Valeur : 0x02|
|`_A_NORMAL`| Normal. Le fichier peut être lu et écrit sans restriction. Valeur : 0x00|
|`_A_RDONLY`| Lecture seule. Impossible d’ouvrir le fichier pour des opérations d’écriture ou de créer un fichier portant le même nom. Valeur : 0x01|
|`_A_SUBDIR`| Sous-répertoire. Valeur : 0x10|
|`_A_SYSTEM`| Fichier système. Normalement non utilisé avec la commande DIR, sauf si l’option /AS est utilisée. Valeur : 0x04|

Plusieurs constantes peuvent être combinées avec l’opérateur OR (&#124;).

## <a name="see-also"></a>Voir aussi

[Fonctions de recherche de nom de fichier](../c-runtime-library/filename-search-functions.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
