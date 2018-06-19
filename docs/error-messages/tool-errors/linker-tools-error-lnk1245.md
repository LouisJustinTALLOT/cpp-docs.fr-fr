---
title: LNK1245 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a1c2e5f7bf66946dcc5816d7a20fd485b59b45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299238"
---
# <a name="linker-tools-error-lnk1245"></a>Erreur des outils Éditeur de liens LNK1245
sous-système non valide '« sous-système spécifié ; /SUBSYSTEM doit être WINDOWS, WINDOWSCE ou CONSOLE  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) a été utilisée pour compiler l’objet et une des conditions suivantes a la valeur true :  
  
-   Un point d’entrée personnalisé a été défini ([/ENTRY](../../build/reference/entry-entry-point-symbol.md)), telle que l’éditeur de liens n’a pas pu déduire un sous-système.  
  
-   Une valeur a été passée à la [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option de l’éditeur de liens qui n’est pas valide pour les objets/CLR.  
  
 Dans les deux cas, la résolution est de spécifier une valeur valide pour l’option de l’éditeur de liens /SUBSYSTEM.