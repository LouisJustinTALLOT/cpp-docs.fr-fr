---
title: Erreur du compilateur C3465 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3465
dev_langs:
- C++
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1965b616ec3eb8c7de50f3a76b10e41f3579954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254034"
---
# <a name="compiler-error-c3465"></a>Erreur du compilateur C3465
pour pouvoir utiliser le type 'type', vous devez faire référence à l’assembly 'assembly'  
  
 Le transfert de type fonctionne pour une application cliente jusqu’à ce que vous recompiliez le client. Pour ce faire, vous avez besoin d’une référence pour chaque assembly contenant la définition d’un type utilisé dans votre application cliente.  
  
 Pour plus d’informations, consultez [transfert de Type (C + c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère un assembly qui contient le nouvel emplacement d’un type.  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère un assembly qui contenait auparavant la définition du type, mais qui contient désormais la syntaxe de transfert du type.  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3465.  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```