---
title: Du compilateur (niveau 1) d’avertissement C4274 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b941fc0cb32e268e33d3b0e1ae66079e8decaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286144"
---
# <a name="compiler-warning-level-1-c4274"></a>Du compilateur (niveau 1) d’avertissement C4274
\#Ident ignorée ; consultez la documentation pour #pragma comment (exestr, 'string')  
  
 La `#ident` directive, qui insère une chaîne spécifiée par l’utilisateur dans l’objet ou le fichier exécutable, est déconseillée. Par conséquent, le compilateur ignore la directive.  
  
> [!CAUTION]
>  C4274 d’avertissement vous indique d’utiliser le [#pragma comment (exestr, 'string')](../../preprocessor/comment-c-cpp.md) la directive. Toutefois, ce Conseil est déconseillé et sera être modifié dans une prochaine version du compilateur. Si vous utilisez la `#pragma` directive, l’outil de l’éditeur de liens (LINK.exe) ignore l’enregistrement de commentaires généré par la directive et émet un avertissement [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Au lieu du `#ident` directive, nous vous recommandons d’utiliser une chaîne de ressource de version de fichier dans votre application.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimer le `#ident "` *chaîne* `"` la directive.  
  
## <a name="see-also"></a>Voir aussi  
 [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)   
 [Outils de l’éditeur de liens LNK4229 d’avertissement](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md)