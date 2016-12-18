---
title: "Erreur du compilateur CS1646 | Microsoft Docs"
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
  - "CS1646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1646"
ms.assetid: 5e4b0f1e-8de3-42b0-bde6-9f882677a409
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1646
Mot clé, identificateur ou chaîne attendue après le spécificateur textuel : @  
  
 Pour plus d’informations sur l’utilisation du spécificateur textuel '@', consultez les littéraux de chaîne. Le spécificateur textuel est autorisé uniquement avant une chaîne, un mot clé ou un identificateur. Pour résoudre cette erreur, supprimez le symbole @ des emplacements incorrects ou ajoutez la chaîne, le mot clé ou l’identificateur nécessaire.  
  
 L’exemple suivant génère l’erreur CS1646 :  
  
```  
// CS1646 class C { int i = @5;  // CS1646 // Try this line instead: // int i = 5; }  
```