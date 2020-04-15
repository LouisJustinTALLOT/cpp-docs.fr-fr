---
title: Classe CCachedDataPathProperty
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352363"
---
# <a name="ccacheddatapathproperty-class"></a>Classe CCachedDataPathProperty

Implémente une propriété de contrôle OLE transférée de façon asynchrone et mise en cache dans un fichier de mémoire.

## <a name="syntax"></a>Syntaxe

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Construit un objet `CCachedDataPathProperty`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`objet dans lequel mettre en cache les données.|

## <a name="remarks"></a>Notes

Un fichier mémoire est stocké dans la RAM plutôt que sur le disque et est utile pour les transferts temporaires rapides.

Avec `CAysncMonikerFile` et `CDataPathProperty` `CCachedDataPathProperty` , fournit des fonctionnalités pour l’utilisation de surnoms asynchrones dans les contrôles OLE. Avec `CCachedDataPathProperty` les objets, vous pouvez transférer des données asynchronement à partir d’une URL ou d’une source de fichier et les stocker dans un fichier mémoire via la `m_Cache` variable publique. Toutes les données sont stockées dans le fichier mémoire, et il n’est pas nécessaire de remplacer [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) sauf si vous voulez surveiller les notifications et répondre. Par exemple, si vous transférez un grand . Fichier GIF et que vous souhaitez informer votre contrôle que plus de `OnDataAvailable` données sont arrivées et qu’il devrait se redessiner, en l’écartant pour faire la notification.

La `CCachedDataPathProperty` classe est `CDataPathProperty`dérivée de .

Pour plus d’informations sur la façon d’utiliser les surnoms asynchrones et les contrôles ActiveX dans les applications Internet, voir les sujets suivants:

- [Les premières étapes d’Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Les premiers pas d’Internet : des monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty

Construit un objet `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Un pointeur à l’objet de `CCachedDataPathProperty` contrôle ActiveX à associer à cet objet.

*lpszPath*<br/>
Le chemin, qui peut être absolu ou relatif, utilisé pour créer un surnom asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CCachedDataPathProperty`utilise des URL, pas des noms de fichiers. Si vous `CCachedDataPathProperty` voulez un objet pour un fichier, prévoyez file:// sur le chemin.

### <a name="remarks"></a>Notes

L’objet `COleControl` pointé par *pControl* est utilisé par [Open](../../mfc/reference/cdatapathproperty-class.md#open) et récupéré par des classes dérivées. Si *le pControl* est NULL, le contrôle utilisé avec `Open` doit être réglé avec [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si *lpszPath* est NULL, vous pouvez `Open` passer dans le chemin à travers ou le régler avec [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache

Contient le nom de classe du fichier mémoire dans lequel les données sont mises en cache.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Notes

Un fichier mémoire est stocké dans la RAM plutôt que sur le disque.

## <a name="see-also"></a>Voir aussi

[Classe CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
