---
title: Compilateur avertissement (niveau 3) C4192 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671a8c83dcadcaa89372e53b6c3d677c5810b4a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114408"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilateur avertissement (niveau 3) C4192

exclusion automatique de « name » lors de l’importation de bibliothèque de types 'library'

Un `#import` bibliothèque contient un élément, *nom*, qui est également défini dans les en-têtes systèmes Win32. En raison des limitations des bibliothèques de types, des noms tels que **IUnknown** ou GUID sont souvent définis dans une bibliothèque de types, duplication de la définition des en-têtes système. `#import` détectera ces éléments et refuser de les incorporer dans les fichiers d’en-tête .tlh et .tli.

Pour remplacer ce comportement, utilisez `#import` attributs [no_auto_exclude](../../preprocessor/no-auto-exclude.md) et [include()](../../preprocessor/include-parens.md).