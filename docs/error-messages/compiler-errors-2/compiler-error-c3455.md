---
title: Erreur du compilateur C3455 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3455
dev_langs:
- C++
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61f48f16164327645eb0c1982e9e11e8ea394276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253378"
---
# <a name="compiler-error-c3455"></a>Erreur du compilateur C3455
'attribute' : aucun des constructeurs d’attributs ne correspond aux arguments  
  
 Une valeur non valide a été utilisée pour déclarer un attribut.  Pour plus d'informations, voir [attribute](../../windows/attribute.md) .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3455.  
  
```  
// C3455.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute("MyAt")]   // C3455  
// try the following line instead  
// [attribute(All)]  
ref struct MyAttr {  
   MyAttr() {}  
};  
```