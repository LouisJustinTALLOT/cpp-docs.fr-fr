---
description: 'En savoir plus sur : structure HSE_VERSION_INFO'
title: HSE_VERSION_INFO, structure
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: fe03f3c4e00f9af62398993838927ce75410f17b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219627"
---
# <a name="hse_version_info-structure"></a>HSE_VERSION_INFO, structure

Cette structure est désignée par le paramètre *pVer* dans la `CHttpServer::GetExtensionVersion` fonction membre. Il fournit le numéro de version d’ISA et une description textuelle de l’ordinateur ISA.

## <a name="syntax"></a>Syntaxe

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>Paramètres

*dwExtensionVersion*<br/>
Numéro de version de l’ordinateur ISA.

*lpszExtensionDesc*<br/>
Description textuelle de l’ordinateur ISA. L’implémentation par défaut fournit le texte de l’espace réservé ; Remplacez `CHttpServer::GetExtensionVersion` pour fournir votre propre description.

## <a name="requirements"></a>Spécifications

**En-tête :** httpext. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
