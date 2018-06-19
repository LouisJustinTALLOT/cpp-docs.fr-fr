---
title: Propriété du modificateur d’un accélérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d99d4656f2835f9adb60f310e429c4ccb97ac7b6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854052"
---
# <a name="accelerator-modifier-property"></a>Modifier, propriété d'un accélérateur
Les éléments suivants sont des entrées valides pour la propriété Modifier dans la table d’accélérateurs.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun**|Utilisateur appuie sur uniquement la valeur de clé. Utilisé avec les valeurs ASCII/ANSI 001 à 026, ce qui est ^ A à ^ Z (CTRL-A à CTRL-Z).|  
|**ALT**|Utilisateur doit appuyer sur la touche ALT avant la valeur de clé.|  
|**CTRL**|Utilisateur doit appuyer sur la touche CTRL ENFONCÉE avant que la valeur de clé. Non valide avec le Type ASCII.|  
|**Touche MAJ enfoncée**|Utilisateur doit appuyer sur la touche MAJ avant la valeur de clé.|  
|**Ctrl + Alt**|Utilisateur doit appuyer sur la touche CTRL et la touche ALT avant la valeur de clé. Non valide avec le Type ASCII.|  
|**CTRL + MAJ**|Utilisateur doit appuyer sur la touche CTRL et la touche MAJ avant la valeur de clé. Non valide avec le Type ASCII.|  
|**ALT + MAJ**|Utilisateur doit appuyer sur la touche ALT et la touche MAJ avant la valeur de clé. Non valide avec le Type ASCII.|  
|**Ctrl + Alt + Maj**|Utilisateur doit appuyer sur MAJ, CTRL et ALT avant la valeur de clé. Non valide avec le Type ASCII.|  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)