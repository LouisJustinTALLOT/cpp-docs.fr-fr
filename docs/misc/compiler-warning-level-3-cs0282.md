---
title: "Avertissement du compilateur (niveau&#160;3) CS0282 | Microsoft Docs"
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
  - "CS0282"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0282"
ms.assetid: fd4cda5d-81c7-40e3-8424-c938b3447356
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0282
Il n’existe pas de classement défini entre les champs dans plusieurs déclarations de classe partielle ou struct 'type'. Pour spécifier un classement, tous les champs d’instance doivent se trouver dans la même déclaration.  
  
 Pour résoudre cette erreur, placez toutes les variables de membre dans une même définition de classe partielle.  
  
 Cette erreur se produit souvent quand un `struct` partiel est défini dans plusieurs emplacements et que les variables membres se trouvent dans plusieurs définitions.  
  
 Le code suivant génère l’avertissement CS0282.  
  
## Exemple  
 Ce code contient une description d’un `struct`. Compilez ces deux modules ensemble en une seule étape à l’aide de la commande suivante :  
  
 `csc /targt:library cs0282_1.cs cs0282_2.cs`  
  
```  
partial struct A { int i; }  
```  
  
## Exemple  
 Ce code contient une description en conflit du même `struct`.  
  
```  
partial struct A { int j; }  
```