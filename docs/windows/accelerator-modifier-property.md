---
title: Propriété modificateur d’un accélérateur | Microsoft Docs
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
ms.openlocfilehash: 0788536e776661b9a84a6cccc648a7db68389ae5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644253"
---
# <a name="accelerator-modifier-property"></a>Modifier, propriété d'un accélérateur
Les éléments suivants sont des entrées valides pour la propriété Modifier dans la table d’accélérateurs.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun**|Utilisateur appuie sur uniquement le **clé** valeur. Utilisé avec les valeurs ASCII/ANSI 001 à 026, ce qui est ^ A à ^ Z (CTRL-A à CTRL-Z).|  
|**Alt**|L’utilisateur doit appuyer sur la **Alt** clé avant du **clé** valeur.|  
|**Ctrl**|L’utilisateur doit appuyer sur la **Ctrl** clé avant du **clé** valeur. Non valide avec le Type ASCII.|  
|**Maj**|L’utilisateur doit appuyer sur la **MAJ** clé avant du **clé** valeur.|  
|**Ctrl + Alt**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **Alt** clé avant du **clé** valeur. Non valide avec le Type ASCII.|  
|**CTRL + MAJ**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|  
|**ALT + MAJ**|L’utilisateur doit appuyer sur le **Alt** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|  
|**Ctrl + Alt + Maj**|L’utilisateur doit appuyer sur **Ctrl**, **Alt**, et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)