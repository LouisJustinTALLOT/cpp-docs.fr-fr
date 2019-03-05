---
title: HSE_VERSION_INFO, structure
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 97f34bebae8a486a825d04b23c5a92fbd4aefa42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267834"
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

*dwExtensionVersion*<br/>
Le numéro de version de l’ISA Server.

*lpszExtensionDesc*<br/>
La description textuelle de l’ISA Server. L’implémentation par défaut fournit le texte d’espace réservé ; substituer `CHttpServer::GetExtensionVersion` afin de fournir votre propre description.

## <a name="requirements"></a>Spécifications

**En-tête :** httpext.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
