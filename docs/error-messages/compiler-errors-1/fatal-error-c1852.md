---
title: Erreur irrécupérable C1852 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11160eea5e978a0c1ef67255d4e96b48fe2d101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199509"
---
# <a name="fatal-error-c1852"></a>Erreur irrécupérable C1852
'nom_fichier' n’est pas un fichier d’en-tête précompilé valide  
  
 Le fichier n’est pas un en-tête précompilé.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Fichier non valide spécifié avec **/Yu** ou **#pragma hdrstop**.  
  
2.  Le compilateur suppose que l’extension de fichier est .pch, sauf indication contraire de votre part.