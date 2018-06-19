---
title: Types incomplets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c357364280244ea62e90badcb91f76138e81a990
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384370"
---
# <a name="incomplete-types"></a>Types incomplets
Un type incomplet est un type qui décrit un identificateur, mais qui ne présente pas les informations nécessaires pour permettre d'en déterminer la taille. Un « type incomplet » peut être :  
  
-   un type de structure dont vous n'avez pas encore spécifié les membres ;  
  
-   un type d'union dont vous n'avez pas encore spécifié les membres ;  
  
-   un type de tableau dont vous n'avez pas encore spécifié la dimension.  
  
 Le type void est un type incomplet qui ne peut pas être complété. Pour compléter un type incomplet, spécifiez les informations manquantes. Les exemples ci-dessous montrent comment créer et compléter des types incomplets.  
  
-   Pour créer un type de structure incomplet, déclarez un type de structure sans spécifier ses membres. Dans l'exemple ci-dessous, le pointeur `ps` pointe vers un type de structure incomplet nommé `student`.  
  
    ```  
    struct student *ps;  
    ```  
  
-   Pour compléter un type de structure incomplet, déclarez le même type de structure ultérieurement dans la même portée en spécifiant ses membres, comme suit :  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   Pour créer un type de tableau incomplet, déclarez un type de tableau sans spécifier son nombre de répétitions. Exemple :  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   Pour compléter un type de tableau incomplet, déclarez le même nom ultérieurement dans la même portée en spécifiant son nombre de répétitions, comme suit :  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations et types](../c-language/declarations-and-types.md)