---
title: "Erreur irrécupérable C1071 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1071
dev_langs: C++
helpviewer_keywords: C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: acd48401d3abc17d994e861bf6fb046450d88ca6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1071"></a>Erreur irrécupérable C1071
fin de fichier inattendue dans un commentaire  
  
 Le compilateur a atteint la fin du fichier lors de l’analyse d’un commentaire.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Terminaison de commentaire manquante (* /).  
  
2.  Caractères de saut de ligne manquants après un commentaire sur la dernière ligne d’un fichier source.  
  
 L’exemple suivant génère l’erreur C1071 :  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```