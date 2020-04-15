---
title: Classe CFont
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373842"
---
# <a name="cfont-class"></a>Classe CFont

Encapsule une police GDI (Graphics Device Interface) Windows et fournit des fonctions membres pour la manipuler.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFont::CFont](#cfont)|Construit un objet `CFont`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Initialise a `CFont` avec les caractéristiques spécifiées.|
|[CFont::CreateFontIndirect](#createfontindirect)|Initialise un `CFont` objet avec les `LOGFONT` caractéristiques données dans une structure.|
|[CFont::CreatePointFont](#createpointfont)|Initialise un `CFont` avec la hauteur spécifiée, mesurée en dixièmes de point, et la police de caractères.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Idem, `CreateFontIndirect` sauf que la hauteur de la police est mesurée en dixièmes de point plutôt qu’en unités logiques.|
|[CFont::DeHandle](#fromhandle)|Retourne un pointeur vers un `CFont` objet lorsqu’on lui donne un Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Remplit une `LOGFONT` information sur la police `CFont` logique attachée à l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFont::opérateur HFONT](#operator_hfont)|Retourne la poignée de police `CFont` Windows GDI attachée à l’objet.|

## <a name="remarks"></a>Notes

Pour utiliser `CFont` un objet, construire `CFont` un objet et y attacher une police Windows avec [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), ou [CreatePointFontIndirect](#createpointfontindirect), puis utiliser les fonctions du membre de l’objet pour manipuler la police.

Les `CreatePointFont` `CreatePointFontIndirect` fonctions et les fonctions sont souvent plus faciles à utiliser que `CreateFont` ou `CreateFontIndirect` puisqu’ils font la conversion pour la hauteur de la police d’une taille de point à des unités logiques automatiquement.

Pour plus `CFont`d’informations sur , voir [Objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont::CFont

Construit un objet `CFont`.

```
CFont();
```

### <a name="remarks"></a>Notes

L’objet résultant doit `CreateFont`être `CreateFontIndirect` `CreatePointFont`initialisé `CreatePointFontIndirect` avec, , , ou avant qu’il puisse être utilisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont

Initialise un `CFont` objet avec les caractéristiques spécifiées.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>Paramètres

*nHeight (en)*<br/>
Spécifie la hauteur désirée (dans les unités logiques) de la police. Consultez `lfHeight` le membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)dans le Windows SDK pour une description. La valeur absolue de *nHeight* ne doit pas dépasser 16 384 unités d’appareils après sa conversion. Pour toutes les comparaisons de hauteur, le mapper de police recherche la police la plus grande qui ne dépasse pas la taille demandée ou la plus petite police si toutes les polices dépassent la taille demandée.

*nWidth (en)*<br/>
Spécifie la largeur moyenne (en unités logiques) des caractères de la police. Si *nWidth* est de 0, le rapport d’aspect de l’appareil sera comparé au rapport d’aspect de numérisation des polices disponibles pour trouver le match le plus proche, qui est déterminé par la valeur absolue de la différence.

*nEscapement (en anglais)*<br/>
Spécifie l’angle (en unités de 0,1 degré) entre le vecteur d’évacuation et l’axe x de la surface d’affichage. Le vecteur d’évasion est la ligne à travers les origines des premiers et derniers personnages sur une ligne. L’angle est mesuré dans le sens inverse des aiguilles d’une montre à partir de l’axe x. Voir `lfEscapement` le membre `LOGFONT` dans la structure dans le Windows SDK pour plus d’informations.

*n Orientation*<br/>
Spécifie l’angle (en unités de 0,1 degré) entre la ligne de base d’un personnage et l’axe x. L’angle est mesuré dans le sens inverse des aiguilles d’une montre à partir de l’axe x pour les systèmes de coordonnées dans lesquels la direction y est vers le bas et dans le sens des aiguilles d’une montre à partir de l’axe x pour les systèmes de coordonnées dans lesquels la direction y est vers le haut.

*n Poids*<br/>
Spécifie le poids de la police (en pixels encrés pour 1000). Voir le membre *lfWeight* dans la `LOGFONT` structure dans le Windows SDK pour plus d’informations. Les valeurs décrites sont approximatives; l’apparence réelle dépend de la police de caractères. Certaines polices n’ont que des poids FW_NORMAL, FW_REGULAR et FW_BOLD. Si FW_DONTCARE est spécifiée, un poids par défaut est utilisé.

*bItalique*<br/>
Précise si la police est italique.

*bUnderline (en)*<br/>
Précise si la police est soulignée.

*cStrikeOut (en)*<br/>
Précise si les caractères de la police sont rayés. Spécifie une police de retrait si elle est réglée à une valeur non zéro.

*nCharSet (en anglais)*<br/>
Spécifie le personnage de `lfCharSet` la police `LOGFONT` setSee le membre dans la structure dans le SDK Windows pour une liste de valeurs.

L’ensemble de caractères OEM est dépendant du système.

Des polices avec d’autres ensembles de caractère peuvent exister dans le système. Une application qui utilise une police avec un ensemble de caractère inconnu ne doit pas tenter de traduire ou d’interpréter les chaînes qui doivent être rendues avec cette police. Au lieu de cela, les chaînes doivent être transmises directement au pilote du périphérique de sortie.

Le mapper de police n’utilise pas la valeur DEFAULT_CHARSET. Une application peut utiliser cette valeur pour permettre au nom et à la taille d’une police de décrire pleinement la police logique. Si une police avec le nom spécifié n’existe pas, une police de n’importe quel ensemble de caractères peut être substituée à la police spécifiée. Pour éviter des résultats inattendus, les applications doivent utiliser la valeur DEFAULT_CHARSET avec parcimonie.

*nOutPrecision*<br/>
Spécifie la précision de sortie souhaitée. La précision de sortie définit la façon dont la sortie doit correspondre à la hauteur, à la largeur, à l’orientation du personnage, à l’évasion et au lancer de la police demandée. Voir `lfOutPrecision` le membre `LOGFONT` dans la structure dans le SDK Windows pour une liste de valeurs et plus d’informations.

*nClipPrecision*<br/>
Spécifie la précision de coupure désirée. La précision de coupure définit comment couper des caractères qui sont partiellement en dehors de la région de coupure. Voir `lfClipPrecision` le membre `LOGFONT` dans la structure dans le SDK Windows pour une liste de valeurs.

Pour utiliser une police intégrée en lecture seulement, une application doit spécifier CLIP_ENCAPSULATE.

Pour atteindre une rotation cohérente de l’appareil, TrueType, et les polices vectorielles, une application peut utiliser l’opérateur DE RO pour combiner la valeur CLIP_LH_ANGLES avec l’une des autres valeurs *nClipPrecision.* Si le CLIP_LH_ANGLES bit est réglé, la rotation de toutes les polices dépend si l’orientation du système de coordonnées est gaucher ou droitier. (Pour plus d’informations sur l’orientation des systèmes de coordonnées, voir la description du *paramètre nOrientation.)* Si CLIP_LH_ANGLES n’est pas réglée, les polices d’appareil tournent toujours dans le sens inverse des aiguilles d’une montre, mais la rotation d’autres polices dépend de l’orientation du système de coordonnées.

*nQualité*<br/>
Spécifie la qualité de sortie de la police, qui définit la façon dont soigneusement le GDI doit tenter de faire correspondre les attributs logiques de la police à ceux d’une police physique réelle. Voir `lfQuality` le membre `LOGFONT` dans la structure dans le SDK Windows pour une liste de valeurs.

*nPitchAndFamily (en)*<br/>
Spécifie le pas et la famille de la police Voir `lfPitchAndFamily` le membre `LOGFONT` dans la structure dans le SDK Windows pour une liste de valeurs et plus d’informations.

*lpszFacename*<br/>
Un `CString` ou un pointeur à une chaîne non terminée qui spécifie le nom de police de la police. La longueur de cette corde ne doit pas dépasser 30 caractères. La fonction Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFacename* est NULL, le GDI utilise une police de caractères indépendante de l’appareil.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut ensuite être sélectionnée comme police pour n’importe quel contexte de périphérique.

La `CreateFont` fonction ne crée pas une nouvelle police Windows GDI. Il sélectionne simplement le match le plus proche des polices physiques disponibles au GDI.

Les applications peuvent utiliser les paramètres par défaut pour la plupart des paramètres lors de la création d’une police logique. Les paramètres qui doivent toujours être donnés des valeurs spécifiques sont *nHeight* et *lpszFacename*. Si *nHeight* et *lpszFacename* ne sont pas définis par l’application, la police logique qui est créée est dépendante de l’appareil.

Lorsque vous terminez `CFont` avec `CreateFont` l’objet `CDC::SelectObject` créé par la fonction, utilisez-le `CFont` pour sélectionner une police différente dans le contexte de l’appareil, puis supprimez l’objet qui n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::CreateFontIndirect

Initialise un `CFont` objet avec les caractéristiques données dans une structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Indique une `LOGFONT` structure qui définit les caractéristiques de la police logique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut ensuite être sélectionnée comme police actuelle pour n’importe quel appareil.

Cette police a les caractéristiques spécifiées dans la structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) Lorsque la police est sélectionnée en utilisant la fonction de membre [CDC::SelectObject,](../../mfc/reference/cdc-class.md#selectobject) le mapper de police GDI tente de faire correspondre la police logique avec une police physique existante. Si le mapper de police ne trouve pas une correspondance exacte pour la police logique, il fournit une police alternative dont les caractéristiques correspondent autant de caractéristiques demandées que possible.

Lorsque vous n’avez plus besoin de `CFont` l’objet créé par la `CreateFontIndirect` fonction, utilisez-le `CDC::SelectObject` pour sélectionner une police différente dans le contexte de l’appareil, puis supprimez l’objet `CFont` qui n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont

Cette fonction fournit un moyen simple de créer une police d’une police spécifiée police et la taille de point.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*nPointSize (en)*<br/>
Hauteur de police demandée en dixièmes de point. (Par exemple, passez 120 pour demander une police de 12 points.)

*lpszFaceName (en)*<br/>
Un `CString` ou un pointeur à une chaîne non terminée qui spécifie le nom de police de la police. La longueur de cette corde ne doit pas dépasser 30 caractères. La fonction Windows 'EnumFontFamilies peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFaceName* est NULL, le GDI utilise une police de caractères indépendante de l’appareil.

*pDC*<br/>
Pointeur à l’objet [CDC](../../mfc/reference/cdc-class.md) à utiliser pour convertir la hauteur en *nPointSize* en unités logiques. Si NULL, un contexte d’appareil d’écran est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, sinon 0.

### <a name="remarks"></a>Notes

Il convertit automatiquement la hauteur en *nPointSize* en unités logiques à l’aide de l’objet CDC pointé par *pDC*.

Lorsque vous terminez avec `CFont` `CreatePointFont` l’objet créé par la fonction, sélectionnez `CFont` d’abord la police hors du contexte de l’appareil, puis supprimez l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect

Cette fonction est la même que [CreateFontIndirect,](#createfontindirect) sauf que le `lfHeight` membre de la `LOGFONT` est interprété en dixièmes de point plutôt que des unités d’appareil.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Indique une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui définit les caractéristiques de la police logique. Le `lfHeight` membre `LOGFONT` de la structure est mesuré en dixièmes de point plutôt que des unités logiques. (Par exemple, `lfHeight` définissez 120 pour demander une police de 12 points.)

*pDC*<br/>
Pointeur à l’objet [CDC](../../mfc/reference/cdc-class.md) à `lfHeight` utiliser pour convertir la hauteur en unités logiques. Si NULL, un contexte d’appareil d’écran est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, sinon 0.

### <a name="remarks"></a>Notes

Cette fonction convertit automatiquement `lfHeight` la hauteur en unités logiques à l’aide de l’objet CDC pointé par *pDC* avant de passer la `LOGFONT` structure sur Windows.

Lorsque vous terminez avec `CFont` `CreatePointFontIndirect` l’objet créé par la fonction, sélectionnez `CFont` d’abord la police hors du contexte de l’appareil, puis supprimez l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont::DeHandle

Retourne un pointeur à un `CFont` objet lorsqu’on lui donne une poignée HFONT à un objet de police GDI Windows.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Une poignée HFONT à une police Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFont` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CFont` un objet n’est pas déjà `CFont` attaché à la poignée, un objet temporaire est créé et attaché. Cet `CFont` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. Une autre façon de dire cela est que l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont

Appelez cette fonction pour récupérer `LOGFONT` une `CFont`copie de la structure pour .

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Paramètres

*pLogFont*<br/>
Pointeur vers la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) pour recevoir les informations de police.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction réussit, sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::opérateur HFONT

Utilisez cet opérateur pour obtenir la poignée De `CFont` Windows GDI de la police attachée à l’objet.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valeur de retour

La poignée de l’objet de `CFont` police Windows GDI attaché à en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Étant donné que cet opérateur `CFont` est automatiquement utilisé pour les `CFont` conversions de [Fonts et Text](/windows/win32/gdi/fonts-and-text), vous pouvez passer des objets à des fonctions qui attendent HFONTs.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
