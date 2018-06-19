---
title: Erreur du compilateur C3132 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3132
dev_langs:
- C++
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb2ecc863bc06542e4bb2e78e71ce95279c004f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252385"
---
# <a name="compiler-error-c3132"></a>Erreur du compilateur C3132
'paramètre de fonction' : les tableaux de paramètres peuvent uniquement être appliqués à un argument formel de type 'single-dimensional managed array'  
  
 Le [ParamArray](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx) attribut a été appliqué à un paramètre qui n’est pas un tableau unidimensionnel.  
  
 L’exemple suivant génère l’erreur C3132 :  
  
```  
// C3132.cpp  
// compile with: /clr /c  
using namespace System;  
void f( [ParamArray] Int32[,] );   // C3132  
void g( [ParamArray] Int32[] );   // C3132  
  
void h( [ParamArray] array<Char ^> ^ MyArray );   // OK  
  
```