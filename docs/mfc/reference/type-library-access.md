---
title: Accès à la bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372871"
---
# <a name="type-library-access"></a>Accès à la bibliothèque de types

Les bibliothèques de type exposent les interfaces d’un contrôle OLE à d’autres applications OLE-aware. Chaque contrôle OLE doit avoir une bibliothèque de type si une ou plusieurs interfaces doivent être exposées.

Les macros suivantes permettent à un contrôle OLE de donner accès à sa propre bibliothèque de type :

### <a name="type-library-access"></a>Accès à la bibliothèque de types

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Déclare une `GetTypeLib` fonction de membre d’un contrôle OLE (doit être utilisé dans la déclaration de classe).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implémente une `GetTypeLib` fonction membre d’un contrôle OLE (doit être utilisé dans la mise en œuvre de la classe).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Déclare la `GetTypeLib` fonction de membre de votre classe de contrôle.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle se rapportait à la bibliothèque de type.

### <a name="remarks"></a>Notes

Utilisez cette macro dans le fichier d’en-tête de la classe de contrôle.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implémente la `GetTypeLib` fonction de membre du contrôle.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle se rapportait à la bibliothèque de type.

*tlid tlid*<br/>
Le numéro d’identification de la bibliothèque de type.

*wVerMajor (en)*<br/>
Le numéro de version principale de la bibliothèque de type.

*wVerMinor (en)*<br/>
Le numéro de version mineure de bibliothèque de type.

### <a name="remarks"></a>Notes

Cette macro doit apparaître dans le fichier d’implémentation de toute classe de contrôle qui utilise la macro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
