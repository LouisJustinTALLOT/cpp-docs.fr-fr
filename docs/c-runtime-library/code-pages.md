---
title: Pages de codes
description: Description de la prise en charge des pages de codes dans le runtime C de Microsoft.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 1f9d311ec714d2043e072cbbfbac505d3f804294
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590067"
---
# <a name="code-pages"></a>Pages de codes

Une *page de codes* est un jeu de caractères, qui peut inclure des nombres, des signes de ponctuation et d’autres glyphes. Différents paramètres régionaux et langues peuvent utiliser différentes pages de codes. Par exemple, la page de codes ANSI 1252 est utilisée pour l'anglais et la plupart des langues européennes ; la page de codes OEM 932 est utilisée pour le kanji (japonais).

Une page de codes peut être représentée dans un tableau sous la forme d’un mappage de caractères à des valeurs codées sur un octet ou multioctets. De nombreuses pages de codes partagent le jeu de caractères ASCII pour les caractères compris dans la plage 0x00 à 0x7F.

La bibliothèque Microsoft Runtime utilise les types de pages de codes suivants :

- Page de codes ANSI par défaut du système : Par défaut, au démarrage, le système d’exécution définit automatiquement la page de codes multioctets sur la page de codes ANSI par défaut du système, qui est obtenue à partir du système d’exploitation. L'appel :

    ```C
    setlocale ( LC_ALL, "" );
    ```

   définit également les paramètres régionaux sur la page de codes ANSI par défaut du système.

- Page de codes des paramètres régionaux. Le comportement d'un certain nombre de routines d'exécution dépend des paramètres régionaux actuels, qui incluent la page de codes des paramètres régionaux. (Pour plus d’informations, consultez [routines dépendantes des paramètres régionaux](../c-runtime-library/locale.md).) Par défaut, toutes les routines dépendantes des paramètres régionaux de la bibliothèque Runtime Microsoft utilisent la page de codes qui correspond aux paramètres régionaux « C ». Au moment de l’exécution, vous pouvez modifier ou interroger la page de codes des paramètres régionaux en cours d’utilisation avec un appel à [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Page de codes multioctets. Le comportement de la plupart des routines de caractères multioctets dans la bibliothèque Runtime dépend de la page de codes multioctets actuelle. Par défaut, ces routines utilisent la page de codes ANSI par défaut du système. Au moment de l’exécution, vous pouvez interroger et modifier la page de codes multioctets avec [_getmbcp](../c-runtime-library/reference/getmbcp.md) et [_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivement.

- Les paramètres régionaux "C" sont définis par ANSI pour correspondre aux paramètres régionaux dans lesquels les programmes C sont traditionnellement exécutés. La page de codes pour les paramètres régionaux "C" (page de codes "C") correspond au jeu de caractères ASCII. Par exemple, dans les paramètres régionaux "C", **islower** retourne la valeur true pour les valeurs 0x61 à 0x7A uniquement. Dans d’autres paramètres régionaux, **IsLower** peut retourner `true` pour ces valeurs et d’autres, comme défini par les paramètres régionaux.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)\
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
