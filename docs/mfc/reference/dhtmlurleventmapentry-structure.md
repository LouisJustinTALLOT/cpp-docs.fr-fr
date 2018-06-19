---
title: Dhtmlurleventmapentry, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d038fa188ac431f20b0b19ca8ad8bf675943954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370056"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry, structure
Le `DHtmlUrlEventMapEntry` structure fournit la prise en charge des cartes URL plusieurs événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szUrl`  
 L’URL.  
  
 *pEventMap*  
 La table d’événements associée à l’URL.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdhtml.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

