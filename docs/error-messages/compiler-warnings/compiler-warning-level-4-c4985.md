---
title: Compilateur avertissement (niveau 4) C4985 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af8717f8b821311814a8aa4ee2f5b3e6ead89eef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4985"></a>Avertissement du compilateur (niveau 4) C4985
'symbol name' : attributs absents de la déclaration précédente.  
  
 Les annotations du langage d’annotation de code source Microsoft (SAL) dans la définition ou la déclaration de méthode actuelle diffèrent des annotations d’une déclaration précédente. Les mêmes annotations SAL doivent être utilisées dans la définition et les déclarations d’une méthode.  
  
 Le langage d’annotation de code source Microsoft (SAL) propose un ensemble d’annotations qui décrivent la manière dont une fonction exploite ses paramètres, les hypothèses qu’elle émet à leur sujet et les garanties apportées lors de la finition. Les annotations sont définies dans le fichier d’en-tête sal.h.  
  
 Notez que les macros SAL ne sont pas développées sauf si l’indicateur [/analyze](../../build/reference/analyze-code-analysis.md) est spécifié pour le projet. Quand vous spécifiez **/analyze**, le compilateur peut lever l’avertissement C4985, même si aucun avertissement ni aucune erreur n’est apparu sans **/analyze**.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Utilisez les mêmes annotations SAL dans la définition d’une méthode et toutes ses déclarations.  
  
## <a name="see-also"></a>Voir aussi  
 [Annotations SAL](../../c-runtime-library/sal-annotations.md)