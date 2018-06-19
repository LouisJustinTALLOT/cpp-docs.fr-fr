---
title: Erreur du compilateur C3699 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3699
dev_langs:
- C++
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddbf6ac43b2a3d987faa86fab6d9862068fc0fe0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265027"
---
# <a name="compiler-error-c3699"></a>Erreur du compilateur C3699
'opérateur' : Impossible d’utiliser cette indirection sur le type 'type'  
  
 Tentative d’utilisation de l’indirection qui n’est pas autorisée sur `type`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3699.  
  
```  
// C3699.cpp  
// compile with: /clr /c  
using namespace System;  
int main() {  
   String * s;   // C3699  
   // try the following line instead  
   // String ^ s2;  
}  
```  
  
## <a name="example"></a>Exemple  
 Une propriété triviale ne peut pas avoir de type référence. Pour plus d'informations, voir [property](../../windows/property-cpp-component-extensions.md) . L’exemple suivant génère C3699.  
  
```  
// C3699_b.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String % x;   // C3699  
   property System::String ^ y;   // OK  
};  
```  
  
## <a name="example"></a>Exemple  
 L’équivalent d’une syntaxe « pointeur vers un pointeur » est un handle vers une référence de suivi. L’exemple suivant génère C3699.  
  
```  
// C3699_c.cpp  
// compile with: /clr /c  
using namespace System;  
void Test(String ^^ i);   // C3699  
void Test2(String ^% i);  
```