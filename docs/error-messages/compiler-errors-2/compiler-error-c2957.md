---
title: Erreur du compilateur C2957 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2957
dev_langs:
- C++
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3db11b7d74406ae8a683801b5fe75527ca421d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241449"
---
# <a name="compiler-error-c2957"></a>Erreur du compilateur C2957
'delim' : délimiteur gauche non valide : '<' attendu  
  
 Une classe générique était incorrecte.  
  
 L’exemple suivant génère l’erreur C2957 :  
  
```  
// C2957.cpp  
// compile with: /clr /LD  
generic << class T>   // C2957  
// try the following line instead  
// generic < class T>  
gc class C {};  
```