---
title: "Avertissement de conformit&#233; CLS CLS01703 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01703"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01703"
ms.assetid: b03ae369-3c4b-4080-9b78-4c9bfba581a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01703
Les types de pointeurs non managés ne sont pas conformes à CLS  
  
 Un champ conforme à CLS ne peut pas contenir une déclaration de pointeur natif.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS01703 :  
  
```  
// CLS01703.cpp // compile with: /clr /LD // CLS01703 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: int* Parameter;   // CLS01703 };  
```