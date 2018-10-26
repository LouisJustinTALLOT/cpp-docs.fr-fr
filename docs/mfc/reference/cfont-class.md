---
title: CFont, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c914bab9ab7a4bb15f6fe3d2820d7ff2534c3c6e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053641"
---
# <a name="cfont-class"></a>CFont (classe)

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
|[CFont::CreateFont n'](#createfont)|Initialise un `CFont` avec les caractéristiques spécifiées.|
|[CFont::CreateFontIndirect](#createfontindirect)|Initialise un `CFont` objet avec les caractéristiques donné dans un `LOGFONT` structure.|
|[CFont::CreatePointFont](#createpointfont)|Initialise un `CFont` avec la hauteur spécifiée, mesurée en dixièmes de point et de police.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Identique à `CreateFontIndirect` , à ceci près que la hauteur de police est mesurée en dixièmes d’un point plutôt qu’en unités logiques.|
|[CFont::FromHandle](#fromhandle)|Retourne un pointeur vers un `CFont` en fonction d’un HFONT Windows de l’objet.|
|[CFont::GetLogFont](#getlogfont)|Remplit un `LOGFONT` avec des informations sur la police logique attachée à la `CFont` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|Retourne le handle de la police Windows GDI attaché à la `CFont` objet.|

## <a name="remarks"></a>Notes

Pour utiliser un `CFont` de l’objet, construisez un `CFont` de l’objet et d’attachement d’une police Windows à l’aide de [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), ou [CreatePointFontIndirect](#createpointfontindirect), puis utilisez les fonctions membres de l’objet pour manipuler la police.

Le `CreatePointFont` et `CreatePointFontIndirect` fonctions sont souvent plus faciles à utiliser que `CreateFont` ou `CreateFontIndirect` dans la mesure où ils ne la conversion pour la hauteur de la police à partir d’une taille de point d’unités logiques automatiquement.

Pour plus d’informations sur `CFont`, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cfont"></a>  CFont::CFont

Construit un objet `CFont`.

```
CFont();
```

### <a name="remarks"></a>Notes

L’objet obtenu doit être initialisée avec `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, ou `CreatePointFontIndirect` avant de pouvoir être utilisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>  CFont::CreateFont n'

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

*nHeight*<br/>
Spécifie la hauteur souhaitée (en unités logiques) de la police. Consultez le `lfHeight` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)structure dans le SDK Windows pour obtenir une description. La valeur absolue de *nHeight* ne doit pas dépasser 16 384 unités de périphérique après qu’il est converti. Pour toutes les comparaisons de hauteur, le mappeur de polices recherche la plus grande police qui ne dépasse pas la taille demandée ou la plus petite police si toutes les polices dépassent la taille demandée.

*nWidth*<br/>
Spécifie la largeur moyenne (en unités logiques) de caractères dans la police. Si *nWidth* est 0, les proportions de l’appareil sera comparée aux proportions de numérisation des polices disponibles pour trouver la correspondance la plus proche, qui est déterminée par la valeur absolue de la différence.

*nEscapement*<br/>
Spécifie l’angle (en unités de degrés de 0,1) entre le vecteur d’échappement et l’axe des abscisses de la surface d’affichage. Le vecteur d’échappement est la ligne via les origines des premier et derniers caractères sur une ligne. L’angle est mesuré dans le sens anti-horaire à partir de l’axe des abscisses. Consultez le `lfEscapement` membre dans le `LOGFONT` structure dans le SDK Windows pour plus d’informations.

*nOrientation*<br/>
Spécifie l’angle (en unités de degrés de 0,1) entre la ligne de base d’un caractère et l’axe des abscisses. L’angle est mesuré dans le sens anti-horaire à partir de l’axe des x pour les systèmes de coordonnées dans lequel l’axe y est hors service et dans le sens horaire à partir de l’axe des x pour les systèmes de coordonnées dans lequel est l’axe y.

*nWeight*<br/>
Spécifie l’épaisseur de police (en pixels ancrés par 1 000). Consultez le *lfWeight* membre dans le `LOGFONT` structure dans le SDK Windows pour plus d’informations. Les valeurs décrites sont approximatives ; l’apparence réelle varie selon le type de caractères. Certaines polices ont des uniquement les pondérations FW_NORMAL, FW_REGULAR et FW_BOLD. Si FW_DONTCARE est spécifié, une pondération par défaut est utilisée.

*bItalic*<br/>
Spécifie si la police est italique.

*bUnderline*<br/>
Spécifie si la police est soulignée.

*cStrikeOut*<br/>
Spécifie si les caractères de la police sont barrées. Spécifie une police barrée si défini sur une valeur différente de zéro.

*nCharSet*<br/>
Spécifie les setSee de caractère de la police le `lfCharSet` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.

Le jeu de caractères OEM est dépendante du système.

Polices avec les autres jeux de caractères peuvent exister dans le système. Une application qui utilise une police avec un jeu de caractères inconnu ne doit pas tenter de traduire ou l’interprétation des chaînes qui doivent être restitués avec cette police. Au lieu de cela, les chaînes doivent être passées directement au pilote de périphérique de sortie.

Le mappeur de police n’utilise pas la valeur DEFAULT_CHARSET. Une application peut utiliser cette valeur pour permettre au nom et la taille d’une police pour décrire complètement la police logique. Si une police portant le nom spécifié n’existe pas, une police à partir de n’importe quel jeu de caractères peut être remplacée par la police spécifiée. Pour éviter des résultats inattendus, les applications doivent utiliser la valeur DEFAULT_CHARSET avec parcimonie.

*nOutPrecision*<br/>
Spécifie la précision du résultat souhaité. La précision de sortie définit comment étroitement doit correspondre à la sortie de la police demandée hauteur, largeur, l’orientation de caractère, échappement et le pas. Consultez le `lfOutPrecision` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs et des informations supplémentaires.

*nClipPrecision*<br/>
Spécifie la précision de découpage souhaité. La précision de découpage définit comment découper des caractères qui sont partiellement en dehors de la zone de découpage. Consultez le `lfClipPrecision` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.

Pour utiliser une police incorporée en lecture seule, une application doit spécifier CLIP_ENCAPSULATE.

Pour obtenir une rotation cohérente de périphérique, les polices TrueType et les polices vectorielles, une application peut utiliser l’opérateur OR pour combiner la valeur CLIP_LH_ANGLES avec d’autres *nClipPrecision* valeurs. Si le bit CLIP_LH_ANGLES est défini, la rotation de toutes les polices varie selon que l’orientation du système de coordonnées est gauche ou droitier. (Pour plus d’informations sur l’orientation de systèmes de coordonnées, consultez la description de la *nOrientation* paramètre.) Si CLIP_LH_ANGLES n’est pas définie, les polices de périphérique toujours faire pivoter à gauche, mais la rotation des autres polices dépend de l’orientation du système de coordonnées.

*nQuality*<br/>
Spécifie la qualité de sortie de la police, qui définit comment soigneusement le GDI doit tenter de correspondent aux attributs de police logique à ceux d’une police physique réelle. Consultez le `lfQuality` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.

*nPitchAndFamily*<br/>
Spécifie la hauteur et la famille de la police. Consultez le `lfPitchAndFamily` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs et des informations supplémentaires.

*lpszFacename*<br/>
Un `CString` ou pointeur vers une chaîne se terminant par null qui spécifie le nom de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. Le Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa) fonction peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFacename* est NULL, l’interface GDI utilise une police indépendant du périphérique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut être sélectionnée par la suite comme police pour n’importe quel contexte de périphérique.

Le `CreateFont` (fonction) ne crée pas une nouvelle police GDI de Windows. Il sélectionne simplement la plus proche à partir de polices physiques disponibles à l’interface GDI.

Applications peuvent utiliser les paramètres par défaut pour la plupart des paramètres lors de la création d’une police logique. Les paramètres qui doivent toujours être des valeurs spécifiques sont *nHeight* et *lpszFacename*. Si *nHeight* et *lpszFacename* ne sont pas définies par l’application, la police logique qui est créée est dépendant du périphérique.

Lorsque vous avez terminé avec le `CFont` objet créé par le `CreateFont` fonction, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez le `CFont` objet n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect

Initialise un `CFont` objet avec les caractéristiques donné dans un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)structure.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Pointe vers un `LOGFONT` structure qui définit les caractéristiques de la police logique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La police peut être sélectionnée par la suite en tant que la police actuelle de n’importe quel appareil.

Cette police présente les caractéristiques spécifiées dans le [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure. Lorsque la police est sélectionnée à l’aide de la [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) fonction membre, le mappeur de police GDI essaie de correspondre à la police logique avec une police physique existante. Si le mappeur de police ne parvient pas à trouver une correspondance exacte pour la police logique, il fournit une autre police dont les caractéristiques correspondent à autant de caractéristiques demandées que possible.

Lorsque vous n’avez plus besoin du `CFont` objet créé par le `CreateFontIndirect` fonction, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez le `CFont` objet n’est plus nécessaire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>  CFont::CreatePointFont

Cette fonction fournit un moyen simple de créer une police d’une police spécifiée et la taille en points.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*nPointSize*<br/>
Hauteur de police en dixièmes d’un point a demandé. (Par exemple, transmettre 120 pour demander une police de 12 points.)

*lpszFaceName*<br/>
Un `CString` ou pointeur vers une chaîne se terminant par null qui spécifie le nom de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. Le Windows ' EnumFontFamilies fonction peut être utilisée pour énumérer toutes les polices actuellement disponibles. Si *lpszFaceName* est NULL, l’interface GDI utilise une police indépendant du périphérique.

*pDC*<br/>
Pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet à utiliser pour convertir la hauteur dans *nPointSize* d’unités logiques. Si NULL, un contexte de périphérique est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Il convertit automatiquement la hauteur en *nPointSize* d’unités logiques à l’aide de l’objet de la capture de données modifiées vers lequel pointe *pDC*.

Lorsque vous avez terminé avec le `CFont` objet créé par le `CreatePointFont` fonctionner, tout d’abord sélectionner la police en dehors du contexte de périphérique, puis supprimez le `CFont` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

Cette fonction est identique à [CreateFontIndirect](#createfontindirect) , à ceci près que le `lfHeight` membre de la `LOGFONT` est interprétée en dixièmes d’un unités point plutôt que d’appareil.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
Pointe vers un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure qui définit les caractéristiques de la police logique. Le `lfHeight` membre de la `LOGFONT` structure est mesurée en dixièmes d’un point plutôt qu’en unités logiques. (Par exemple, définissez `lfHeight` à 120 pour demander une police de 12 points.)

*pDC*<br/>
Pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet à utiliser pour convertir la hauteur dans `lfHeight` d’unités logiques. Si NULL, un contexte de périphérique est utilisé pour la conversion.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Cette fonction convertit automatiquement la hauteur en `lfHeight` d’unités logiques à l’aide de l’objet de la capture de données modifiées vers lequel pointe *pDC* avant de transmettre le `LOGFONT` structure une session sur Windows.

Lorsque vous avez terminé avec le `CFont` objet créé par le `CreatePointFontIndirect` fonctionner, tout d’abord sélectionner la police en dehors du contexte de périphérique, puis supprimez le `CFont` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>  CFont::FromHandle

Retourne un pointeur vers un `CFont` lorsqu’un handle HFONT vers un objet de police GDI de Windows de l’objet.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Un handle HFONT à une police Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CFont` objet en cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Si un `CFont` objet n’est pas déjà attaché au handle, une table temporaire `CFont` objet est créé et attaché. Ce fichier temporaire `CFont` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède les temps d’inactivité dans sa boucle de l’événement, alors graphique temporaire de tous les objets sont supprimés. Une autre façon de dire cela est que l’objet temporaire est valide uniquement pendant le traitement du message d’une fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>  CFont::GetLogFont

Appelez cette fonction pour récupérer une copie de la `LOGFONT` de structure pour `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Paramètres

*pLogFont*<br/>
Pointeur vers le [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure pour recevoir des informations sur les police.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit, sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>  CFont::operator HFONT

Utilisez cet opérateur pour obtenir le handle Windows GDI de la police attaché à la `CFont` objet.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valeur de retour

Le handle de l’objet de police Windows GDI attaché à `CFont` cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Dans la mesure où cet opérateur est utilisé automatiquement pour les conversions entre `CFont` à [polices et texte](/windows/desktop/gdi/fonts-and-text), vous pouvez passer `CFont` objets aux fonctions qui attendent HFONTs.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](/windows/desktop/gdi/graphic-objects) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

