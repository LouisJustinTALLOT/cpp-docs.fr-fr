---
title: types de données SBCS et MBCS
description: Comment représenter des caractères uniques et multioctets dans le runtime C de Microsoft.
ms.topic: conceptual
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 27d32ffd079cdc82ab8a799df9d9ec778b546a3b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590249"
---
# <a name="sbcs-and-mbcs-data-types"></a>types de données SBCS et MBCS

Toute routine de bibliothèque Runtime Microsoft MBCS qui gère uniquement 1 caractère multioctet ou 1 octet d’un caractère multioctet attend un **`unsigned int`** argument (où 0x00 <= valeur de caractère <= 0xFFFF et 0x00 <= valeur d’octet <= 0xFF). Une routine MBCS qui gère des octets ou des caractères multioctets dans un contexte de chaîne s’attend à ce qu’une chaîne de caractères multioctets soit représentée comme un **`unsigned char`** pointeur.

> [!CAUTION]
> Chaque octet d’un caractère multioctet peut être représenté dans un 8 bits **`char`** . Toutefois, un caractère codé sur un octet SBCS ou MBCS de type **`char`** avec une valeur supérieure à 0x7F est négatif. Quand un tel caractère est converti directement en **`int`** ou a **`long`** , le résultat est étendu par le compilateur et peut donc produire des résultats inattendus.

Il est préférable de représenter un octet d’un caractère multioctet sous forme de 8 bits **`unsigned char`** . Ou, pour éviter un résultat négatif, convertissez un caractère codé sur un octet de type **`char`** en un caractère **`unsigned char`** avant de le convertir en **`int`** ou **`long`** .

Étant donné que certaines fonctions de gestion de chaînes SBCS acceptent les paramètres (signés) **`char`** <strong>\*</strong> , un avertissement du compilateur d’incompatibilité de type se produit lorsque **_MBCS** est défini. Il existe trois façons d’éviter cet avertissement, indiquées dans l’ordre de leur efficacité :

1. Utilisez les fonctions inline de type sécurisé dans TCHAR.H. Il s'agit du comportement par défaut.

1. Utilisez les macros directes dans TCHAR.H en définissant **_MB_MAP_DIRECT** sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. Il s’agit de la méthode la plus rapide, mais n’est pas de type sécurisé.

1. Utilisez les fonctions de bibliothèque liée statiquement de type sécurisé dans TCHAR.H. Pour cela, définissez la constante **_NO_INLINING** sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
