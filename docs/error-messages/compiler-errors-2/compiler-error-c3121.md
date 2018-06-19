---
title: Erreur du compilateur C3121 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3121
dev_langs:
- C++
helpviewer_keywords:
- C3121
ms.assetid: 1d3c7be4-d42d-4def-8d53-182c0c5cc237
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff398632375f6c676a3533f3a47064b94aecaa0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248086"
---
# <a name="compiler-error-c3121"></a>Erreur du compilateur C3121
Impossible de changer GUID pour la classe 'nom_classe'  
  
 Vous avez tenté de modifier l’ID de classe avec [__declspec (UUID)](../../cpp/uuid-cpp.md).  
  
 Par exemple, le code suivant génère C3121 :  
  
```  
// C3121.cpp  
[emitidl];  
[module(name="MyLibrary")];  
  
[coclass, uuid="00000000-0000-0000-0000-111111111111"]  
class __declspec(uuid("00000000-0000-0000-0000-111111111112")) A   // C3121  
{  
};  
int main()  
{  
}  
```