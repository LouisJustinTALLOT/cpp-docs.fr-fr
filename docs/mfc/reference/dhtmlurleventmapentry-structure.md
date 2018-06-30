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
ms.openlocfilehash: ee629d9dcffc80ce20306989cad72d466722af87
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123329"
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
 *szUrl*  
 L’URL.  
  
 *pEventMap*  
 La table d’événements associée à l’URL.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdhtml.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

