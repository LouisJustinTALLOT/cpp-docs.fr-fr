---
title: Erreur du compilateur C2811 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2811
dev_langs:
- C++
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef9c608f19be28dbbeeca89c5f6672149e0ac4f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236077"
---
# <a name="compiler-error-c2811"></a>Erreur du compilateur C2811
'type1' : ne peut pas hériter de 'type2', une variable de référence classe peut uniquement hériter d’une classe ref ou classe interface  
  
 Vous avez tenté d’utiliser une classe non managée comme classe de base pour une classe managée.  
  
 L’exemple suivant génère C2811 :  
  
```  
// C2811.cpp  
// compile with: /clr /c  
struct S{};  
ref struct T {};  
ref class C : public S {};   // C2811  
ref class D : public T {};   // OK  
```