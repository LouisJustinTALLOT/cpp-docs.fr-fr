---
title: Compilateur avertissement (niveau 3) C4359 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4359
dev_langs:
- C++
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7ddc48294734e5a180014ea20cf98b9d7374f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292982"
---
# <a name="compiler-warning-level-3-c4359"></a>Avertissement du compilateur (niveau 3) C4359
'type' : l’alignement réel (8) est supérieure à la valeur spécifiée dans __declspec(align())  
  
 L’alignement spécifié pour un type est inférieur à l’alignement du type de l’un de ses membres de données.  Pour plus d’informations, consultez [aligner](../../cpp/align-cpp.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4359 :.  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```