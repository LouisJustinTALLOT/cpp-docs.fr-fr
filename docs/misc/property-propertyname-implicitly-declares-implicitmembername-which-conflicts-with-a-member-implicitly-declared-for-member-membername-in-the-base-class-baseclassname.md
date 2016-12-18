---
title: "La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre d&#233;clar&#233; implicitement pour la propri&#233;t&#233; &#39;&lt;nom_membre&gt;&#39; dans la classe de base &#39;&lt;nom_classe_base&gt;&#39; | Microsoft Docs"
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
  - "vbc40024"
  - "bc40024"
helpviewer_keywords: 
  - "BC40024"
ms.assetid: fab4f290-a41f-47d6-9bdb-44eb8dd395d5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre d&#233;clar&#233; implicitement pour la propri&#233;t&#233; &#39;&lt;nom_membre&gt;&#39; dans la classe de base &#39;&lt;nom_classe_base&gt;&#39;
Le membre '\<nom\_membre1\>' déclare implicitement '\<nom\_membre\_implicite\>', qui est en conflit avec un membre déclaré implicitement pour le membre '\<nom\_membre2\>' dans la classe de base '\<nom\_classe\_base\>'. Le membre ne doit donc pas être déclaré 'Overloads'.  
  
 Une propriété d’une classe dérivée génère un membre implicite portant le même nom qu’un membre implicite de la classe de base et spécifie le mot clé [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md).  
  
 La surcharge permet de définir plusieurs versions d’une propriété ou d’une procédure dans la même classe. Vous ne pouvez pas définir une version supplémentaire d’un membre de classe de base tant que ce membre ne spécifie pas `Overloads`. Étant donné que les membres implicites ne spécifient pas `Overloads`, le compilateur suppose que cette propriété occulte \([Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)\) le membre de classe de base implicite.  
  
 Le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] crée des membres implicites correspondant à certains éléments de programmation que vous déclarez. Le tableau suivant récapitule ces membres implicites ou *synthétiques*.  
  
|Élément déclaré|Membres créés implicitement|  
|---------------------|---------------------------------|  
|Énumération|Membre `value__`|  
|Événement|Procédure `add_<eventname>`<br /><br /> Procédure `remove_<eventname>`<br /><br /> Champ `<eventname>Event`<br /><br /> Délégué `<eventname>EventHandler`|  
|Propriété|Procédure `get_<propertyname>`<br /><br /> Procédure `set_<propertyname>`|  
|Membre `My.Form`, membre `My.WebService` ou membre d’une classe marquée avec l’attribut <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Variable `m_<variablename>``Static`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
  
 En raison du risque de conflits de noms, vous devez éviter de nommer un élément de programmation déclaré en utilisant la même forme que l’un de ces membres implicites. Par exemple, vous devez éviter tout nom d’élément qui commence par `get_` ou `set_`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40024  
  
### Pour corriger cette erreur  
  
-   Si vous envisagez de masquer ou d’occulter le membre de classe de base implicite, remplacez le mot clé [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) par le mot clé [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) dans la déclaration de la propriété.  
  
-   Si vous ne souhaitez pas occulter le membre de classe de base implicite, modifiez le nom de la propriété pour éviter les conflits avec les noms répertoriés dans le tableau précédent.  
  
## Voir aussi  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)