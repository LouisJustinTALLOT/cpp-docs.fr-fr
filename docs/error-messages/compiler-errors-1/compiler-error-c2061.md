---
title: Erreur du compilateur C2061 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4d4b018dbab16e8e376a3331a85d0f1b1004f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167377"
---
# <a name="compiler-error-c2061"></a>Erreur du compilateur C2061
Erreur de syntaxe : identificateur 'identificateur'  
  
 Le compilateur a détecté un identificateur là où il n’était pas attendu. Assurez-vous que `identifier` est déclaré avant de l’utiliser.  
  
 Un initialiseur peut être mis entre parenthèses. Pour éviter ce problème, incluez le déclarateur entre parenthèses ou rendre un `typedef`.  
  
 Cette erreur peut également être provoquée lorsque le compilateur détecte une expression comme argument de modèle de classe ; Utilisez [typename](../../cpp/typename.md) pour indiquer au compilateur qu’il s’agit d’un type.  
  
 L’exemple suivant génère l’erreur C2061 :  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 L’erreur C2061 peut se produire si vous passez un nom de l’instance [typeid](../../windows/typeid-cpp-component-extensions.md):  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```