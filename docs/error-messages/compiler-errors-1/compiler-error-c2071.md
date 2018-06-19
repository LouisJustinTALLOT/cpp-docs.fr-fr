---
title: Erreur du compilateur C2071 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169203"
---
# <a name="compiler-error-c2071"></a>Erreur du compilateur C2071
'identificateur' : classe de stockage non conforme  
  
 `identifier` a été déclaré avec un non valide [classe de stockage](../../c-language/c-storage-classes.md). Cette erreur peut survenir quand plusieurs classes de stockage sont spécifiées pour un même identificateur ou quand la définition est incompatible avec la déclaration de la classe de stockage.  
  
 Pour résoudre ce problème, comprendre la classe de stockage prévue de l’identificateur, par exemple, `static` ou `extern`et corrigez la déclaration pour faire correspondre.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2071.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2071.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```