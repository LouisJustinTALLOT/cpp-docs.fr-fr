---
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
ms.openlocfilehash: e7394250c93bcc718d50f2ea9b3522256df7c820
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296708"
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
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Construit un objet `CCachedDataPathProperty`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` objet dans lequel en cache des données.|

## <a name="remarks"></a>Notes

Un fichier de mémoire est stocké dans la mémoire RAM, plutôt que sur le disque et est utile pour les transferts temporaires rapide.

Avec `CAysncMonikerFile` et `CDataPathProperty`, `CCachedDataPathProperty` fournit les fonctionnalités pour l’utilisation de monikers asynchrones dans les contrôles OLE. Avec `CCachedDataPathProperty` objets, vous êtes en mesure de transférer des données de façon asynchrone à partir d’une URL ou le fichier source et le stocker dans un fichier de mémoire via la `m_Cache` variable publique. Toutes les données sont stockées dans le fichier de mémoire, et il n’est pas nécessaire de substituer [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) sauf si vous souhaitez surveiller les notifications et d’y répondre. Par exemple, si vous transférez une grande taille. Fichier GIF et souhaitez notifier votre contrôle que davantage de données est arrivé et il doit se redessiner, substituer `OnDataAvailable` pour rendre la notification.

La classe `CCachedDataPathProperty` est dérivée de `CDataPathProperty`.

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les rubriques suivantes :

- [Internet premières étapes : Contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Internet premières étapes : Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl.h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

Construit un objet `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Un pointeur vers l’objet de contrôle ActiveX doit être associé à ce `CCachedDataPathProperty` objet.

*lpszPath*<br/>
Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CCachedDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CCachedDataPathProperty` de l’objet d’un fichier, faites précéder file:// pour le chemin d’accès.

### <a name="remarks"></a>Notes

Le `COleControl` objet vers lequel pointe *pControl* est utilisé par [Open](../../mfc/reference/cdatapathproperty-class.md#open) et récupérées par les classes dérivées. Si *pControl* est NULL, le contrôle utilisé avec `Open` doit être défini avec [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si *lpszPath* est NULL, vous pouvez passer dans le chemin d’accès via `Open` ou définissez-la avec [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

Contient le nom de classe du fichier de mémoire dans lequel les données sont mises en cache.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Notes

Un fichier de mémoire est stocké dans la mémoire RAM, plutôt que sur le disque.

## <a name="see-also"></a>Voir aussi

[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
