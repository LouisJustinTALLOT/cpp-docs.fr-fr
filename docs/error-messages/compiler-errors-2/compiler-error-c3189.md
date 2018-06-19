---
title: Erreur du compilateur C3189 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3189
dev_langs:
- C++
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf0e49ecf9c8003d8dcfe035b14c8f5c5067dbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251011"
---
# <a name="compiler-error-c3189"></a>Erreur du compilateur C3189
' typeid\<déclarateur abstrait de type >': cette syntaxe n’est plus pris en charge, utilisez :: typeid à la place  
  
 Une forme obsolète de [typeid](../../windows/typeid-cpp-component-extensions.md) a été utilisé, utilisez la nouvelle forme.  
  
 L’exemple suivant génère l’erreur C3189 :  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```