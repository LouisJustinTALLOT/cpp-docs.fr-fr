---
title: Accès à la bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420749"
---
# <a name="type-library-access"></a>Accès à la bibliothèque de types

Les bibliothèques de types exposent les interfaces d’un contrôle OLE à d’autres applications prenant en charge OLE. Chaque contrôle OLE doit avoir une bibliothèque de types si une ou plusieurs interfaces doivent être exposées.

Les macros suivantes permettent à un contrôle OLE de fournir l’accès à sa propre bibliothèque de types :

### <a name="type-library-access"></a>Accès à la bibliothèque de types

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Déclare une fonction membre `GetTypeLib` d’un contrôle OLE (doit être utilisé dans la déclaration de classe).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implémente une fonction membre `GetTypeLib` d’un contrôle OLE (doit être utilisé dans l’implémentation de classe).|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Déclare la fonction membre `GetTypeLib` de votre classe de contrôle.

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

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implémente la fonction membre `GetTypeLib` du contrôle.

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

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
