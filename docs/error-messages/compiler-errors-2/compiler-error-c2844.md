---
title: Erreur du compilateur C2844 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a45e4a94e3d474be670f822d56a7c080f25693c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247307"
---
# <a name="compiler-error-c2844"></a>Erreur du compilateur C2844
'membre' : ne peut pas être un membre d’interface 'interface'  
  
 Un [classe d’interface](../../windows/interface-class-cpp-component-extensions.md) ne peut pas contenir un membre de données, sauf si elle est également une propriété.  
  
 Autre chose qu’une fonction membre ou de propriété n’est pas autorisée dans une interface. En outre, les constructeurs, destructeurs et les opérateurs ne sont pas autorisés.  
  
 L’exemple suivant génère l’erreur C2844 :  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
