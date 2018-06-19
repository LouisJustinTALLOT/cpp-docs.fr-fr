---
title: LNK1158 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1158
dev_langs:
- C++
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71cee2a31d1a7b05104031fbf41e8e3addb82d7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300184"
---
# <a name="linker-tools-error-lnk1158"></a>Erreur des outils Éditeur de liens LNK1158
Impossible d’exécuter 'nom_fichier'  
  
 Le fichier exécutable donné appelé par [lien](../../build/reference/linker-command-line-syntax.md) n’est pas dans le répertoire qui contient le lien, ni dans un répertoire spécifié dans la variable d’environnement PATH.  
  
 Par exemple, vous obtiendrez cette erreur si vous essayez d’utiliser le paramètre PGOPTIMIZE le [LTCG](../../build/reference/ltcg-link-time-code-generation.md) option de l’éditeur de liens sur un ordinateur avec un système d’exploitation 32 bits.