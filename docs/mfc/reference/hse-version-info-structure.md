---
title: HSE_VERSION_INFO, structure
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 6bdb668be037dfaa07e1121e4b61ea332e430e31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577284"
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

## <a name="requirements"></a>Configuration requise

**En-tête :** httpext.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

