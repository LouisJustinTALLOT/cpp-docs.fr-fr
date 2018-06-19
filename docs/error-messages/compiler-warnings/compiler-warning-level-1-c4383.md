---
title: Compilateur avertissement (niveau 1) C4383 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b78209cf4e3e320cca8b161a4e6c99eaca6d771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286082"
---
# <a name="compiler-warning-level-1-c4383"></a>Avertissement du compilateur (niveau 1) C4383
'opérateur_déréférencement_instance' : la signification du déréférencement d’un handle peut changer lorsqu’il existe un opérateur défini par l’utilisateur 'opérateur' ; Écrivez l’opérateur comme une fonction static pour rendre l’opérande explicite  
  
 Lorsque vous ajoutez un remplacement de l’instance définie par l’utilisateur de l’opérateur de déréférencement dans un type managé, vous substituez potentiellement la possibilité de retourner l’objet du handle de l’opérateur de déréférencement du type. Envisagez d’écrire un ligne statique, défini par l’utilisateur opérateur de déréférencement.  
  
 Pour plus d’informations, consultez [Handle sur l’opérateur Object (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) et [opérateur de référence de suivi](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
 En outre, un opérateur d’instance n’est pas disponible à d’autres compilateurs de langage via les métadonnées référencées. Pour plus d’informations, consultez [les opérateurs définis par l’utilisateur (C + c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4383.  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```