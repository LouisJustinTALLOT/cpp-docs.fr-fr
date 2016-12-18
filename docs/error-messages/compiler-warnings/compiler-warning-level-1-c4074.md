---
title: "Avertissement du compilateur (niveau 1) C4074 | Microsoft Docs"
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
  - "C4074"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4074"
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 1) C4074
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

initialiseurs placés dans une zone d'initialisation réservée par le compilateur  
  
 La zone d'initialisation du compilateur, spécifiée par [\#pragma init\_seg](../../preprocessor/init-seg.md), est réservée par Microsoft.  Le code dans cette zone peut être exécuté avant initialisation de la bibliothèque runtime C.  
  
 L'exemple suivant génère l'erreur C4074 :  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```