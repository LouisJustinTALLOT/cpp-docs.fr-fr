---
title: Avertissement du compilateur (niveau 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198976"
---
# <a name="compiler-warning-level-3-c4192"></a>Avertissement du compilateur (niveau 3) C4192

exclusion automatique de’name’lors de l’importation de la bibliothèque de types’Library'

Une bibliothèque `#import` contient un élément, un *nom*, qui est également défini dans les en-têtes système Win32. En raison des limitations des bibliothèques de types, les noms tels que **IUnknown** ou GUID sont souvent définis dans une bibliothèque de types, en dupliquant la définition des en-têtes système. `#import` détecte ces éléments et refuse de les incorporer dans les fichiers d’en-tête. tlh et. tli.

Pour remplacer ce comportement, utilisez `#import` attributs [no_auto_exclude](../../preprocessor/no-auto-exclude.md) et [include ()](../../preprocessor/include-parens.md).
