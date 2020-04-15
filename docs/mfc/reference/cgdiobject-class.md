---
title: CGdiObject, classe
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373739"
---
# <a name="cgdiobject-class"></a>CGdiObject, classe

Fournit une classe de base pour différents genres d'objets GDI (Graphics Device Interface) Windows, par exemple des images bitmap, des zones, des pinceaux, des plumes, des palettes et des polices.

## <a name="syntax"></a>Syntaxe

```
class CGdiObject : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Construit un objet `CGdiObject`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Attache un objet Windows GDI à un `CGdiObject` objet.|
|[CGdiObject::CreateStockObject](#createstockobject)|Récupère une poignée sur l’un des stylos de stock, brosses ou polices prédéfinis Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Supprime l’objet GDI Windows `CGdiObject` attaché à l’objet de mémoire en libérant tout stockage du système associé à l’objet.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Supprime tous `CGdiObject` les objets `FromHandle`temporaires créés par .|
|[CGdiObject::Detach](#detach)|Détache un objet Windows GDI `CGdiObject` d’un objet et renvoie une poignée à l’objet GDI Windows.|
|[CGdiObject::DeHandle](#fromhandle)|Retourne un pointeur à un `CGdiObject` objet donné une poignée à un objet GDI Windows.|
|[CGdiObject::GetObject](#getobject)|Remplit un tampon avec des données qui décrivent l’objet GDI Windows attaché à l’objet. `CGdiObject`|
|[CGdiObject::GetObjectType](#getobjecttype)|Récupère le type de l’objet GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Retours `m_hObject` à moins **qu’il ne s’agisse** de NULL, auquel cas NULL est retourné.|
|[CGdiObject:UnrealizeObject](#unrealizeobject)|Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CGdiObject::opérateur !](#operator_neq)|Détermine si deux objets GDI ne sont logiquement pas égaux.|
|[CGdiObject::opérateur](#operator_eq_eq)|Détermine si deux objets GDI sont logiquement égaux.|
|[CGdiObject::opérateur HGDIOBJ](#operator_hgdiobj)|Récupère un HANDLE à l’objet Windows GDI ci-joint.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Un HANDLE contenant le HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN ou HFONT attaché à cet objet.|

## <a name="remarks"></a>Notes

Vous ne `CGdiObject` créez jamais un directement. Au contraire, vous créez un objet à `CPen` partir `CBrush`d’une de ses classes dérivées, comme ou .

Pour plus `CGdiObject`d’informations sur , voir [Objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::Attach

Attache un objet Windows GDI à un `CGdiObject` objet.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Un HANDLE à un objet Windows GDI (par exemple, HPEN ou HBRUSH).

### <a name="return-value"></a>Valeur de retour

Nonzero si l’attachement est réussi; sinon 0.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

Construit un objet `CGdiObject`.

```
CGdiObject();
```

### <a name="remarks"></a>Notes

Vous ne `CGdiObject` créez jamais un directement. Au contraire, vous créez un objet à `CPen` partir `Cbrush`d’une de ses classes dérivées, comme ou .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

Récupère une poignée sur l’un des stylos, brosses ou polices Windows GDI prédéfinis `CGdiObject` et attache l’objet GDI à l’objet.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Une constante spécifiant le type d’objet de stock souhaité. Voir le paramètre *fnObject* pour [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) dans le SDK Windows pour une description des valeurs appropriées.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction avec l’une des classes dérivées qui correspond `CPen` au type d’objet GDI Windows, comme pour un stylo stock.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

Supprime l’objet Windows GDI joint de la mémoire en libérant tout stockage du système associé à l’objet GDI Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet GDI a été supprimé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Le stockage associé `CGdiObject` à l’objet n’est pas affecté par cet appel. Une application ne `DeleteObject` doit `CGdiObject` pas faire appel à un objet qui est actuellement sélectionné dans un contexte d’appareil.

Lorsqu’une brosse à motifs est supprimée, la bitmap associée à la brosse n’est pas supprimée. Le bitmap doit être supprimé indépendamment.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

Appelé automatiquement `CWinApp` par le gestionnaire `DeleteTempMap` de temps `CGdiObject` d’arrêt, supprime tous les objets temporaires créés par `FromHandle`.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Notes

`DeleteTempMap`détache l’objet Windows GDI attaché `CGdiObject` à un objet `CGdiObject` temporaire avant de supprimer l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::Detach

Détache un objet Windows GDI `CGdiObject` d’un objet et renvoie une poignée à l’objet GDI Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Valeur de retour

A `HANDLE` à l’objet Windows GDI détaché; autrement NULL si aucun objet GDI n’est attaché.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::DeHandle

Retourne un pointeur à un `CGdiObject` objet donné une poignée à un objet GDI Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Un HANDLE à un objet GDI Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CGdiObject` à un qui peut être temporaire ou permanent.

