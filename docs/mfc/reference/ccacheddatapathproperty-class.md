---
description: 'En savoir plus sur : classe CCachedDataPathProperty'
title: CCachedDataPathProperty, classe
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
ms.openlocfilehash: a61d2553afc4415da29399293843deb1be5f113d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122497"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty, classe

Implémente une propriété de contrôle OLE transférée de façon asynchrone et mise en cache dans un fichier de mémoire.

## <a name="syntax"></a>Syntaxe

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCachedDataPathProperty :: CCachedDataPathProperty](#ccacheddatapathproperty)|Construit un objet `CCachedDataPathProperty`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCachedDataPathProperty :: m_Cache](#m_cache)|`CMemFile` objet dans lequel mettre en cache les données.|

## <a name="remarks"></a>Notes

Un fichier de mémoire est stocké dans la mémoire RAM plutôt que sur le disque, ce qui est utile pour les transferts temporaires rapides.

Avec `CAysncMonikerFile` et `CDataPathProperty` , fournit des `CCachedDataPathProperty` fonctionnalités pour l’utilisation de monikers asynchrones dans les contrôles OLE. Avec `CCachedDataPathProperty` les objets, vous pouvez transférer des données de façon asynchrone à partir d’une URL ou d’une source de fichier et les stocker dans un fichier de mémoire via la `m_Cache` variable publique. Toutes les données sont stockées dans le fichier de mémoire, et il n’est pas nécessaire de substituer [ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) , sauf si vous souhaitez surveiller les notifications et répondre. Par exemple, si vous transférez un grand. Fichier GIF et souhaitez notifier à votre contrôle que davantage de données sont arrivées et qu’il doit se redessiner, substituer `OnDataAvailable` pour effectuer la notification.

La classe `CCachedDataPathProperty` est dérivée de `CDataPathProperty` .

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les rubriques suivantes :

- [Premières étapes Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Premières étapes Internet : monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a> CCachedDataPathProperty :: CCachedDataPathProperty

Construit un objet `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Pointeur vers l’objet de contrôle ActiveX à associer à cet `CCachedDataPathProperty` objet.

*lpszPath*<br/>
Chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui référence l’emplacement absolu réel de la propriété. `CCachedDataPathProperty` utilise des URL, et non des noms de fichiers. Si vous souhaitez un `CCachedDataPathProperty` objet pour un fichier, ajoutez file://au chemin d’accès.

### <a name="remarks"></a>Notes

L' `COleControl` objet pointé par *pControl* est utilisé par les classes dérivées [Open](../../mfc/reference/cdatapathproperty-class.md#open) et récupéré. Si *pControl* a la valeur null, le contrôle utilisé avec `Open` doit être défini avec [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si *lpszPath* a la valeur null, vous pouvez transmettre le chemin d’accès `Open` ou le définir avec [setPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a> CCachedDataPathProperty :: m_Cache

Contient le nom de la classe du fichier mémoire dans lequel les données sont mises en cache.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Notes

Un fichier de mémoire est stocké dans la mémoire RAM plutôt que sur le disque.

## <a name="see-also"></a>Voir aussi

[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
