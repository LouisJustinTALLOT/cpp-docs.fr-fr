---
title: Lock::operator == | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
dev_langs:
- C++
helpviewer_keywords:
- lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38cefb80b1c4c6969cba976c30383c1499a4968d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048888"
---
# <a name="lockoperator"></a>lock::operator==
Opérateur d’égalité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*t*<br/>
Objet à comparer pour l’égalité.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `true` si `t` est identique à l’objet du verrou, `false` dans le cas contraire.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
```Output  
Equal!  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [Lock, membres](../dotnet/lock-members.md)   
 [lock::operator!=](../dotnet/lock-operator-inequality.md)