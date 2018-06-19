---
title: Erreur du compilateur C3291 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3291
dev_langs:
- C++
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 829479ce2514d77f5be99feae03edf056963af7c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254197"
---
# <a name="compiler-error-c3291"></a>Erreur du compilateur C3291
'default' : ne peut pas être le nom d'une propriété triviale  
  
 Une propriété triviale ne peut pas être nommée `default`. Pour plus d'informations, voir [property](../../windows/property-cpp-component-extensions.md) .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3291.  
  
```  
// C3291.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String ^ default;   // C3291  
   property System::String ^ Default;   // OK  
};  
```