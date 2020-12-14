---
description: En savoir plus sur les macros de nom de fichier
title: Macros de noms de fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 2b10d021d27eedf008a143472715ee8e0cbecde5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200570"
---
# <a name="filename-macros"></a>Macros de noms de fichiers

Les macros de nom de fichier sont prédéfinies en tant que noms de fichiers spécifiés dans la dépendance (pas les spécifications de noms de fichiers complets sur le disque). Ces macros n’ont pas besoin d’être placées entre parenthèses lorsqu’elles sont appelées ; spécifiez uniquement un $ comme indiqué.

|Macro|Signification|
|-----------|-------------|
|**$\@**|Nom complet de la cible actuelle (chemin d’accès, nom de base, extension), comme spécifié actuellement.|
|**$$\@**|Nom complet de la cible actuelle (chemin d’accès, nom de base, extension), comme spécifié actuellement. Valide uniquement comme dépendant dans une dépendance.|
|**$&#42;**|Chemin d’accès et nom de base de la cible actuelle moins l’extension de fichier.|
|**$&#42;&#42;**|Tous les dépendants de la cible actuelle.|
|**$?**|Tous les dépendants avec un horodateur ultérieur à la cible actuelle.|
|**$<**|Fichier dépendant avec un horodateur ultérieur à la cible actuelle. Valide uniquement dans les commandes dans les règles d’inférence.|

Pour spécifier une partie d’une macro de nom de fichier prédéfinie, ajoutez un modificateur de macro et mettez la macro modifiée entre parenthèses.

|Modificateur|Partie du nom de fichier résultant|
|--------------|-----------------------------|
|**D**|Lecteur plus répertoire|
|**B**|Nom de base|
|**F**|Nom de base plus extension|
|**R**|Lecteur plus répertoire plus nom de base|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
