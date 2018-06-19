---
title: Erreur irrécupérable C1026 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c034d45b7f8b222471094f4580902ae1b8dc66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198103"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026
dépassement de capacité de la pile de l'analyseur, programme trop complexe  
  
 L’espace requis pour analyser le programme a provoqué un dépassement de capacité de pile du compilateur.  
  
 Réduire la complexité des expressions en :  
  
-   Diminution du niveau d’imbrication des `for` et `switch` instructions. Placez les instructions plus profondément imbriquées dans des fonctions séparées.  
  
-   Avec rupture des expressions longues qui impliquent des appels de fonction ou des opérateurs de virgules.