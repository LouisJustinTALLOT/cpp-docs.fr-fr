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
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507433"
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
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Initialise un pinceau avec le style, la couleur et le modèle spécifiés dans une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Initialise un pinceau avec un modèle spécifié par une bitmap indépendante du périphérique (DIB, Device-Independent Bitmap).|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Initialise un pinceau avec le modèle hachuré et la couleur spécifiés.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Initialise un pinceau avec un modèle spécifié par une bitmap.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Initialise un pinceau avec la couleur unie spécifiée.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crée un pinceau qui est la couleur système par défaut.|
|[CBrush::FromHandle](#fromhandle)|Retourne un pointeur vers un `CBrush` objet en fonction d’un handle vers un `HBRUSH` objet Windows.|
|[CBrush::GetLogBrush](#getlogbrush)|Obtient une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBrush:: Operator HBRUSH](#operator_hbrush)|Retourne le handle Windows attaché à l' `CBrush` objet.|

## <a name="remarks"></a>Notes

Pour utiliser un `CBrush` objet, construisez `CBrush` un objet `CDC` et transmettez-le à une fonction membre qui requiert un pinceau.

Les pinceaux peuvent être pleins, hachurés ou à motif.

Pour plus d’informations `CBrush`sur, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

Construit un objet `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*crColor*<br/>
Spécifie la couleur de premier plan du pinceau sous forme de couleur RVB. Si le pinceau est hachuré, ce paramètre spécifie la couleur du hachurage.

*nIndex*<br/>
Spécifie le style de hachurage du pinceau. Il peut s’agir de l’une des valeurs suivantes:

- HS_BDIAGONAL hachuré vers le bas (de gauche à droite) à 45 degrés

- Hachurage horizontale et verticale HS_CROSS

- Hachurage HS_DIAGCROSS à 45 degrés

- HS_FDIAGONAL hachuré vers le haut (de gauche à droite) à 45 degrés

- Hachure horizontale HS_HORIZONTAL

- Hachure verticale HS_VERTICAL

*pBitmap*<br/>
Pointe vers un `CBitmap` objet qui spécifie une image bitmap avec laquelle le pinceau peint.

### <a name="remarks"></a>Notes

`CBrush`a quatre constructeurs surchargés. Le constructeur sans argument construit un `CBrush` objet non initialisé qui doit être initialisé avant de pouvoir être utilisé.

Si vous utilisez le constructeur sans arguments, vous devez initialiser l’objet résultant `CBrush` avec [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)ou [ CreateDIBPatternBrush](#createdibpatternbrush). Si vous utilisez l’un des constructeurs qui prend des arguments, aucune initialisation supplémentaire n’est nécessaire. Les constructeurs avec des arguments peuvent lever une exception si des erreurs sont rencontrées, alors que le constructeur sans arguments échoue toujours.

Le constructeur avec un seul paramètre [COLORREF](/windows/win32/gdi/colorref) construit un pinceau plein avec la couleur spécifiée. La couleur spécifie une valeur RVB et peut être construite avec la macro RGB dans WINDOWS. Manutention.

Le constructeur avec deux paramètres construit un pinceau hachuré. Le paramètre *nIndex* spécifie l’index d’un modèle hachuré. Le paramètre *crColor* spécifie la couleur.

Le constructeur avec un `CBitmap` paramètre construit un pinceau à motif. Le paramètre identifie une image bitmap. La bitmap est supposée avoir été créée à l’aide de [CBitmap:: CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)ou [CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). La taille minimale d’une image bitmap à utiliser dans un motif de remplissage est de 8 pixels par 8 pixels.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

Initialise un pinceau avec un style, une couleur et un modèle spécifiés dans une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) .

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Paramètres

*lpLogBrush*<br/>
Pointe vers une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur le pinceau.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné comme pinceau actuel pour tout contexte de périphérique.

Un pinceau créé à l’aide d’une image bitmap monochrome (1 plan, 1 bit par pixel) est dessiné à l’aide des couleurs de texte et d’arrière-plan actuelles. Les pixels représentés par un bit défini sur 0 seront dessinés avec la couleur de texte actuelle. Les pixels représentés par un bit défini sur 1 sont dessinés avec la couleur d’arrière-plan actuelle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

Initialise un pinceau avec le modèle spécifié par une bitmap indépendante du périphérique (DIB, Device-Independent Bitmap).

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
Identifie un objet de mémoire globale qui contient une image bitmap indépendante du périphérique (DIB) compressée.

*nUsage*<br/>
Spécifie si `bmiColors[]` les champs de la structure de données [BITMAPINFO,](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (une partie du DIB compressé) contiennent des index ou des valeurs RVB explicites dans la palette logique actuellement réalisée. Le paramètre doit avoir l’une des valeurs suivantes:

- DIB_PAL_COLORS la table des couleurs se compose d’un tableau d’index 16 bits.

- DIB_RGB_COLORS la table des couleurs contient des valeurs RVB littérales.

*lpPackedDIB*<br/>
Pointe vers un DIB compressé composé d’une `BITMAPINFO` structure immédiatement suivie d’un tableau d’octets définissant les pixels de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné pour tout contexte de périphérique qui prend en charge les opérations raster.

Les deux versions diffèrent dans la façon dont vous gérez le DIB:

- Dans la première version, pour obtenir un descripteur du DIB, vous devez `GlobalAlloc` appeler la fonction Windows pour allouer un bloc de mémoire globale, puis remplir la mémoire avec le DIB compressé.

- Dans la deuxième version, il n’est pas nécessaire d' `GlobalAlloc` appeler pour allouer de la mémoire pour le DIB compressé.

Un DIB compressé se compose d' `BITMAPINFO` une structure de données immédiatement suivie du tableau d’octets qui définit les pixels de l’image bitmap. Les bitmaps utilisés comme modèles de remplissage doivent être de 8 pixels par 8 pixels. Si la bitmap est plus grande, Windows crée un motif de remplissage en utilisant uniquement les bits correspondant aux 8 premières lignes et 8 colonnes de pixels dans le coin supérieur gauche de l’image bitmap.

Quand une application sélectionne un pinceau de modèle DIB à deux couleurs dans un contexte de périphérique monochrome, Windows ignore les couleurs spécifiées dans le DIB et affiche à la place le pinceau de motif en utilisant le texte actuel et les couleurs d’arrière-plan du contexte de périphérique. Les pixels mappés à la première couleur (au décalage 0 dans la table des couleurs DIB) du DIB s’affichent à l’aide de la couleur du texte. Les pixels mappés à la deuxième couleur (au décalage 1 dans la table des couleurs) sont affichés à l’aide de la couleur d’arrière-plan.

Pour plus d’informations sur l’utilisation des fonctions Windows suivantes, consultez la SDK Windows:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Cette fonction est fournie uniquement pour la compatibilité avec les applications écrites pour les versions de Windows antérieures à 3,0 `CreateDIBPatternBrushPt` ; utilisez la fonction.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Cette fonction doit être utilisée pour les applications Win32.)

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

Initialise un pinceau avec le modèle hachuré et la couleur spécifiés.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie le style de hachurage du pinceau. Il peut s’agir de l’une des valeurs suivantes:

- HS_BDIAGONAL hachuré vers le bas (de gauche à droite) à 45 degrés

- Hachurage horizontale et verticale HS_CROSS

- Hachurage HS_DIAGCROSS à 45 degrés

- HS_FDIAGONAL hachuré vers le haut (de gauche à droite) à 45 degrés

- Hachure horizontale HS_HORIZONTAL

- Hachure verticale HS_VERTICAL

*crColor*<br/>
Spécifie la couleur de premier plan du pinceau sous la forme d’une couleur RVB (la couleur des hachures). Pour plus d’informations, consultez [COLORREF](/windows/win32/gdi/colorref) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné comme pinceau actuel pour tout contexte de périphérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

Initialise un pinceau avec un modèle spécifié par une bitmap.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*pBitmap*<br/>
Identifie une image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné pour tout contexte de périphérique qui prend en charge les opérations raster. La bitmap identifiée par *pBitmap* est généralement initialisée à l’aide de la fonction [CBitmap:: CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)ou [CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) .

Les bitmaps utilisés comme modèles de remplissage doivent être de 8 pixels par 8 pixels. Si la bitmap est plus grande, Windows utilise uniquement les bits correspondant aux 8 premières lignes et colonnes de pixels dans le coin supérieur gauche de l’image bitmap.

Vous pouvez supprimer un pinceau de motif sans affecter le bitmap associé. Cela signifie que l’image bitmap peut être utilisée pour créer un nombre quelconque de pinceaux de modèle.

Un pinceau créé à l’aide d’une image bitmap monochrome (1 plan de couleur, 1 bit par pixel) est dessiné à l’aide du texte et des couleurs d’arrière-plan actuels. Les pixels représentés par un bit défini sur 0 sont dessinés avec la couleur de texte actuelle. Les pixels représentés par un bit défini sur 1 sont dessinés avec la couleur d’arrière-plan actuelle.

Pour plus d’informations sur l’utilisation de [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), une fonction Windows, consultez le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

Initialise un pinceau avec une couleur unie spécifiée.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Paramètres

*crColor*<br/>
Structure [COLORREF](/windows/win32/gdi/colorref) qui spécifie la couleur du pinceau. La couleur spécifie une valeur RVB et peut être construite avec la macro RGB dans WINDOWS. Manutention.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné comme pinceau actuel pour tout contexte de périphérique.

Quand une application a fini d’utiliser le pinceau créé `CreateSolidBrush`par, elle doit sélectionner le pinceau en dehors du contexte de périphérique.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CBrush:: CBrush](#cbrush).

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

Initialise une couleur de pinceau.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie un index de couleurs. Cette valeur correspond à la couleur utilisée pour peindre l’un des éléments de la fenêtre 21. Pour obtenir la liste des valeurs, consultez [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le pinceau peut ensuite être sélectionné comme pinceau actuel pour tout contexte de périphérique.

Quand une application a fini d’utiliser le pinceau créé `CreateSysColorBrush`par, elle doit sélectionner le pinceau en dehors du contexte de périphérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

Retourne un pointeur vers un `CBrush` objet lorsqu’un handle est fourni à un objet Windows [HBRUSH](#operator_hbrush) .

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Paramètres

*hBrush*<br/>
HANDLE vers un pinceau Windows GDI.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CBrush` objet en cas de réussite; sinon, null.

### <a name="remarks"></a>Notes

Si un `CBrush` objet n’est pas déjà attaché au descripteur, `CBrush` un objet temporaire est créé et attaché. Cet objet `CBrush` temporaire est valide uniquement jusqu’à la prochaine heure d’inactivité de l’application dans sa boucle d’événements. À ce stade, tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire est valide uniquement pendant le traitement d’un message de fenêtre.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CBrush:: CBrush](#cbrush).

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

Appelez cette fonction membre pour récupérer la `LOGBRUSH` structure.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Paramètres

*pLogBrush*<br/>
Pointe vers une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur le pinceau.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie et que *pLogBrush* est un pointeur valide, la valeur de retour est le nombre d’octets stockés dans la mémoire tampon.

Si la fonction est réussie et que *pLogBrush* a la valeur null, la valeur de retour est le nombre d’octets requis pour contenir les informations que la fonction stocke dans la mémoire tampon.

Si la fonction échoue, la valeur de retour est 0.

### <a name="remarks"></a>Notes

La `LOGBRUSH` structure définit le style, la couleur et le motif d’un pinceau.

Par exemple, appelez `GetLogBrush` pour mettre en correspondance la couleur ou le motif particulier d’une image bitmap.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush:: Operator HBRUSH

Utilisez cet opérateur pour récupérer le handle Windows GDI attaché de l' `CBrush` objet.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers l’objet Windows GDI représenté par `CBrush` l’objet; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HBRUSH.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CBitmap, classe](../../mfc/reference/cbitmap-class.md)<br/>
[CDC, classe](../../mfc/reference/cdc-class.md)
