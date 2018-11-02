---
title: Compilateur avertissement (niveau 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519711"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilateur avertissement (niveau 3) C4192

exclusion automatique de « name » lors de l’importation de bibliothèque de types 'library'

Un `#import` bibliothèque contient un élément, *nom*, qui est également défini dans les en-têtes systèmes Win32. En raison des limitations des bibliothèques de types, des noms tels que **IUnknown** ou GUID sont souvent définis dans une bibliothèque de types, duplication de la définition des en-têtes système. `#import` détectera ces éléments et refuser de les incorporer dans les fichiers d’en-tête .tlh et .tli.

Pour remplacer ce comportement, utilisez `#import` attributs [no_auto_exclude](../../preprocessor/no-auto-exclude.md) et [include()](../../preprocessor/include-parens.md).