---
title: Avertissement LNK4022 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cffb9c4c67bc3003b8dcdda0ad3a2e8d55abe932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300369"
---
# <a name="linker-tools-warning-lnk4022"></a>Avertissement des outils Éditeur de liens LNK4022
Impossible de trouver une correspondance unique pour le symbole 'symbole'  
  
 LINK ou LIB a trouvé plusieurs correspondances pour le symbole non décoré donné et ne peut pas résoudre l’ambiguïté. Aucun fichier de sortie (.exe, .dll, .exp ou .lib) n’est généré. Cet avertissement est suivi par un avertissement [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pour chaque dupliquer le symbole et finalement suivi de l’erreur irrécupérable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Pour éviter cet avertissement, spécifiez le symbole dans sa forme décorée. Exécutez [DUMPBIN](../../build/reference/dumpbin-options.md) sur l’objet pour voir les noms décorés.