---
title: "L’avertissement C4121 (niveau 4) d’avertissement de compilateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4121
dev_langs: C++
helpviewer_keywords: C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4886f8274ed8813cf556529efe657dca786f0e36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4121"></a>Avertissement C4121 de compilateur (niveau 4) d’avertissement
'symbole' : l'alignement d'un membre était sensible à la compression  
  
 Le compilateur a ajouté du remplissage pour aligner un membre de structure dans la limite de compression. Toutefois, la valeur de compression est inférieure à la taille du membre. Par exemple, l'extrait de code suivant produit l'avertissement C4121 :  
  
```  
// C4121.cpp  
// compile with: /W4 /c  
#pragma pack(2)  
struct s  
{  
   char a;  
   int b; // C4121  
   long long c;  
};  
```  
  
 Pour résoudre ce problème, effectuez l'une des modifications suivantes :  
  
-   Modifiez la taille de compression en lui assignant une valeur égale ou supérieure à la taille du membre à l'origine de l'erreur. Par exemple, dans cet extrait de code, remplacez `pack(2)` par `pack(4)` ou `pack(8)`.  
  
-   Réorganisez les déclarations des membres par taille, de la plus grande à la plus petite. Dans l'extrait de code, inversez l'ordre des membres de structure de sorte que le membre `long long` précède `int`, et que `int` précède `char`.  
  
 Cet avertissement se produit uniquement lorsque le compilateur ajoute du remplissage avant les membres de données. Il ne se produit pas lorsque la compression a placé des données à un emplacement de mémoire qui n'est pas aligné pour le type de données, mais qu'aucun remplissage n'a été placé avant le membre de données. Lorsque les données ne sont pas alignées sur les limites qui sont des multiples de la taille des données, les performances peuvent se dégrader. Les lectures et écritures de données non alignées provoquent des erreurs de processeur sur certaines architectures. En outre, ces erreurs peuvent nécessiter deux ou trois fois plus de temps pour être résolues. Les accès aux données non alignées ne peuvent pas être portés sur certaines architectures RISC.  
  
 Vous pouvez utiliser [#pragma pack](../../preprocessor/pack.md) ou [/Zp](../../build/reference/zp-struct-member-alignment.md) pour spécifier l’alignement de structure. (Le compilateur ne génère pas cet avertissement lorsque **/Zp1** est spécifié.)