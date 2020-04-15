---
title: CBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352476"
---
# <a name="cbrush-class"></a>CBrush, classe

Encapsule un pinceau GDI (Graphics Device Interface) Windows.

## <a name="syntax"></a>Syntaxe

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Construit un objet `CBrush`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Initialise un pinceau avec le style, la couleur et le motif spécifié dans une structure [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Initialise un pinceau avec un motif spécifié par un bitmap indépendant de l’appareil (DIB).|
|[CBrush::CréerHatchBrush](#createhatchbrush)|Initialise une brosse avec le motif et la couleur éclos spécifiés.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Initialise un pinceau avec un motif spécifié par un bitmap.|
|[CBrush::CréerSolidBrush](#createsolidbrush)|Initialise un pinceau avec la couleur solide spécifiée.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crée un pinceau qui est la couleur du système par défaut.|
|[CBrush::DeHandle](#fromhandle)|Retourne un pointeur à un `CBrush` objet `HBRUSH` lorsqu’on lui donne une poignée sur un objet Windows.|
|[CBrush::GetLogBrush](#getlogbrush)|Obtient une structure [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBrush::opérateur HBRUSH](#operator_hbrush)|Retourne la poignée Windows `CBrush` attachée à l’objet.|

## <a name="remarks"></a>Notes

Pour utiliser `CBrush` un objet, construisez un `CBrush` `CDC` objet et transmettez-le à n’importe quelle fonction membre qui nécessite un pinceau.

Les brosses peuvent être solides, éclos ou à motifs.

Pour plus `CBrush`d’informations sur , voir [Objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush

Construit un objet `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*crColor (en)*<br/>
Spécifie la couleur du premier plan de la brosse comme une couleur RGB. Si la brosse est éclose, ce paramètre spécifie la couleur de l’éclosion.

*nIndex*<br/>
Spécifie le style d’écoutille de la brosse. Il peut s’agir de l’une des valeurs suivantes :

- HS_BDIAGONAL éclose vers le bas (de gauche à droite) à 45 degrés

- HS_CROSS crosshatch horizontal et vertical

- HS_DIAGCROSS Crosshatch à 45 degrés

- HS_FDIAGONAL’écoutille ascendante (de gauche à droite) à 45 degrés

- HS_HORIZONTAL trappe horizontale

- HS_VERTICAL Trappe verticale

*pBitmap (en)*<br/>
Points à `CBitmap` un objet qui spécifie une bitmap avec laquelle le pinceau peint.

### <a name="remarks"></a>Notes

`CBrush`a quatre constructeurs surchargés. Le constructeur sans arguments construit un objet `CBrush` uninitialisé qui doit être pararalisé avant qu’il puisse être utilisé.

Si vous utilisez le constructeur sans arguments, vous `CBrush` devez initialiser l’objet résultant avec [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), ou [CreateDIBPatternBrush](#createdibpatternbrush). Si vous utilisez l’un des constructeurs qui prend des arguments, alors aucune autre initialisation n’est nécessaire. Les constructeurs avec des arguments peuvent jeter une exception si des erreurs sont rencontrées, tandis que le constructeur sans arguments réussira toujours.

Le constructeur avec un seul paramètre [COLORREF](/windows/win32/gdi/colorref) construit une brosse solide avec la couleur spécifiée. La couleur spécifie une valeur RGB et peut être construite avec la macro RGB dans WINDOWS. H.

Le constructeur avec deux paramètres construit une brosse à trappe. Le paramètre *nIndex* spécifie l’index d’un modèle éclos. Le *paramètre crColor* spécifie la couleur.

Le constructeur avec `CBitmap` un paramètre construit une brosse à motifs. Le paramètre identifie un bitmap. Le bitmap est supposé avoir été créé en utilisant [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), ou [CBitmap:CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). La taille minimale pour une bitmap à utiliser dans un modèle de remplissage est de 8 pixels par 8 pixels.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect

Initialise un pinceau avec un style, une couleur et un motif spécifiés dans une structure [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Paramètres

*lpLogBrush*<br/>
Indique une structure [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur le pinceau.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être choisi comme brosse actuelle pour n’importe quel contexte de périphérique.

Un pinceau créé à l’aide d’un bit-mèche monochrome (1 bit par pixel) est dessiné à l’aide du texte actuel et des couleurs de fond. Pixels représentés par un peu réglé à 0 seront dessinés avec la couleur de texte actuelle. Pixels représentés par un peu réglé à 1 seront dessinés avec la couleur de fond actuelle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush

Initialise un pinceau avec le motif spécifié par un bitmap indépendant de l’appareil (DIB).

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Paramètres

*hPackedDIB*<br/>
Identifie un objet de mémoire globale contenant une bitmap indépendante d’appareil emballé (DIB).

*nUsage (en)*<br/>
Précise si les `bmiColors[]` domaines de la structure de données [BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (une partie du « DIB emballé ») contiennent des valeurs ou des indices RGB explicites dans la palette logique actuellement réalisée. Le paramètre doit être l’une des valeurs suivantes :

- DIB_PAL_COLORS La table couleur se compose d’un tableau d’index 16 bits.

- DIB_RGB_COLORS La table couleur contient des valeurs littérales RGB.

*lpPackedDIB*<br/>
Points à un DIB emballé `BITMAPINFO` composé d’une structure immédiatement suivie d’un tableau d’octets définissant les pixels de la bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné pour n’importe quel contexte d’appareil qui prend en charge les opérations de raster.

Les deux versions diffèrent dans la façon dont vous gérez le DIB :

- Dans la première version, pour obtenir une poignée `GlobalAlloc` à la DIB vous appelez la fonction Windows pour allouer un bloc de mémoire globale, puis remplir la mémoire avec le DIB emballé.

- Dans la deuxième version, il `GlobalAlloc` n’est pas nécessaire d’appeler pour allouer la mémoire pour le DIB emballé.

Un DIB emballé se `BITMAPINFO` compose d’une structure de données immédiatement suivie par la gamme d’octets qui définit les pixels de la bitmap. Bitmaps utilisés comme modèles de remplissage doit être de 8 pixels par 8 pixels. Si la bitmap est plus grande, Windows crée un modèle de remplissage en utilisant uniquement les bits correspondant aux 8 premières rangées et 8 colonnes de pixels dans le coin supérieur gauche de la bitmap.

Lorsqu’une application sélectionne un pinceau bicolore de modèle DIB dans un contexte d’appareil monochrome, Windows ignore les couleurs spécifiées dans le DIB et affiche plutôt le pinceau de modèle en utilisant le texte actuel et les couleurs de fond du contexte de l’appareil. Pixels cartographiés à la première couleur (à décalage 0 dans la table couleur DIB) de la DIB sont affichés en utilisant la couleur du texte. Pixels cartographiés à la deuxième couleur (à décalage 1 dans la table de couleur) sont affichés en utilisant la couleur de fond.

Pour plus d’informations sur l’utilisation des fonctions Windows suivantes, voir le SDK Windows :

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Cette fonction n’est fournie que pour la compatibilité avec les applications `CreateDIBPatternBrushPt` écrites pour les versions de Windows plus tôt que 3.0; utilisez la fonction.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Cette fonction doit être utilisée pour les applications basées sur Win32.)

- [GlobalAlloc GlobalAlloc (en)](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CréerHatchBrush

Initialise une brosse avec le motif et la couleur éclos spécifiés.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie le style d’écoutille de la brosse. Il peut s’agir de l’une des valeurs suivantes :

- HS_BDIAGONAL éclose vers le bas (de gauche à droite) à 45 degrés

- HS_CROSS crosshatch horizontal et vertical

- HS_DIAGCROSS Crosshatch à 45 degrés

- HS_FDIAGONAL’écoutille ascendante (de gauche à droite) à 45 degrés

- HS_HORIZONTAL trappe horizontale

- HS_VERTICAL Trappe verticale

*crColor (en)*<br/>
Specifie la couleur de premier plan de la brosse comme une couleur RGB (la couleur des écoutilles). Voir [COLORREF](/windows/win32/gdi/colorref) dans le Windows SDK pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être choisi comme brosse actuelle pour n’importe quel contexte de périphérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush

Initialise un pinceau avec un motif spécifié par un bitmap.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*pBitmap (en)*<br/>
Identifie un bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné pour n’importe quel contexte d’appareil qui prend en charge les opérations de raster. Le bitmap identifié par *pBitmap* est généralement initialisé en utilisant le [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), ou [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) fonction.

Bitmaps utilisés comme modèles de remplissage doit être de 8 pixels par 8 pixels. Si la bitmap est plus grande, Windows n’utilisera que les bits correspondant aux 8 premières rangées et colonnes de pixels dans le coin supérieur gauche de la bitmap.

Une brosse à motifs peut être supprimée sans affecter la bitmap associée. Cela signifie que la bitmap peut être utilisée pour créer n’importe quel nombre de brosses à motifs.

Un pinceau créé à l’aide d’une bitmap monochrome (1 plan couleur, 1 bit par pixel) est dessiné à l’aide du texte actuel et des couleurs de fond. Pixels représentés par un peu réglé à 0 sont dessinés avec la couleur de texte actuelle. Pixels représentés par un peu réglé à 1 sont dessinés avec la couleur de fond actuelle.

Pour plus d’informations sur l’utilisation [de CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), une fonction Windows, voir le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CréerSolidBrush

Initialise un pinceau avec une couleur solide spécifiée.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Paramètres

*crColor (en)*<br/>
Une structure [COLORREF](/windows/win32/gdi/colorref) qui spécifie la couleur du pinceau. La couleur spécifie une valeur RGB et peut être construite avec la macro RGB dans WINDOWS. H.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être choisi comme brosse actuelle pour n’importe quel contexte de périphérique.

Lorsqu’une application a fini `CreateSolidBrush`d’utiliser la brosse créée par, elle doit sélectionner la brosse hors du contexte de l’appareil.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CBrush:CBrush](#cbrush).

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush

Initialise une couleur de pinceau.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie un index de couleur. Cette valeur correspond à la couleur utilisée pour peindre l’un des 21 éléments de fenêtre. Consultez [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) dans windows SDK pour une liste de valeurs.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être choisi comme brosse actuelle pour n’importe quel contexte de périphérique.

Lorsqu’une application a fini `CreateSysColorBrush`d’utiliser la brosse créée par, elle doit sélectionner la brosse hors du contexte de l’appareil.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::DeHandle

Retourne un pointeur à un `CBrush` objet lorsqu’on lui donne une poignée sur un objet Windows [HBRUSH.](#operator_hbrush)

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Paramètres

*hBrush (en)*<br/>
HANDLE à un pinceau Windows GDI.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CBrush` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CBrush` un objet n’est pas déjà `CBrush` attaché à la poignée, un objet temporaire est créé et attaché. Cet `CBrush` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a du temps d’inactivité dans sa boucle d’événement. À l’heure actuelle, tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CBrush:CBrush](#cbrush).

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush

Appelez cette fonction de `LOGBRUSH` membre pour récupérer la structure.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Paramètres

*pLogBrush (en)*<br/>
Indique une structure [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur le pinceau.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, et *pLogBrush* est un pointeur valide, la valeur de retour est le nombre d’octets stockés dans le tampon.

Si la fonction réussit, et *pLogBrush* est NULL, la valeur de retour est le nombre d’octets requis pour détenir les informations que la fonction stockerait dans le tampon.

Si la fonction échoue, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

La `LOGBRUSH` structure définit le style, la couleur et le motif d’un pinceau.

Par exemple, `GetLogBrush` appelez pour correspondre à la couleur ou au motif particulier d’une bitmap.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::opérateur HBRUSH

Utilisez cet opérateur pour obtenir la poignée `CBrush` Windows GDI attachée de l’objet.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée à `CBrush` l’objet GDI Windows représenté par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HBRUSH.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
