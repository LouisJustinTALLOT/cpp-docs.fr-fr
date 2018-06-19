---
title: Erreur du compilateur C2719 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8779db363c506d2f4ad884e15f78ba8231caa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233332"
---
# <a name="compiler-error-c2719"></a>Erreur du compilateur C2719
'paramètre' : le paramètre formel avec __declspec(align('#')) ne sera pas aligné  
  
 Le [aligner](../../cpp/align-cpp.md) `__declspec` modificateur n’est pas autorisé sur les paramètres de fonction. L’alignement des paramètres de fonction est contrôlé par la convention d’appel utilisée. Pour plus d’informations, consultez [Conventions d’appel](../../cpp/calling-conventions.md).  
  
 L'exemple suivant génère l'erreur C2719 et montre comment la corriger :  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```