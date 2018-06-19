---
title: Erreur du compilateur C2012 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2012
dev_langs:
- C++
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e52b08d7a7d93682e1750ae545183195fc563734
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164120"
---
# <a name="compiler-error-c2012"></a>Erreur du compilateur C2012
nom manquant après '<'  
  
 Une directive `#include` ne contient pas le nom de fichier nécessaire.  
  
 L’exemple suivant génère l’erreur C2012 :  
  
```  
// C2012.cpp  
#include <   // C2012 include the filename to resolve  
```  
  
 Solution possible :  
  
```  
// C2012b.cpp  
// compile with: /c  
#include <stdio.h>  
```