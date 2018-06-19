---
title: Erreur du compilateur C2337 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2337
dev_langs:
- C++
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af10023a044e8f4f602ca6a018139d557b99dffe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195124"
---
# <a name="compiler-error-c2337"></a>Erreur du compilateur C2337
'attribute name' : attribut introuvable  
  
 Vous avez utilisé un attribut qui n’est pas pris en charge dans cette version de Visual C++.  
  
 L’exemple suivant génère l’erreur C2337 :  
  
```  
// C2337.cpp  
// compile with: /c  
[emitidl];  
[module(name="x")];  
[grasshopper]   // C2337, not a supported attribute  
class a{};  
```