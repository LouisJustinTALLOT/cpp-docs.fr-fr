---
title: Performances des bibliothèques multithread
description: Vue d’ensemble de la façon d’optimiser les performances à partir des bibliothèques multithread du runtime C de Microsoft.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
ms.openlocfilehash: edfbbf3055e9023c74cf0e154577d4b1853f557b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590197"
---
# <a name="multithreaded-libraries-performance"></a>Performances des bibliothèques multithread

La bibliothèque CRT monothread n’est plus disponible. Cette rubrique explique comment extraire des performances maximales des bibliothèques multithreads.

## <a name="maximizing-performance"></a>Optimisation des performances

Les performances des bibliothèques multithread ont été améliorées et sont proches de celles des bibliothèques monothread, maintenant indisponibles. Pour les situations nécessitant des performances plus élevées, il existe plusieurs nouvelles fonctionnalités.

- Le verrouillage de flux indépendant vous permet de verrouiller un flux de données, puis d’utiliser les [fonctions _nolock](../c-runtime-library/nolock-functions.md) qui accèdent directement au flux. Cela permet à l’utilisation du verrou de se trouver en dehors des boucles critiques.

- Les paramètres régionaux par thread réduisent le coût de l’accès aux paramètres régionaux pour les scénarios multithreads (consultez [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Les fonctions dépendantes des paramètres régionaux (avec des noms se terminant par _l) acceptent les paramètres régionaux en tant que paramètre, réduisant de manière significative le coût (par exemple, [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Des optimisations pour les pages de code commun réduisent le coût de nombreuses opérations courtes.

- Définir [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) force toutes les opérations d’E/S à supposer un modèle d’E/S monothread et à utiliser les formes _nolock des fonctions. Cela permet aux applications monothreads à E/S élevées d’obtenir de meilleures performances.

- L’exposition du handle de tas CRT vous permet d’activer le segment de mémoire du tas LFH Windows pour le tas CRT, ce qui peut améliorer considérablement les performances dans les scénarios très évolutifs.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
