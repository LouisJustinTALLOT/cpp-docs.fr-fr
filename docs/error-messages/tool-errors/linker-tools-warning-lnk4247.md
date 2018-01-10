---
title: "LNK4247 d’avertissement des outils Éditeur de liens | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4247
dev_langs: C++
helpviewer_keywords: LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 517605993199942f863faa78e14a022529214a64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4247"></a>Avertissement des outils Éditeur de liens LNK4247
point d’entrée 'nom_fonction_décoré' a déjà un attribut de thread ; 'attribute' ignoré  
  
 Un point d’entrée, spécifié avec [/ENTRY (symbole de Point d’entrée)](../../build/reference/entry-entry-point-symbol.md), possédait un attribut de thread, mais [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) a également été spécifié, avec un modèle de thread différent.  
  
 L’éditeur de liens a ignoré la valeur spécifiée avec /CLRTHREADATTRIBUTE.  
  
 Pour résoudre cet avertissement :  
  
-   Supprimez /CLRTHREADATTRIBUTE de votre build.  
  
-   Supprimez l’attribut à partir de votre fichier de code source.  
  
-   Retirez les deux l’attribut source et /CLRTHREADATTRIBUTE de votre version et acceptez le modèle de thread CLR par défaut.  
  
-   Modifiez la valeur passée à /CLRTHREADATTRIBUTE., tel qu’il corresponde à l’attribut dans la source.  
  
-   Modifier l’attribut dans la source, de sorte qu’il corresponde à la valeur passée à /CLRTHREADATTRIBUTE.  
  
 L’exemple suivant génère l’erreur LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```