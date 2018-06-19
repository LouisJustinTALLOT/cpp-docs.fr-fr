---
title: Erreur du compilateur C2140 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2140
dev_langs:
- C++
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1634e2a61ed9ee22bdfde619f8710226b74e48a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169684"
---
# <a name="compiler-error-c2140"></a>Erreur du compilateur C2140
'type' : un type dépendant d’un paramètre de type générique n’est pas autorisé en tant qu’argument pour un trait de type intrinsèque du compilateur 'trait'  
  
 Un spécificateur de type non valide a été passé à un trait de type.  
  
 Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2140.  
  
```  
// C2140.cpp  
// compile with: /clr /c  
template <class T>  
  
struct is_polymorphic {  
   static const bool value = __is_polymorphic(T);  
};  
  
class x {};  
  
generic <class T>  
ref class C {  
   void f() {  
      System::Console::WriteLine(__is_polymorphic(T));   // C2140  
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140  
  
      System::Console::WriteLine(__is_polymorphic(x));   // OK  
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK  
   }  
};  
```