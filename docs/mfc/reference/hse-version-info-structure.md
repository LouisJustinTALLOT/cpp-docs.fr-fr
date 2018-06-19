---
title: Hse_version_info, Structure | Documents Microsoft
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
ms.openlocfilehash: acdf63e062aab1407daee461e22f00f5d3c59cee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369884"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO, structure
Cette structure est pointée par le `pVer` paramètre dans le `CHttpServer::GetExtensionVersion` fonction membre. Il fournit le numéro de version ISA et une description de l’ISA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *dwExtensionVersion*  
 Le numéro de version de l’ISA.  
  
 *lpszExtensionDesc*  
 La description de l’ISA. L’implémentation par défaut fournit le texte d’espace réservé ; substituer `CHttpServer::GetExtensionVersion` afin de fournir votre propre description.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** httpext.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

