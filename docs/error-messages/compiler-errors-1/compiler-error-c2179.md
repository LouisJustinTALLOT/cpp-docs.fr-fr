---
title: Erreur du compilateur C2179 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2179
dev_langs: C++
helpviewer_keywords: C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7a14231f02983151936947c6ed0f880a5a8dabb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2179"></a>Erreur du compilateur C2179
'type' : un argument d’attribut ne peut pas utiliser les paramètres de type  
  
 Un paramètre de type générique est résolu pendant l’exécution. Toutefois, un paramètre d’attribut doit être résolu au moment de la compilation. Par conséquent, vous ne pouvez pas utiliser un paramètre de type générique en tant qu’argument à un attribut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2179.  
  
```  
// C2179.cpp  
// compile with: /clr  
using namespace System;  
  
public ref struct Attr : Attribute {  
   Attr(Type ^ a) {  
      x = a;  
   }  
  
   Type ^ x;  
};  
  
ref struct G {};  
  
generic<typename T>   
public ref class Z {   
public:  
   Type ^ d;  
   [Attr(T::typeid)]   // C2179  
   // try the following line instead  
   // [Attr(G::typeid)]  
   T t;  
};  
```