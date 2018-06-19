---
title: Erreur du compilateur C3458 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3458
dev_langs:
- C++
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5380f3a42bf297a5b2e674e1411abef832e7cb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255356"
---
# <a name="compiler-error-c3458"></a>Erreur du compilateur C3458
'attribute1' : attribut 'attribute2' déjà spécifié pour 'construct'  
  
 Deux attributs qui s’excluent mutuellement ont été spécifiés pour la même construction.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3458.  
  
```  
// C3458.cpp  
// compile with: /clr /c  
[System::Reflection::DefaultMember("Chars")]  
public ref class MyString {  
public:  
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458  
   property char default[int] {  
      char get(int index);  
      void set(int index, char c);  
   }  
};  
```