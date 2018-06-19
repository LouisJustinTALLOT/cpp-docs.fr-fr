---
title: Erreur irrécupérable C1004 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88f76c00c8f5b36acf238f0da88e908eac6dbe8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197167"
---
# <a name="fatal-error-c1004"></a>Erreur irrécupérable C1004
fin de fichier inattendue rencontrée  
  
 Le compilateur a atteint la fin d’un fichier source sans pouvoir résoudre une construction. Le code peut être manquant, un des éléments suivants :  
  
-   Une accolade fermante  
  
-   Une parenthèse fermante  
  
-   Marque de commentaire fermant (* /)  
  
-   Un point-virgule  
  
 Pour résoudre cette erreur, vérifiez les éléments suivants :  
  
-   Le lecteur de disque par défaut l’espace est insuffisant pour les fichiers temporaires, lesquels nécessitent environ deux fois plus d’espace que le fichier source.  
  
-   Un `#if` directive qui correspond à false manque une fermeture `#endif` directive.  
  
-   Un fichier source ne se termine pas par un retour chariot et un saut de ligne.  
  
 L’exemple suivant génère l’erreur C1004 :  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 Solution possible :  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```