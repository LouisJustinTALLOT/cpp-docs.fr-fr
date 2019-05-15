---
title: Accès à la bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611530"
---
# <a name="type-library-access"></a>Accès à la bibliothèque de types

Bibliothèques de types exposent les interfaces d’un contrôle OLE pour d’autres applications prenant en charge OLE. Chaque contrôle OLE doit avoir une bibliothèque de types si une ou plusieurs interfaces doivent être exposées.

Les macros suivantes permettent un contrôle OLE fournir l’accès à sa propre bibliothèque de types :

### <a name="type-library-access"></a>Accès à la bibliothèque de types

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Déclare un `GetTypeLib` fonction membre d’un contrôle OLE (doit être utilisé dans la déclaration de classe).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implémente un `GetTypeLib` fonction membre d’un contrôle OLE (doit être utilisé dans l’implémentation de classe).|

##  <a name="declare_oletypelib"></a>  DECLARE_OLETYPELIB

Déclare le `GetTypeLib` fonction membre de votre classe de contrôle.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle lié à la bibliothèque de types.

### <a name="remarks"></a>Notes

Utilisez cette macro dans le fichier d’en-tête de classe contrôle.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="implement_oletypelib"></a>  IMPLEMENT_OLETYPELIB

Implémente le contrôle `GetTypeLib` fonction membre.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle lié à la bibliothèque de types.

*tlid*<br/>
Le numéro d’ID de la bibliothèque de types.

*wVerMajor*<br/>
Le numéro de version principale de bibliothèque de types.

*wVerMinor*<br/>
Le numéro de version mineure de bibliothèque de types.

### <a name="remarks"></a>Notes

Cette macro doit apparaître dans le fichier d’implémentation pour n’importe quelle classe de contrôle qui utilise le declare_oletypelib (macro).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
