---
title: "C3380 d’erreur du compilateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: fbc75caa22d3c46b5a7a487662119a43b27eaf2b
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3380"></a>Erreur du compilateur C3380
'class' : spécificateur d’accès à l’assembly non valide - seuls 'public' ou 'private' sont autorisés  
  
 Lorsqu’il est appliqué à une classe managée ou un struct, le [public](../../cpp/public-cpp.md) et [privé](../../cpp/private-cpp.md) mots clés indiquent si la classe doit être exposée via les métadonnées de l’assembly. Seuls `public` ou `private` peut être appliqué à une classe dans un programme compilé avec [/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Le `ref` et `value` lorsque utilisé avec les mots clés [/clr](../../build/reference/clr-common-language-runtime-compilation.md), indiquent qu’une classe est managée (voir [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 L’exemple suivant génère l’erreur C3380 :  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  

