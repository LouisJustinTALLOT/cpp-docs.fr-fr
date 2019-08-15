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
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506256"
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
|[CGdiObject::Attach](#attach)|Joint un objet Windows GDI à un `CGdiObject` objet.|
|[CGdiObject::CreateStockObject](#createstockobject)|Récupère un handle vers l’un des stylets boursiers, des pinceaux ou des polices prédéfinis de Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Supprime l’objet Windows GDI attaché à l’objet `CGdiObject` de la mémoire en libérant tout le stockage système associé à l’objet.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Supprime tous les objets `CGdiObject` temporaires créés par `FromHandle`.|
|[CGdiObject::Detach](#detach)|Détache un objet Windows GDI d’un `CGdiObject` objet et retourne un handle vers l’objet Windows GDI.|
|[CGdiObject::FromHandle](#fromhandle)|Retourne un pointeur vers un `CGdiObject` objet en fonction d’un handle vers un objet Windows GDI.|
|[CGdiObject::GetObject](#getobject)|Remplit une mémoire tampon avec des données qui décrivent l’objet Windows GDI attaché `CGdiObject` à l’objet.|
|[CGdiObject::GetObjectType](#getobjecttype)|Récupère le type de l’objet GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Retourne `m_hObject` à moins que **ce** ne soit null, auquel cas la valeur null est retournée.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CGdiObject:: Operator! =](#operator_neq)|Détermine si deux objets GDI ne sont pas égaux logiquement.|
|[CGdiObject::operator ==](#operator_eq_eq)|Détermine si deux objets GDI sont logiquement égaux.|
|[CGdiObject:: Operator HGDIOBJ](#operator_hgdiobj)|Récupère un HANDLE vers l’objet Windows GDI attaché.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|HANDLE contenant la valeur HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN ou HFONT attaché à cet objet.|

## <a name="remarks"></a>Notes

Vous ne créez jamais `CGdiObject` directement un. Au lieu de cela, vous créez un objet à partir de l’une de `CPen` ses `CBrush`classes dérivées, telles que ou.

Pour plus d’informations `CGdiObject`sur, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="attach"></a>  CGdiObject::Attach

Joint un objet Windows GDI à un `CGdiObject` objet.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
HANDLE d’un objet Windows GDI (par exemple, HPEN ou HBRUSH).

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la pièce jointe est réussie; Sinon, 0.

##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject

Construit un objet `CGdiObject`.

```
CGdiObject();
```

### <a name="remarks"></a>Notes

Vous ne créez jamais `CGdiObject` directement un. Au lieu de cela, vous créez un objet à partir de l’une de `CPen` ses `Cbrush`classes dérivées, telles que ou.

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

Récupère un handle vers l’un des stylets, pinceaux ou polices Windows GDI prédéfinis, et attache l’objet GDI à l' `CGdiObject` objet.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Constante spécifiant le type d’objet stock souhaité. Consultez le paramètre *fnObject* pour [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) dans le SDK Windows pour obtenir une description des valeurs appropriées.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction avec l’une des classes dérivées qui correspond au type d’objet Windows GDI, par `CPen` exemple pour un stylet boursier.

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

Supprime l’objet Windows GDI attaché de la mémoire en libérant tout le stockage système associé à l’objet Windows GDI.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet GDI a été correctement supprimé; Sinon, 0.

### <a name="remarks"></a>Notes

Le stockage associé à l' `CGdiObject` objet n’est pas affecté par cet appel. Une application ne doit pas `DeleteObject` appeler sur `CGdiObject` un objet qui est actuellement sélectionné dans un contexte de périphérique.

Lorsqu’un pinceau de motif est supprimé, l’image bitmap associée au pinceau n’est pas supprimée. La bitmap doit être supprimée indépendamment.

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

Appelée automatiquement par le `CWinApp` gestionnaire de temps d’inactivité, `DeleteTempMap` supprime tous `CGdiObject` les objets temporaires `FromHandle`créés par.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Notes

`DeleteTempMap`détache l’objet Windows GDI attaché à un objet temporaire `CGdiObject` avant de supprimer l' `CGdiObject` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

Détache un objet Windows GDI d’un `CGdiObject` objet et retourne un handle vers l’objet Windows GDI.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Valeur de retour

`HANDLE` À l’objet Windows GDI détaché; sinon, NULL si aucun objet GDI n’est attaché.

##  <a name="fromhandle"></a>  CGdiObject::FromHandle

Retourne un pointeur vers un `CGdiObject` objet en fonction d’un handle vers un objet Windows GDI.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
HANDLE d’un objet Windows GDI.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CGdiObject` qui peut être temporaire ou permanent.

### <a name="remarks"></a>Notes

Si un `CGdiObject` objet n’est pas déjà attaché à l’objet Windows GDI, un `CGdiObject` objet temporaire est créé et attaché.

Cet objet `CGdiObject` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valide que pendant le traitement d’un message de fenêtre.

##  <a name="getobject"></a>  CGdiObject::GetObject

Remplit une mémoire tampon avec des données qui définissent un objet spécifié.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Paramètres

*nCount*<br/>
Spécifie le nombre d’octets à copier dans la mémoire tampon *lpObject* .

*lpObject*<br/>
Pointe vers une mémoire tampon fournie par l’utilisateur qui doit recevoir les informations.

### <a name="return-value"></a>Valeur de retour

Nombre d’octets récupérés; Sinon, 0 si une erreur se produit.

### <a name="remarks"></a>Notes

La fonction récupère une structure de données dont le type dépend du type d’objet graphique, comme indiqué dans la liste suivante:

|Object|Type de mémoire tampon|
|------------|-----------------|
|`CPen`|[LOGPEN,](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[PIXELS](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Non pris en charge|

Si l’objet est un `CBitmap` objet, `GetObject` retourne uniquement les informations de format de largeur, de hauteur et de couleur de l’image bitmap. Les bits réels peuvent être récupérés à l’aide de [CBitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Si l’objet est un `CPalette` objet, `GetObject` récupère un mot qui spécifie le nombre d’entrées dans la palette. La fonction ne récupère pas la structure [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) qui définit la palette. Une application peut recevoir des informations sur les entrées de palette en appelant [cpalette:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

Récupère le type de l’objet GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de l’objet, en cas de réussite; Sinon, 0. Il peut avoir l’une des valeurs suivantes :

- Bitmap OBJ_BITMAP

- Pinceau OBJ_BRUSH

- Police OBJ_FONT

- Palette OBJ_PAL

- Stylet OBJ_PEN

- Stylet étendu OBJ_EXTPEN

- Région OBJ_REGION

- Contexte de périphérique OBJ_DC

- Contexte de périphérique de mémoire OBJ_MEMDC

- Métafichier OBJ_METAFILE

- Contexte de périphérique de métafichier OBJ_METADC

- Métafichier OBJ_ENHMETAFILE amélioré

- OBJ_ENHMETADC-contexte de périphérique de métafichier amélioré

##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle

Retourne `m_hObject` à moins que **ce** ne soit null, auquel cas la valeur null est retournée.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Valeur de retour

HANDLE de l’objet Windows GDI attaché; Sinon, la valeur est NULL si aucun objet n’est attaché.

### <a name="remarks"></a>Notes

Cela fait partie du paradigme de l’interface de gestion générale et est utile quand NULL est une valeur valide ou spéciale pour un descripteur.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

HANDLE contenant la valeur HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE ou HFONT attaché à cet objet.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: Operator! =

Détermine si deux objets GDI ne sont pas égaux logiquement.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Pointeur vers un existant `CGdiObject`.

### <a name="remarks"></a>Notes

Détermine si un objet GDI sur le côté gauche n’est pas égal à un objet GDI sur le côté droit.

##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==

Détermine si deux objets GDI sont logiquement égaux.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Référence à un existant `CGdiObject`.

### <a name="remarks"></a>Notes

Détermine si un objet GDI sur le côté gauche est égal à un objet GDI situé à droite.

##  <a name="operator_hgdiobj"></a>CGdiObject:: Operator HGDIOBJ

Récupère un HANDLE vers l’objet Windows GDI attaché; Sinon, la valeur est NULL si aucun objet n’est attaché.

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject

Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`UnrealizeObject` Tandis que est une fonction membre de la classe, elle doit être appelée uniquement `CBrush` sur `CPalette` les `CGdiObject` objets ou.

Pour `CBrush` les objets `UnrealizeObject` , indique au système de réinitialiser l’origine du pinceau donné la prochaine fois qu’il est sélectionné dans un contexte de périphérique. Si l’objet est un `CPalette` objet, `UnrealizeObject` indique au système de réaliser la palette comme s’il n’avait pas été réalisé précédemment. La prochaine fois que l’application appelle la fonction [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) pour la palette spécifiée, le système remappe complètement la palette logique à la palette du système.

La `UnrealizeObject` fonction ne doit pas être utilisée avec des objets stock. La `UnrealizeObject` fonction doit être appelée chaque fois qu’une nouvelle origine de pinceau est définie (au moyen de la fonction [CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) ). La `UnrealizeObject` fonction ne doit pas être appelée pour le pinceau actuellement sélectionné ou pour la palette actuellement sélectionnée d’un contexte d’affichage.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CBitmap, classe](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush, classe](../../mfc/reference/cbrush-class.md)<br/>
[CFont, classe](../../mfc/reference/cfont-class.md)<br/>
[CPalette, classe](../../mfc/reference/cpalette-class.md)<br/>
[CPen, classe](../../mfc/reference/cpen-class.md)<br/>
[CRgn, classe](../../mfc/reference/crgn-class.md)
