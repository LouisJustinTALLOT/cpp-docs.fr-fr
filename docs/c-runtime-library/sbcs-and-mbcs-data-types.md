---
title: Types de données SBCS et MBCS | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccdec81251589ba36209f878f1fa8b727d7d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409275"
---
# <a name="sbcs-and-mbcs-data-types"></a>Types de données SBCS et MBCS

Toute routine de bibliothèque Runtime Microsoft MBCS qui gère un seul caractère multioctet ou un seul octet de caractère multioctet attend un argument `unsigned int` (où 0x00 <= valeur du caractère <= 0xFFFF et 0x00 <= valeur de l’octet <= 0xFF). Une routine MBCS qui gère des octets ou des caractères multioctets dans un contexte de chaîne attend une chaîne de caractères multioctets représentée en tant que pointeur `unsigned char`.

> [!CAUTION]
> Chaque octet d’un caractère multioctet peut être représenté dans un **char** 8 bits. Toutefois, un caractère codé sur un octet SBCS ou MBCS de type **char** avec une valeur supérieure à 0x7F est négatif. Quand un tel caractère est converti directement en **int** ou **long**, le compilateur génère un résultat de type signe étendu, ce qui peut donc donner des résultats inattendus.

Ainsi, il est préférable de représenter un octet d’un caractère multi-octet sous forme de `unsigned char` 8 bits. Sinon, pour éviter un résultat négatif, il suffit de convertir un caractère codé sur un octet de type **char** en `unsigned char` avant de le convertir en **int** ou en **long**.

Étant donné que certaines fonctions de gestion des chaînes SBCS acceptent des paramètres **char\*** (signés), un avertissement du compilateur d’incompatibilité de type est généré quand **_MBCS** est défini. Il existe trois façons d’éviter cet avertissement, indiquées dans l’ordre de leur efficacité :

1. Utilisez les fonctions inline de type sécurisé dans TCHAR.H. Il s'agit du comportement par défaut.

1. Utilisez les macros directes dans TCHAR.H en définissant **_MB_MAP_DIRECT** sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. Cette méthode est la plus rapide mais n’est pas de type sécurisé.

1. Utilisez les fonctions de bibliothèque liée statiquement de type sécurisé dans TCHAR.H. Pour cela, définissez la constante **_NO_INLINING** sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
