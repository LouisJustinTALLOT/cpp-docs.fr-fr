---
title: Erreur irrécupérable NMAKE U1033 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319268"
---
# <a name="nmake-fatal-error-u1033"></a>Erreur irrécupérable NMAKE U1033
Erreur de syntaxe : 'chaîne' inattendu  
  
 La chaîne n’est pas partie de la syntaxe valide d’un makefile.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Si la valeur de la fermeture de crochets pointus (**<<**) pour un fichier inline ne sont pas au début d’une ligne, l’erreur suivante se produit :  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Si une définition de macro dans le makefile contenue un signe égal (**=**) sans précédente nom ou si le nom en cours est une macro qui se développe vers rien, l’erreur suivante se produit :  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  Si le point-virgule (**;**) dans une ligne de commentaire dans les outils. INI n’est pas au début de la ligne, l’erreur suivante se produit :  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  Si le makefile a été mis en forme par un traitement de texte, l’erreur suivante peut se produire :  
  
    ```  
    syntax error : ':' unexpected  
    ```