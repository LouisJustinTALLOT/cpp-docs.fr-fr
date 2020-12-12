---
description: 'En savoir plus sur : accès à la bibliothèque de types'
title: Accès à la bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: c855f82914e540ab13f4bc20581c041633b5bc0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218652"
---
# <a name="type-library-access"></a>Accès à la bibliothèque de types

Les bibliothèques de types exposent les interfaces d’un contrôle OLE à d’autres applications prenant en charge OLE. Chaque contrôle OLE doit avoir une bibliothèque de types si une ou plusieurs interfaces doivent être exposées.

Les macros suivantes permettent à un contrôle OLE de fournir l’accès à sa propre bibliothèque de types :

### <a name="type-library-access"></a>Accès à la bibliothèque de types

|Nom|Description|
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Déclare une `GetTypeLib` fonction membre d’un contrôle OLE (doit être utilisé dans la déclaration de classe).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implémente une `GetTypeLib` fonction membre d’un contrôle OLE (doit être utilisé dans l’implémentation de classe).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a> DECLARE_OLETYPELIB

Déclare la `GetTypeLib` fonction membre de votre classe de contrôle.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle associée à la bibliothèque de types.

### <a name="remarks"></a>Notes

Utilisez cette macro dans le fichier d’en-tête de la classe de contrôle.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a> IMPLEMENT_OLETYPELIB

Implémente la `GetTypeLib` fonction membre du contrôle.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle associée à la bibliothèque de types.

*tlid*<br/>
Numéro d’identification de la bibliothèque de types.

*wVerMajor*<br/>
Numéro de version principale de la bibliothèque de types.

*wVerMinor*<br/>
Numéro de version mineure de la bibliothèque de types.

### <a name="remarks"></a>Notes

Cette macro doit apparaître dans le fichier d’implémentation pour toute classe de contrôle qui utilise la macro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
