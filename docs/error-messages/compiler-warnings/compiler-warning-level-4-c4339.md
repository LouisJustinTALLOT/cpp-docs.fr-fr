---
title: "Avertissement du compilateur (niveau 4) C4339 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4339"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4339"
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 4) C4339
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : utilisation de ce type non défini dans les métadonnées WinRT ou CLR, ce qui peut provoquer une exception runtime  
  
 Un type n'a pas été défini dans le code qui a été compilé pour Windows Runtime ou le Common Language Runtime.  Définissez ce type pour éviter une exception d'exécution possible.  
  
 Cet avertissement est désactivé par défaut.  Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 L'exemple suivant génère l'erreur C4339 et montre comment la corriger :  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```