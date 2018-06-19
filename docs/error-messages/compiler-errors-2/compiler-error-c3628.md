---
title: Erreur du compilateur C3628 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5210a9bb91b86c63f0cebabce8901c9af50ae896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266413"
---
# <a name="compiler-error-c3628"></a>Erreur du compilateur C3628
'base' classe' : managé ou WinRTclasses prennent uniquement en charge l’héritage public  
  
Une tentative a tenté d’utiliser un managé ou WinRT classe en tant qu’un [privé](../../cpp/private-cpp.md) ou [protégé](../../cpp/protected-cpp.md) classe de base. Managé ou WinRT classe peut uniquement être utilisée comme classe de base avec [public](../../cpp/public-cpp.md) accès.  
  
L'exemple suivant génère l'erreur C3628 et montre comment la corriger :  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
