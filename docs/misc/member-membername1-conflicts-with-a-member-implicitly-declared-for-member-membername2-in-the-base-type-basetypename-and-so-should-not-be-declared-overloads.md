---
title: "Le membre &#39;&lt;nom_membre1&gt;&#39; est en conflit avec un membre implicitement d&#233;clar&#233; pour le membre &#39;&lt;nom_membre2&gt;&#39; dans le type de base &#39;&lt;nom_type_base&gt;&#39; et ne doit donc pas &#234;tre d&#233;clar&#233; comme &#39;Overloads&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40023"
  - "bc40023"
helpviewer_keywords: 
  - "BC40023"
ms.assetid: 82bb29a6-8d49-47a4-8c19-b21e97dfc7de
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre1&gt;&#39; est en conflit avec un membre implicitement d&#233;clar&#233; pour le membre &#39;&lt;nom_membre2&gt;&#39; dans le type de base &#39;&lt;nom_type_base&gt;&#39; et ne doit donc pas &#234;tre d&#233;clar&#233; comme &#39;Overloads&#39;
Une propriété ou procédure d’une classe dérivée utilise le même nom qu’un membre implicite de la classe de base et spécifie le mot clé [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md).  
  
 La surcharge permet de définir de nombreuses versions d’une propriété ou d’une procédure dans la même classe. Vous ne pouvez pas définir une version supplémentaire d’un membre de classe de base tant que ce membre ne spécifie pas `Overloads`. Étant donné que les membres implicites ne spécifient pas `Overloads`, le compilateur suppose que cette propriété ou procédure masque \([Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)\) le membre de classe de base implicite.  
  
 Le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] crée des membres implicites correspondant à certains éléments de programmation que vous déclarez. Le tableau suivant récapitule ces membres implicites ou *synthétiques*.  
  
|Élément déclaré|Membres créés implicitement|  
|---------------------|---------------------------------|  
|Énumération|Membre `value__`|  
|Événement|Procédure `add_<eventname>`<br /><br /> Procédure `remove_<eventname>`<br /><br /> Champ `<eventname>Event`<br /><br /> Délégué `<eventname>EventHandler`|  
|Propriété|Procédure `get_<propertyname>`<br /><br /> Procédure `set_<propertyname>`|  
|Membre `My.Form`, membre `My.WebService` ou membre d’une classe marquée avec l’attribut <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Variable `m_<variablename>``Static`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
  
 En raison du risque de conflits de noms, vous devez éviter de nommer un élément de programmation déclaré en utilisant la même forme que l’un de ces membres implicites. Par exemple, vous devez éviter tout nom d’élément qui commence par `get_` ou `set_`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements et le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40023  
  
### Pour corriger cette erreur  
  
-   Modifiez le nom de la propriété ou procédure pour éviter tout conflit avec les noms répertoriés dans le tableau précédent.  
  
## Voir aussi  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)