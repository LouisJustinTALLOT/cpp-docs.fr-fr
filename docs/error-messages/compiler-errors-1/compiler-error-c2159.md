---
title: Erreur du compilateur C2159 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2159
dev_langs:
- C++
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 412907d8c2f6c6f14adfb4f0799f3f2715a8381e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167552"
---
# <a name="compiler-error-c2159"></a>Erreur du compilateur C2159
plus d'une classe de stockage spécifiée  
  
 Une déclaration contient plusieurs classes de stockage.  
  
 L’exemple suivant génère l’erreur C2159 :  
  
```  
// C2159.cpp  
// compile with: /c  
static int i;   // OK  
extern static int i;   // C2159  
```