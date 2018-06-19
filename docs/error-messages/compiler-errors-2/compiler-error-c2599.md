---
title: Erreur du compilateur C2599 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2599
dev_langs:
- C++
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce7741e878b8743346bf9a088d973d65c4d7c290
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232937"
---
# <a name="compiler-error-c2599"></a>Erreur du compilateur C2599
'enum' : une déclaration anticipée de type enum n’est pas autorisée.  
  
 Le compilateur ne prend plus en déclaration anticipée d’une énumération managée.  
  
 Déclaration anticipée d’un type enum n’est pas autorisée sous [/Za](../../build/reference/za-ze-disable-language-extensions.md).  
  
 L’exemple suivant génère l’erreur C2599 :  
  
```  
// C2599.cpp  
// compile with: /clr /c  
enum class Status;   // C2599  
  
enum class Status2 { stop2, hold2, go2};   
  
ref struct MyStruct {  
   // Delete the following line to resolve.  
   Status m_status;  
  
   Status2 m_status2;   // OK  
};  
  
enum class Status { stop, hold, go };  
```