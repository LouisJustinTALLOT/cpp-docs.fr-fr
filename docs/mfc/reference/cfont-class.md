---
title: CFont, classe
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
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866605"
---
# <a name="cfont-class"></a>CFont, classe

Encapsule une police GDI (Graphics Device Interface) Windows et fournit des fonctions membres pour la manipuler.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CFont :: CFont](#cfont)|Construit un objet `CFont`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CFont :: CreateFont](#createfont)|Initialise une `CFont` avec les caractéristiques spécifiées.|
|[CFont :: CreateFontIndirect](#createfontindirect)|Initialise un objet `CFont` avec les caractéristiques fournies dans une structure `LOGFONT`.|
|[CFont :: CreatePointFont](#createpointfont)|Initialise une `CFont` avec la hauteur spécifiée, mesurée en dixièmes de point, et de police.|
|[CFont :: CreatePointFontIndirect](#createpointfontindirect)|Identique à `CreateFontIndirect` sauf que la hauteur de police est mesurée en dixièmes d’un point plutôt qu’en unités logiques.|
|[CFont :: FromHandle](#fromhandle)|Retourne un pointeur vers un objet `CFont` lorsqu’un HFONT Windows est fourni.|
|[CFont :: GetLogFont](#getlogfont)|Remplit un `LOGFONT` avec des informations sur la police logique attachée à l’objet `CFont`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[CFont :: Operator HFONT](#operator_hfont)|Retourne le handle de police GDI Windows attaché à l’objet `CFont`.|

## <a name="remarks"></a>Notes

Pour utiliser un objet `CFont`, construisez un objet `CFont` et attachez-y une police Windows avec [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)ou [CreatePointFontIndirect](#createpointfontindirect), puis utilisez les fonctions membres de l’objet pour manipuler la police.

Les fonctions `CreatePointFont` et `CreatePointFontIndirect` sont souvent plus faciles à utiliser que `CreateFont` ou `CreateFontIndirect`, car elles effectuent automatiquement la conversion de la hauteur de la police d’une taille de point en unités logiques.

Pour plus d’informations sur les `CFont`, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cfont"></a>CFont :: CFont

Construit un objet `CFont`.

```
CFont();
```

### <a name="remarks"></a>Notes

L’objet obtenu doit être initialisé avec `CreateFont`, `CreateFontIndirect`, `CreatePointFont`ou `CreatePointFontIndirect` avant de pouvoir être utilisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont :: CreateFont

Initialise un objet `CFont` avec les caractéristiques spécifiées.

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

*nHeight*<br/>
Spécifie la hauteur souhaitée (en unités logiques) de la police. Pour obtenir une description, consultez le membre `lfHeight` de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)dans le SDK Windows. La valeur absolue de *nHeight* ne doit pas dépasser 16 384 unités de périphérique après sa conversion. Pour toutes les comparaisons de hauteur, le mappeur de polices recherche la plus grande police qui ne dépasse pas la taille demandée ou la plus petite police si toutes les polices dépassent la taille demandée.

*nWidth*<br/>
Spécifie la largeur moyenne (en unités logiques) des caractères de la police. Si *nWidth* est égal à 0, les proportions de l’appareil sont mises en correspondance avec les proportions de numérisation des polices disponibles pour trouver la correspondance la plus proche, qui est déterminée par la valeur absolue de la différence.

*nEscapement*<br/>
Spécifie l’angle (en unités de 0,1 degrés) entre le vecteur d’échappement et l’axe des abscisses de la surface d’affichage. Le vecteur d’échappement est la ligne de l’origine du premier et du dernier caractère d’une ligne. L’angle est mesuré dans le sens inverse des aiguilles d’une position à partir de l’axe x. Pour plus d’informations, consultez le membre `lfEscapement` dans la structure `LOGFONT` du SDK Windows.

*nOrientation*<br/>
Spécifie l’angle (en unités de 0,1 degrés) entre la ligne de base d’un caractère et l’axe des x. L’angle est mesuré dans le sens inverse des aiguilles d’une montre à partir de l’axe x pour les systèmes de coordonnées dans lesquels le sens y est bas et dans le sens des aiguilles d’une montre à partir de l’axe x pour les systèmes de coordonnées dans lesquels l’axe y est en position.

*nWeight*<br/>
Spécifie l’épaisseur de la police (en pixels manuscrits par 1000). Pour plus d’informations, consultez le membre *lfWeight* dans la structure `LOGFONT` de la SDK Windows. Les valeurs décrites sont approximatives ; l’apparence réelle dépend de la police. Certaines polices ont uniquement des poids FW_NORMAL, FW_REGULAR et FW_BOLD. Si FW_DONTCARE est spécifié, une pondération par défaut est utilisée.

*bItalic*<br/>
Spécifie si la police est en italique.

*bUnderline*<br/>
Spécifie si la police est soulignée.

*cStrikeOut*<br/>
Spécifie si les caractères de la police sont barrés. Spécifie une police barré si sa valeur est différente de zéro.

*nCharSet*<br/>
Spécifie les jeux de caractères de la police que le membre `lfCharSet` dans la structure `LOGFONT` dans la SDK Windows pour obtenir une liste de valeurs.

Le jeu de caractères OEM est dépendant du système.

Des polices avec d’autres jeux de caractères peuvent exister dans le système. Une application qui utilise une police avec un jeu de caractères inconnu ne doit pas tenter de traduire ou d’interpréter les chaînes qui doivent être rendues avec cette police. Au lieu de cela, les chaînes doivent être transmises directement au pilote de périphérique de sortie.

Le mappeur de polices n’utilise pas la valeur DEFAULT_CHARSET. Une application peut utiliser cette valeur pour autoriser le nom et la taille d’une police à décrire entièrement la police logique. Si une police portant le nom spécifié n’existe pas, une police de n’importe quel jeu de caractères peut être substituée à la police spécifiée. Pour éviter des résultats inattendus, les applications doivent utiliser la valeur DEFAULT_CHARSET avec modération.

*nOutPrecision*<br/>
Spécifie la précision de sortie souhaitée. La précision de sortie définit la précision avec laquelle la sortie doit correspondre à la hauteur, à la largeur, à l’orientation des caractères, à l’échappement et au pas de la police demandée. Pour obtenir la liste des valeurs et plus d’informations, consultez le membre `lfOutPrecision` dans la structure `LOGFONT` du SDK Windows.

*nClipPrecision*<br/>
Spécifie la précision de découpage souhaitée. La précision du découpage définit comment découper les caractères qui se trouvent partiellement à l’extérieur de la zone de découpage. Pour obtenir la liste des valeurs, consultez le membre `lfClipPrecision` dans la structure `LOGFONT` du SDK Windows.

Pour utiliser une police en lecture seule incorporée, une application doit spécifier CLIP_ENCAPSULATE.

Pour obtenir une rotation cohérente des polices d’appareil, TrueType et vectorielles, une application peut utiliser l’opérateur OR pour combiner la valeur CLIP_LH_ANGLES avec l’une des autres valeurs *nClipPrecision* . Si le bit de CLIP_LH_ANGLES est défini, la rotation de toutes les polices varie selon que l’orientation du système de coordonnées est gauche ou droite. (Pour plus d’informations sur l’orientation des systèmes de coordonnées, consultez la description du paramètre *nOrientation* .) Si CLIP_LH_ANGLES n’est pas défini, les polices d’appareil pivotent toujours dans le sens inverse des aiguilles d’une autre, mais la rotation des autres polices dépend de l’orientation du système de coordonnées.

*nQuality*<br/>
Spécifie la qualité de sortie de la police, qui définit la précision avec laquelle l’GDI doit tenter de faire correspondre les attributs de police logique à ceux d’une police physique réelle. Pour obtenir la liste des valeurs, consultez le membre `lfQuality` dans la structure `LOGFONT` du SDK Windows.

*nPitchAndFamily*<br/>
Spécifie le pas et la famille de la police Pour obtenir la liste des valeurs et plus d’informations, consultez le membre `lfPitchAndFamily` dans la structure `LOGFONT` du SDK Windows.

*lpszFacename*<br/>
`CString` ou pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de la police de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. La fonction [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) de Windows peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFacename* a la valeur null, le GDI utilise une police indépendante du périphérique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut être sélectionnée par la suite en tant que police pour tout contexte de périphérique.

La fonction `CreateFont` ne crée pas de police GDI Windows. Il sélectionne simplement la correspondance la plus proche parmi les polices physiques disponibles pour le GDI.

Les applications peuvent utiliser les paramètres par défaut pour la plupart des paramètres lors de la création d’une police logique. Les paramètres qui doivent toujours recevoir des valeurs spécifiques sont *nHeight* et *lpszFacename*. Si *nHeight* et *lpszFacename* ne sont pas définis par l’application, la police logique qui est créée dépend de l’appareil.

Lorsque vous avez terminé avec l’objet `CFont` créé par la fonction `CreateFont`, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez l’objet `CFont` qui n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont :: CreateFontIndirect

Initialise un objet `CFont` avec les caractéristiques fournies dans une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw).

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Pointe vers une structure de `LOGFONT` qui définit les caractéristiques de la police logique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut être sélectionnée par la suite en tant que police actuelle pour n’importe quel appareil.

Cette police a les caractéristiques spécifiées dans la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) . Lorsque la police est sélectionnée à l’aide de la fonction membre [CDC :: SelectObject](../../mfc/reference/cdc-class.md#selectobject) , le mappeur de polices GDI tente de faire correspondre la police logique avec une police physique existante. Si le mappeur de polices ne parvient pas à trouver une correspondance exacte pour la police logique, il fournit une police alternative dont les caractéristiques correspondent autant de caractéristiques demandées que possible.

Lorsque vous n’avez plus besoin de l’objet `CFont` créé par la fonction `CreateFontIndirect`, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez l’objet `CFont` qui n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>CFont :: CreatePointFont

Cette fonction fournit un moyen simple de créer une police d’une taille de police et de point spécifiée.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*nPointSize*<br/>
Hauteur de police demandée en dixièmes de point. (Par exemple, vous pouvez passer 120 pour demander une police à 12 points.)

*lpszFaceName*<br/>
`CString` ou pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de la police de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. La fonction EnumFontFamilies de Windows peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFaceName* a la valeur null, le GDI utilise une police indépendante du périphérique.

*pDC*<br/>
Pointeur vers l’objet [CDC](../../mfc/reference/cdc-class.md) à utiliser pour convertir la hauteur de *nPointSize* en unités logiques. Si la valeur est NULL, un contexte de périphérique d’écran est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Il convertit automatiquement la hauteur de *nPointSize* en unités logiques à l’aide de l’objet CDC désigné par *PDC*.

Lorsque vous avez terminé avec l’objet `CFont` créé par la fonction `CreatePointFont`, commencez par sélectionner la police hors du contexte de périphérique, puis supprimez l’objet `CFont`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>CFont :: CreatePointFontIndirect

Cette fonction est identique à [CreateFontIndirect](#createfontindirect) , à ceci près que le `lfHeight` membre du `LOGFONT` est interprété en dixièmes de point plutôt qu’en unités de périphérique.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Pointe vers une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui définit les caractéristiques de la police logique. Le `lfHeight` membre de la structure `LOGFONT` est mesuré en dixièmes d’un point plutôt que d’unités logiques. (Par exemple, définissez `lfHeight` sur 120 pour demander une police à 12 points.)

*pDC*<br/>
Pointeur vers l’objet [CDC](../../mfc/reference/cdc-class.md) à utiliser pour convertir la hauteur de `lfHeight` en unités logiques. Si la valeur est NULL, un contexte de périphérique d’écran est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Cette fonction convertit automatiquement la hauteur de `lfHeight` en unités logiques à l’aide de l’objet CDC désigné par *PDC* avant de passer la structure `LOGFONT` sur Windows.

Lorsque vous avez terminé avec l’objet `CFont` créé par la fonction `CreatePointFontIndirect`, commencez par sélectionner la police hors du contexte de périphérique, puis supprimez l’objet `CFont`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont :: FromHandle

Retourne un pointeur vers un objet `CFont` lorsqu’un handle HFONT est fourni à un objet de police Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Handle HFONT à une police Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CFont` en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Si un objet `CFont` n’est pas déjà attaché au handle, un objet `CFont` temporaire est créé et attaché. Cet objet `CFont` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire est valide uniquement pendant le traitement d’un message de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont :: GetLogFont

Appelez cette fonction pour récupérer une copie de la structure `LOGFONT` pour `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Paramètres

*pLogFont*<br/>
Pointeur vers la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) pour recevoir les informations sur la police.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction est réussie, sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>CFont :: Operator HFONT

Utilisez cet opérateur pour récupérer le handle GDI Windows de la police attachée à l’objet `CFont`.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valeur de retour

Handle de l’objet de police GDI Windows attaché à `CFont` en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Étant donné que cet opérateur est utilisé automatiquement pour les conversions de `CFont` en [polices et texte](/windows/win32/gdi/fonts-and-text), vous pouvez passer des objets `CFont` à des fonctions qui attendent HFONTs.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
