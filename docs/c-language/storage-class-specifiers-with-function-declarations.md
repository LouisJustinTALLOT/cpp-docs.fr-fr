---
title: "Spécificateurs de classe de stockage avec déclarations de fonction | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1073f0eef2a976866f0bacd0cfbe1f7e6f022334
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Spécificateurs de classe de stockage avec déclarations de fonction
Vous pouvez utiliser le spécificateur de classe de stockage **static** ou `extern` dans les déclarations de fonctions. Les fonctions ont toujours des durées de vie globales.  
  
 **Section spécifique à Microsoft**  
  
 Les déclarations de fonctions au niveau interne ont la même signification que les déclarations de fonctions au niveau externe. Cela signifie qu'une fonction est visible de son point de déclaration jusqu'au reste de l'unité de traduction, même si elle est déclarée au niveau de la portée locale.  
  
 **FIN de la section spécifique à Microsoft**  
  
 Les règles de visibilité des fonctions varient légèrement des règles pour les variables, comme suit :  
  
-   Une fonction déclarée comme étant **static** est visible uniquement dans le fichier source dans lequel elle est définie. Les fonctions du même fichier source peuvent appeler la fonction **static**, mais les fonctions dans d'autres fichiers sources ne peuvent pas y accéder directement par nom. Vous pouvez déclarer une autre fonction **static** avec le même nom dans un fichier source différent sans conflit.  
  
-   Les fonctions déclarées comme `extern` sont visibles dans tous les fichiers sources du programme (sauf si vous redéclarer ultérieurement une fonction comme étant **static**). Toute fonction peut appeler une fonction `extern`.  
  
-   Les déclarations de fonctions qui omettent le spécificateur de classe de stockage sont `extern` par défaut.  
  
 **Section spécifique à Microsoft**  
  
 Microsoft permet la redéfinition d'un identificateur `extern` comme étant **static**.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de stockage C](../c-language/c-storage-classes.md)