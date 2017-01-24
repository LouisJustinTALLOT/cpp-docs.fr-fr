---
title: "Avertissement du compilateur (niveau&#160;1) CS1695 | Microsoft Docs"
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
  - "CS1695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1695"
ms.assetid: cc4e4d00-0618-400d-985b-90968e98772c
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1695
Syntaxe de \#pragma checksum non valide ; doit être \#pragma checksum "nom\_fichier" "{XXXXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXXXXX}" "XXXX..."  
  
 Vous devriez rarement rencontrer cette erreur étant donné que la somme de contrôle est généralement insérée au moment de l’exécution si vous générez du code par le biais de l’API Code Dom.  
  
 Toutefois, si vous deviez taper cette instruction `#pragma` et si vous tapiez incorrectement le GUID ou la somme de contrôle, vous obtiendriez cette erreur. La vérification de syntaxe par le compilateur ne confirme pas la saisie correcte d’un GUID, mais elle vérifie bien le nombre de chiffres et de délimiteurs, ainsi que la nature hexadécimale de ces chiffres. De même, elle vérifie que la somme de contrôle contient un nombre pair de chiffres et que les chiffres sont hexadécimaux.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1695 :  
  
```  
// CS1695.cs #pragma checksum "12345"  // CS1695 public class Test { static void Main() { } }  
```