---
title: Erreur du compilateur C2014 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2014
dev_langs:
- C++
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 839fececb10897c799473ae328afb9f422b4c390
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165959"
---
# <a name="compiler-error-c2014"></a>Erreur du compilateur C2014
commande de préprocesseur doit commencer comme premier espace autre que blanc  
  
 Le `#` signe d’une directive de préprocesseur doit être le premier caractère d’une ligne qui n’est pas un espace blanc.  
  
 L’exemple suivant génère l’erreur C2014 :  
  
```  
// C2014.cpp  
int k; #include <stdio.h>   // C2014  
```  
  
 Solution possible :  
  
```  
// C2014b.cpp  
// compile with: /c  
int k;   
#include <stdio.h>  
```