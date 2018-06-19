---
title: Erreur du compilateur C2006 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93880e7d767de3101cd7a292af5fa2874cae86bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165569"
---
# <a name="compiler-error-c2006"></a>Erreur du compilateur C2006
'directive' attendu d’un nom de fichier, a trouvé 'jeton'  
  
 Directives telles que [#include](../../preprocessor/hash-include-directive-c-cpp.md) ou [#import](../../preprocessor/hash-import-directive-cpp.md) nécessitent un nom de fichier. Pour résoudre cette erreur, assurez-vous que *jeton* est un nom de fichier valide. En outre, placez le nom de fichier entre guillemets doubles ou des crochets pointus.  
  
 L’exemple suivant génère l’erreur C2006 :  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Solution possible :  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```