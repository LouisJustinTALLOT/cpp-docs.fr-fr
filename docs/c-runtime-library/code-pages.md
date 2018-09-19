---
title: Pages de codes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a81b358a89f3ed16747d27bc6401c01ad194680
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113719"
---
# <a name="code-pages"></a>Pages de codes

Une *page de codes* est un jeu de caractères, qui peut inclure des nombres, des signes de ponctuation et d’autres glyphes. Différents paramètres régionaux et langues peuvent utiliser différentes pages de codes. Par exemple, la page de codes ANSI 1252 est utilisée pour l'anglais et la plupart des langues européennes ; la page de codes OEM 932 est utilisée pour le kanji (japonais).

Une page de codes peut être représentée dans un tableau sous la forme d'un mappage de caractères en valeurs codées sur un octet ou en valeurs multioctets. De nombreuses pages de codes partagent le jeu de caractères ASCII pour les caractères compris dans la plage 0x00 à 0x7F.

La bibliothèque Runtime Microsoft utilise les types suivants de pages de codes :

- Page de codes ANSI par défaut du système : Par défaut, au démarrage, le système d'exécution définit automatiquement la page de codes multioctets sur la page de codes ANSI par défaut du système, qui est obtenue à partir du système d'exploitation. L'appel :

    ```C
    setlocale ( LC_ALL, "" );
    ```

     définit également les paramètres régionaux sur la page de codes ANSI par défaut du système.

- Page de codes des paramètres régionaux. Le comportement d'un certain nombre de routines d'exécution dépend des paramètres régionaux actuels, qui incluent la page de codes des paramètres régionaux. Pour plus d’informations, consultez [Routines dépendantes des paramètres régionaux](../c-runtime-library/locale.md). Par défaut, toutes les routines dépendantes des paramètres régionaux de la bibliothèque Runtime Microsoft utilisent la page de codes correspondant aux paramètres régionaux "C". Au moment de l’exécution, vous pouvez modifier ou interroger la page de codes des paramètres régionaux utilisée avec un appel à [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Page de codes multioctets. Le comportement de la plupart des routines de caractères multioctets dans la bibliothèque Runtime dépend de la page de codes multioctets actuelle. Par défaut, ces routines utilisent la page de codes ANSI par défaut du système. Au moment de l’exécution, vous pouvez interroger et modifier la page de codes multioctets avec [_getmbcp](../c-runtime-library/reference/getmbcp.md) et [_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivement.

- Les paramètres régionaux "C" sont définis par ANSI pour correspondre aux paramètres régionaux dans lesquels les programmes C sont traditionnellement exécutés. La page de codes pour les paramètres régionaux "C" (page de codes "C") correspond au jeu de caractères ASCII. Par exemple, dans les paramètres régionaux "C", **islower** retourne la valeur true pour les valeurs 0x61 à 0x7A uniquement. Avec d’autres paramètres régionaux, **islower** peut retourner la valeur true pour ces valeurs,ainsi que d’autres valeurs, telles que définies par ces paramètres régionaux.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>