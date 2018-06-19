---
title: Compilateur avertissement (niveau 3) C4192 | Documents Microsoft
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
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291412"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilateur avertissement (niveau 3) C4192
exclusion automatique de 'name' lors de l’importation de bibliothèque de types 'library'  
  
 A `#import` bibliothèque contient un élément, *nom*, qui est également défini dans les en-têtes systèmes Win32. En raison des limitations des bibliothèques de types, des noms tels que **IUnknown** ou GUID sont souvent définis dans une bibliothèque de types, dupliquant la définition provenant des en-têtes système. `#import` détectera ces éléments et refuser les incorporer dans les fichiers d’en-tête .tlh et .tli.  
  
 Pour remplacer ce comportement, utilisez `#import` attributs [no_auto_exclude](../../preprocessor/no-auto-exclude.md) et [include()](../../preprocessor/include-parens.md).