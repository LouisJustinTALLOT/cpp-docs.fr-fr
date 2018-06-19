---
title: Erreur du compilateur C2392 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2392
dev_langs:
- C++
helpviewer_keywords:
- C2392
ms.assetid: 98ced473-6383-46ed-b79c-21857d65dcb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffb2ce4ef752d91eaadc66d17aadf3838ee560df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197908"
---
# <a name="compiler-error-c2392"></a>Erreur du compilateur C2392
'méthode1' : retours covariants types ne sont pas pris en charge dans managed ou WinRTtypes, le cas contraire, 'méthode2' est substitué  
  
 Types de retour covariants ne sont pas autorisés pour les fonctions membres Windows Runtime ou lors de la compilation avec le [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) option.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2392 et montre comment la corriger.  
  
```  
// C2392.cpp  
// compile with: /clr  
public ref struct B {  
public:  
   int i;  
};  
  
public ref struct D: public B{};  
  
public ref struct B1 {  
public:  
   virtual B^ mf() {  
      B^ pB = gcnew B;  
      pB->i = 11;  
      return pB;  
   }  
};  
  
public ref struct D1: public B1 {  
public:  
   virtual D^ mf() override {  // C2392  
   // try the following line instead  
   // virtual B^ mf() override {  
   // return type D^ is covariant with B^, not allowed with CLR types  
      D^ pD = gcnew D;  
      pD->i = 12;  
      return pD;  
   }  
};  
  
int main() {  
   B1^ pB1 = gcnew D1;  
   B^ pB = pB1->mf();  
   D^ pD = dynamic_cast<D^>(pB);  
}  
```