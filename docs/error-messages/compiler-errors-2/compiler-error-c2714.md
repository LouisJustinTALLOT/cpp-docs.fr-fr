---
title: Erreur du compilateur C2714 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2714
dev_langs:
- C++
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b012acdebd5ccddb056d9558bb1034ac2ba0b49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235158"
---
# <a name="compiler-error-c2714"></a>Erreur du compilateur C2714
__alignof (void) n’est pas autorisée.  
  
 Une valeur non valide a été passée à un opérateur.  
  
 Consultez [__alignof, opérateur](../../cpp/alignof-operator.md) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2714.  
  
```  
// C2714.cpp  
int main() {  
   return __alignof(void);   // C2714  
   return __alignof(char);   // OK  
}  
```