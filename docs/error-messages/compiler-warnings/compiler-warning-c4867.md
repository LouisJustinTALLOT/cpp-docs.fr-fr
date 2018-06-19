---
title: Avertissement du compilateur C4867 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46bf4866791ec82ac5984132903e22ab16e07ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270883"
---
# <a name="compiler-warning-c4867"></a>Avertissement du compilateur C4867
'fonction' : appel de fonction pas de liste d’arguments ; Utilisez 'appel' pour créer un pointeur vers membre  
  
 Un pointeur vers une fonction membre a été correctement initialisé.  
  
 Cet avertissement peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : conformité pointeur vers membre améliorée.  Le code compilé avant Visual C++ 2005 génère désormais C4867.  
  
 Cet avertissement est toujours émis en tant qu’erreur. Pour désactiver cet avertissement, utilisez le pragma [warning](../../preprocessor/warning.md) . Pour plus d’informations sur l’erreur C4867 et MFC/ATL, consultez [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```