---
title: Hse_version_info, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: daf1565c2fe2d7a4620f83b765671fea80502102
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335813"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO, structure
Cette structure est indiquée par le *pVer* paramètre dans le `CHttpServer::GetExtensionVersion` fonction membre. Il fournit le numéro de version d’ISA et une description textuelle de l’ISA Server.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *dwExtensionVersion*  
 Le numéro de version de l’ISA Server.  
  
 *lpszExtensionDesc*  
 La description textuelle de l’ISA Server. L’implémentation par défaut fournit le texte d’espace réservé ; substituer `CHttpServer::GetExtensionVersion` afin de fournir votre propre description.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** httpext.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

