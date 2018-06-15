---
title: Délimiteurs pour les balises de documentation Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe65dfec3befa15ffebde3d074081ee11364f4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337572"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Délimiteurs pour les étiquettes de documentation Visual C++
L’utilisation de balises de documentation exige des délimiteurs, qui indiquent au compilateur où un commentaire de documentation commence et se termine.  
  
 Vous pouvez utiliser les genres de délimiteurs ci-dessous avec les balises de documentation XML :  
  
 `///`  
 Il s’agit de la forme illustrée dans les exemples de documentation et utilisée par les modèles de projet Visual C++.  
  
 `/** */`  
 Ce sont des délimiteurs multilignes.  
  
 Des règles de mise en forme s’appliquent quand vous utilisez les délimiteurs `/** */` :  
  
-   Pour la ligne qui contient le délimiteur `/**`, si le reste de la ligne est un espace blanc, la ligne n’est pas traitée dans le cadre des commentaires. Si le premier caractère est un espace blanc, ce caractère est ignoré et le reste de la ligne est traité. Sinon, tout le texte de la ligne après le délimiteur `/**` est traité comme faisant partie du commentaire.  
  
-   Pour la ligne qui contient le délimiteur `*/`, s’il n’y a que des espaces blancs jusqu’au délimiteur `*/`, cette ligne est ignorée. Sinon, le texte de la ligne jusqu’au délimiteur `*/` est traité comme faisant partie du commentaire, conformément aux règles de critères spéciaux décrites dans la puce suivante.  
  
-   Pour les lignes qui suivent celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne qui consiste en un espace blanc facultatif et un astérisque (`*`) suivi d’autres espaces blancs facultatifs. Si le compilateur trouve un ensemble commun de caractères au début de chaque ligne, il ignore ce modèle pour toutes les lignes qui suivent le délimiteur `/**`, jusqu’à la ligne (en l’incluant éventuellement) qui contient le délimiteur `*/`.  
  
 Voici quelques exemples :  
  
-   La seule partie du commentaire suivant qui sera traitée est la ligne qui commence par `<summary>`. Les deux formats de balise suivants produisent les mêmes commentaires :  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   Le compilateur applique un modèle « * » à ignorer au début des deuxième et troisième lignes.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   Le compilateur ne trouve aucun modèle dans ce commentaire, car la deuxième ligne n’a pas d’astérisque. Ainsi, tout le texte des deuxième et troisième lignes est traité comme faisant partie du commentaire jusqu’au délimiteur `*/`.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   Le compilateur ne trouve pas de modèle dans ce commentaire pour deux raisons. Tout d’abord, aucune ligne ne commence par un nombre constant d’espaces avant l’astérisque. Ensuite, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces. Ainsi, tout le texte de la deuxième ligne jusqu’à `*/` est traité comme faisant partie du commentaire.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)