---
title: Erreur du compilateur C3353 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47c9d1dd8c21e56613b9da00fc2bf4f7fbeafcca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253903"
---
# <a name="compiler-error-c3353"></a>Erreur du compilateur C3353
'délégué' : un délégué ne peut être créé qu'à partir d'une fonction globale ou à partir d'une fonction membre d'un type managé ou WinRT  
  
 Les délégués, déclarés avec le [déléguer](../../windows/delegate-cpp-component-extensions.md) (mot clé), ne peut être déclaré dans une portée globale.  
  
 L'exemple suivant génère l'erreur C3353 :  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```