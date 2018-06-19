---
title: Erreur du compilateur C2871 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2871
dev_langs:
- C++
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aae5cc8200599b5f6b0643f07cbd342ec7d47c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250672"
---
# <a name="compiler-error-c2871"></a>Erreur du compilateur C2871
'nom' : un espace de noms portant ce nom n’existe pas  
  
Cette erreur se produit lorsque vous passez un identificateur qui n’est pas un espace de noms pour un [à l’aide de](../../cpp/namespaces-cpp.md#using_directives) directive.  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère C2871 :  
  
```cpp  
// C2871.cpp  
// compile with: /c
namespace a {
   int fn(int i) { return i; }
} 
namespace b { 
   using namespace d;   // C2871 because d is not a namespace  
   using namespace a;   // OK
}  
```