### <a name="remarks"></a>Notes

Si `CGdiObject` un objet n’est pas déjà attaché `CGdiObject` à l’objet GDI Windows, un objet temporaire est créé et joint.

Cet `CGdiObject` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. Une autre façon de dire cela est que l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject::GetObject

Remplit un tampon de données qui définissent un objet spécifié.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Paramètres

*nCompte*<br/>
Spécifie le nombre d’octets à copier dans le tampon *lpObject.*

*lpObject*<br/>
Indique un tampon fourni par l’utilisateur qui doit recevoir l’information.

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets récupérés; autrement 0 en cas d’erreur.

### <a name="remarks"></a>Notes

La fonction récupère une structure de données dont le type dépend du type d’objet graphique, comme le montre la liste suivante :

|Object|Type tampon|
|------------|-----------------|
|`CPen`|[LOGPEN (EN ANGLAIS)](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH (LOGBRUSH)](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[Bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Non pris en charge|

Si l’objet `CBitmap` est `GetObject` un objet, retourne seulement la largeur, la hauteur et les informations de format de couleur de la bitmap. Les bits réels peuvent être récupérés en utilisant [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Si l’objet `CPalette` est `GetObject` un objet, récupère un WORD qui spécifie le nombre d’entrées dans la palette. La fonction ne récupère pas la structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) qui définit la palette. Une application peut obtenir des informations sur les entrées de palette en appelant [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

Récupère le type de l’objet GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Valeur de retour

Le type de l’objet, en cas de succès; sinon 0. Il peut s'agir de l'une des valeurs suivantes :

- OBJ_BITMAP Bitmap

- Brosse OBJ_BRUSH

- OBJ_FONT Font

- OBJ_PAL Palette

- stylo OBJ_PEN

- OBJ_EXTPEN stylo étendu

- Région OBJ_REGION

- contexte OBJ_DC Appareil

- OBJ_MEMDC contexte du dispositif mémoire

- OBJ_METAFILE Metafile

- OBJ_METADC contexte de dispositif Metafile

- OBJ_ENHMETAFILE Metafile amélioré

- OBJ_ENHMETADC contexte de dispositif amélioré-métaafile

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Retours `m_hObject` à moins **qu’il ne s’agisse** de NULL, auquel cas NULL est retourné.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Un HANDLE à l’objet Windows GDI ci-joint; autrement NULL si aucun objet n’est attaché.

### <a name="remarks"></a>Notes

Cela fait partie du paradigme d’interface de poignée générale et est utile lorsque NULL est une valeur valide ou spéciale pour une poignée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject::m_hObject

Un HANDLE contenant le HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE ou HFONT attaché à cet objet.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::opérateur !

Détermine si deux objets GDI ne sont logiquement pas égaux.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Un pointeur `CGdiObject`à un existant .

### <a name="remarks"></a>Notes

Détermine si un objet GDI sur le côté gauche n’est pas égal à un objet GDI sur le côté droit.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::opérateur

Détermine si deux objets GDI sont logiquement égaux.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Une référence à `CGdiObject`un existant .

### <a name="remarks"></a>Notes

Détermine si un objet GDI sur le côté gauche est égal à un objet GDI sur le côté droit.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::opérateur HGDIOBJ

Récupère un HANDLE à l’objet Windows GDI ci-joint ; autrement NULL si aucun objet n’est attaché.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject:UnrealizeObject

Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Bien `UnrealizeObject` qu’il s’agit d’une fonction membre de la `CGdiObject` classe, il ne doit être invoqué que sur ou sur `CBrush` des `CPalette` objets.

Pour `CBrush` les `UnrealizeObject` objets, dirige le système pour réinitialiser l’origine du pinceau donné la prochaine fois qu’il est sélectionné dans un contexte d’appareil. Si l’objet `CPalette` est `UnrealizeObject` un objet, dirige le système pour réaliser la palette comme si elle n’avait pas été réalisée auparavant. La prochaine fois que l’application appelle le [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) fonction pour la palette spécifiée, le système remaps complètement la palette logique à la palette du système.

La `UnrealizeObject` fonction ne doit pas être utilisée avec des objets en stock. La `UnrealizeObject` fonction doit être appelée chaque fois qu’une nouvelle origine de brosse est définie (au moyen de la [fonction CDC::SetBrushOrg).](../../mfc/reference/cdc-class.md#setbrushorg) La `UnrealizeObject` fonction ne doit pas être demandée pour le pinceau actuellement sélectionné ou la palette actuellement sélectionnée de n’importe quel contexte d’affichage.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush, classe](../../mfc/reference/cbrush-class.md)<br/>
[Classe CFont](../../mfc/reference/cfont-class.md)<br/>
[Classe CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Classe CPen](../../mfc/reference/cpen-class.md)<br/>
[CRgn, classe](../../mfc/reference/crgn-class.md)
