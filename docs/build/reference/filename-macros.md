---
title: Macros de noms de fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 54527c6f06bee396fdc7419647c607f8979c6a38
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825567"
---
# <a name="filename-macros"></a>Macros de noms de fichiers

Macros de nom de fichier sont prédéfinies en tant que noms de fichiers spécifiés dans la dépendance (spécifications de nom de fichier complet pas sur le disque). Ces macros n’êtes pas obligé d’être mis entre parenthèses lorsqu’elle est appelée ; Spécifiez uniquement un $ comme indiqué.

|Macro|Signification|
|-----------|-------------|
|**$\@**|Nom complet la cible en cours (chemin d’accès, nom de base, extension), tel qu’il est spécifié.|
|**$$\@**|Nom complet la cible en cours (chemin d’accès, nom de base, extension), tel qu’il est spécifié. Valide uniquement en tant que dépendant dans une dépendance.|
|**$&#42;**|Nom chemin d’accès et de la base de la cible en cours moins l’extension de fichier.|
|**$&#42;&#42;**|Tous les dépendants de la cible actuelle.|
|**$?**|Tous les dépendants avec une horodatage la plus récente que la cible actuelle.|
|**$<**|Fichier dépendant avec un horodatage la plus récente que la cible actuelle. Valide uniquement dans les commandes dans les règles d’inférence.|

Pour spécifier une partie d’une macro de nom de fichier prédéfinie, ajoutez un modificateur de macro et placez la macro modifiée entre parenthèses.

|Modificateur|Partie de nom de fichier résultant|
|--------------|-----------------------------|
|**D**|Lecteur plus répertoire|
|**B**|Nom de base|
|**F**|Nom de base assorti de l’extension|
|**R**|Lecteur plus répertoire plus nom de base|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
