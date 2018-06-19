---
title: Erreur du compilateur C3163 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7be8fbba29cf82070d6fd96c76f810bda961489
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250887"
---
# <a name="compiler-error-c3163"></a>Erreur du compilateur C3163
'construct' : attributs non cohérents avec la déclaration précédente  
  
 L’ou les attributs qui sont appliqué à une définition en conflit avec l’ou les attributs qui sont appliqué à une déclaration.  
  
 Une résolution C3163 consiste à éliminer les attributs de la déclaration anticipée. Tous les attributs d’une déclaration anticipée doivent être inférieure aux attributs de la définition ou, au maximum, égal aux uns aux autres.  
  
 Des causes possibles de l’erreur C3163 implique le langage Microsoft source code annotation (SAL). Les macros SAL ne développez pas sauf si vous compilez votre projet à l’aide de la **/ analyze** indicateur. Un programme qui se compile correctement sans /ANALYZE peut lever l’exception C3163 si vous tentez de le recompiler avec l’option /Analyze. Pour plus d’informations sur SAL, consultez [Annotations SAL](../../c-runtime-library/sal-annotations.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3163.  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Annotations SAL](../../c-runtime-library/sal-annotations.md)