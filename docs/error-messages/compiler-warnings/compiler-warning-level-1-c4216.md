---
title: "Avertissement du compilateur (niveau 1) C4216 | Microsoft Docs"
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
  - "C4216"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4216"
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 1) C4216
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

extension non standard utilisée : long à virgule flottante  
  
 Les extensions Microsoft par défaut \(\/Ze\) traitent les **float long** comme des **double**.  La compatibilité ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) ne le fait pas.  Utilisez **double** pour assurer la compatibilité.  L'exemple suivant génère l'erreur C4216 :  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```