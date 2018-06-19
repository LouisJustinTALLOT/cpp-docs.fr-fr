---
title: Erreur irrécupérable NMAKE U1070 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe39a5d6f6074596561cd8e32f7b9428bc60f6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327039"
---
# <a name="nmake-fatal-error-u1070"></a>Erreur irrécupérable NMAKE U1070
cycle dans la définition de macro 'nom_macro'  
  
 La définition de macro donnée contenait une macro dont la définition contenue la macro donnée. Définitions de macros circulaires ne sont pas valides.  
  
## <a name="example"></a>Exemple  
 Les définitions de macros suivantes  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 génère l’erreur suivante :  
  
```  
cycle in macro definition 'TWO'  
```