---
title: Erreur du compilateur C2821 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2821
dev_langs:
- C++
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8c134d84ef27110cde83d54cbb8e46aa6a39efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236557"
---
# <a name="compiler-error-c2821"></a>Erreur du compilateur C2821
premier paramètre formel de 'operator new' doit être 'unsigned int'  
  
Le premier paramètre formel de la [new, opérateur](../../standard-library/new-operators.md#op_new) doit être non `int`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2821 :  
  
```cpp  
// C2821.cpp  
// compile with: /c  
void * operator new( /* unsigned int,*/ void * );   // C2821  
void * operator new( unsigned int, void * );  
```