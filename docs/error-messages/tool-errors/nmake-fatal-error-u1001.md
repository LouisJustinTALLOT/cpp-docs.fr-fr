---
title: Erreur irrécupérable NMAKE U1001 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1001
dev_langs:
- C++
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68699a235f461a0f5550802cc009d345ecdba7c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316008"
---
# <a name="nmake-fatal-error-u1001"></a>Erreur irrécupérable NMAKE U1001
Erreur de syntaxe : caractère non conforme 'caractère' dans la macro  
  
 Le caractère donné apparaît dans une macro, mais n’est pas une lettre, un nombre ou un trait de soulignement.  
  
 Cette erreur peut résulter d’un signe des deux-points manquant dans une expansion macro :  
  
```  
syntax error : illegal character '=' in macro  
```