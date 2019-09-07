---
title: CRgn, classe
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 97266ac9e4f1885149ce521f554ad2f22daee6e0
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741503"
---
# <a name="crgn-class"></a>CRgn, classe

Encapsule une région GDI (Graphics Device Interface) Windows.

## <a name="syntax"></a>Syntaxe

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Construit un objet `CRgn`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Définit un `CRgn` objet de manière à ce qu’il soit équivalent à l’Union `CRgn` de deux objets spécifiés.|
|[CRgn::CopyRgn](#copyrgn)|Définit un `CRgn` objet afin qu’il s’agit d’une copie d' `CRgn` un objet spécifié.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Initialise un `CRgn` objet avec une zone elliptique.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Initialise un `CRgn` objet avec une zone elliptique définie par une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .|
|[CRgn::CreateFromData](#createfromdata)|Crée une région à partir de la région donnée et des données de transformation.|
|[CRgn::CreateFromPath](#createfrompath)|Crée une région à partir du chemin d’accès sélectionné dans le contexte de périphérique donné.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Initialise un `CRgn` objet avec une région polygonale. Le système ferme automatiquement le polygone, si nécessaire, en dessinant une ligne du dernier vertex jusqu’au premier.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Initialise un `CRgn` objet avec une zone composée d’une série de polygones fermés. Les polygones peuvent être disjoints ou se chevaucher.|
|[CRgn::CreateRectRgn](#createrectrgn)|Initialise un `CRgn` objet avec une zone rectangulaire.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Initialise un `CRgn` objet avec une zone rectangulaire définie par un [Rect](/windows/win32/api/windef/ns-windef-rect)tructure.|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Initialise un `CRgn` objet avec une zone rectangulaire avec des angles arrondis.|
|[CRgn::EqualRgn](#equalrgn)|Vérifie deux `CRgn` objets pour déterminer s’ils sont équivalents.|
|[CRgn::FromHandle](#fromhandle)|Retourne un pointeur vers un `CRgn` objet en fonction d’un handle vers une région Windows.|
|[CRgn::GetRegionData](#getregiondata)|Remplit la mémoire tampon spécifiée avec des données décrivant la région donnée.|
|[CRgn::GetRgnBox](#getrgnbox)|Récupère les coordonnées du rectangle englobant d’un `CRgn` objet.|
|[CRgn::OffsetRgn](#offsetrgn)|Déplace un `CRgn` objet selon les décalages spécifiés.|
|[CRgn ::P tInRegion](#ptinregion)|Détermine si un point spécifié se trouve dans la zone.|
|[CRgn::RectInRegion](#rectinregion)|Détermine si une partie d’un rectangle spécifié se trouve dans les limites de la zone.|
|[CRgn::SetRectRgn](#setrectrgn)|Définit l' `CRgn` objet sur la zone rectangulaire spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRgn :: Operator HRGN](#operator_hrgn)|Retourne le handle Windows contenu dans l' `CRgn` objet.|

## <a name="remarks"></a>Notes

Une région est une zone elliptique ou polygonale dans une fenêtre. Pour utiliser des régions, vous utilisez les fonctions membres de `CRgn` la classe avec les fonctions de découpage `CDC`définies en tant que membres de la classe.

Les fonctions membres de `CRgn` créent, modifient et récupèrent des informations sur l’objet Region pour lequel elles sont appelées.

Pour plus d’informations sur `CRgn`l’utilisation de, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

Crée une nouvelle région GDI en combinant deux régions existantes.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Paramètres

*pRgn1*<br/>
Identifie une région existante.

*pRgn2*<br/>
Identifie une région existante.

*nCombineMode*<br/>
Spécifie l’opération à effectuer lors de la combinaison des deux régions sources. Il peut s’agir de l’une des valeurs suivantes :

- RGN_AND utilise des zones qui se chevauchent des deux régions (intersection).

- RGN_COPY crée une copie de la région 1 (identifiée par *pRgn1*).

- RGN_DIFF crée une région composée des zones de la région 1 (identifiées par *pRgn1*) qui ne font pas partie de la région 2 (identifiée par *pRgn2*).

- RGN_OR combine les deux régions dans leur intégralité (Union).

- RGN_XOR combine les deux régions, mais supprime les zones qui se chevauchent.

### <a name="return-value"></a>Valeur de retour

Spécifie le type de la zone résultante. Il peut s’agir de l’une des valeurs suivantes :

- COMPLEXREGION nouvelle région a des bordures qui se chevauchent.

- ERREUR : aucune nouvelle région créée.

- NULLREGION nouvelle région est vide.

- SIMPLEREGION nouvelle région n’a pas de bordures se chevauchant.

### <a name="remarks"></a>Notes

Les régions sont combinées comme spécifié par *nCombineMode*.

Les deux régions spécifiées sont combinées et le handle de la région qui en `CRgn` résulte est stocké dans l’objet. Ainsi, quelle que soit la région stockée dans l' `CRgn` objet est remplacée par la région combinée.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Utilisez [CopyRgn](#copyrgn) pour copier simplement une région dans une autre région.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

Copie la région définie par *pRgnSrc* dans l' `CRgn` objet.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Paramètres

*pRgnSrc*<br/>
Identifie une région existante.

### <a name="return-value"></a>Valeur de retour

Spécifie le type de la zone résultante. Il peut s’agir de l’une des valeurs suivantes :

- COMPLEXREGION nouvelle région a des bordures qui se chevauchent.

- ERREUR : aucune nouvelle région créée.

- NULLREGION nouvelle région est vide.

- SIMPLEREGION nouvelle région n’a pas de bordures se chevauchant.

### <a name="remarks"></a>Notes

La nouvelle région remplace la région précédemment stockée dans `CRgn` l’objet. Cette fonction est un cas particulier de la fonction membre [CombineRgn](#combinergn) .

### <a name="example"></a>Exemples

  Consultez l’exemple de [CRgn :: CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

Crée une région elliptique.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x logique de l’angle supérieur gauche du rectangle englobant de l’ellipse.

*y1*<br/>
Spécifie la coordonnée y logique de l’angle supérieur gauche du rectangle englobant de l’ellipse.

*x2*<br/>
Spécifie la coordonnée x logique du coin inférieur droit du rectangle englobant de l’ellipse.

*y2*<br/>
Spécifie la coordonnée y logique du coin inférieur droit du rectangle englobant de l’ellipse.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La région est définie par le rectangle englobant spécifié par *x1*, *Y1*, *x2*et *Y2*. La région est stockée dans `CRgn` l’objet.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsqu’il a fini d’utiliser une région créée avec `CreateEllipticRgn` la fonction, une application doit sélectionner la région hors du contexte de périphérique et utiliser `DeleteObject` la fonction pour la supprimer.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

Crée une région elliptique.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une `RECT` structure ou un `CRect` objet qui contient les coordonnées logiques des angles supérieur gauche et inférieur droit du rectangle englobant de l’ellipse.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La région est définie par la structure ou l’objet désigné par *lpRect* et est stockée dans `CRgn` l’objet.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsqu’il a fini d’utiliser une région créée avec `CreateEllipticRgnIndirect` la fonction, une application doit sélectionner la région hors du contexte de périphérique et utiliser `DeleteObject` la fonction pour la supprimer.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CRgn :: CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>  CRgn::CreateFromData

Crée une région à partir de la région donnée et des données de transformation.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Paramètres

*lpXForm*<br/>
Pointe vers une structure ATA [XForm](/windows/win32/api/wingdi/ns-wingdi-xform)qui définit la transformation à effectuer sur la région. Si ce pointeur est NULL, la transformation d’identité est utilisée.

*nCount*<br/>
Spécifie le nombre d’octets pointés par *pRgnData*.

*pRgnData*<br/>
Pointe vers une structure de données [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) qui contient les données de la région.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Une application peut récupérer des données pour une région en appelant `CRgn::GetRegionData` la fonction.

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

Crée une région à partir du chemin d’accès sélectionné dans le contexte de périphérique donné.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Identifie un contexte de périphérique (Device Context) qui contient un chemin d’accès fermé.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Le contexte de périphérique identifié par le paramètre *PDC* doit contenir un chemin d’accès fermé. Après `CreateFromPath` avoir converti un chemin d’accès en une région, Windows ignore le chemin d’accès fermé du contexte de périphérique.

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

Crée une région polygonale.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Paramètres

*lpPoints*<br/>
Pointe vers un tableau de `POINT` structures ou un tableau d' `CPoint` objets. Chaque structure spécifie la coordonnée x et la coordonnée y d’un vertex du polygone. La `POINT` structure se présente sous la forme suivante :

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Spécifie le nombre `POINT` de structures `CPoint` ou d’objets dans le tableau pointé par *lpPoints*.

*nMode*<br/>
Spécifie le mode de remplissage pour la région. Il peut s’agir d’un paramètre alternatif ou d’un enroulement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Le système ferme automatiquement le polygone, si nécessaire, en dessinant une ligne du dernier vertex jusqu’au premier. La région obtenue est stockée dans `CRgn` l’objet.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsque le mode de remplissage polygone est alternatif, le système remplit la zone entre les côtés de polygones numérotés et pairs sur chaque ligne de numérisation. Autrement dit, le système remplit la zone entre le premier et le deuxième côté, entre le troisième et le quatrième côté, et ainsi de suite.

Lorsque le mode de remplissage de polygone est en cours d’enroulement, le système utilise la direction dans laquelle une figure a été dessinée pour déterminer s’il faut remplir une zone. Chaque segment de ligne d’un polygone est dessiné dans le sens horaire ou dans le sens inverse des aiguilles d’une montre. Chaque fois qu’une ligne imaginaire dessinée à partir d’une zone fermée à l’extérieur d’une figure passe par un segment de ligne dans le sens des aiguilles d’une montre, un nombre est incrémenté. Lorsque la ligne passe par un segment de ligne dans le sens inverse, le nombre est décrémenté. La zone est remplie si le nombre est différent de zéro lorsque la ligne atteint l’extérieur de la figure.

Lorsqu’une application a fini d’utiliser une région créée à `CreatePolygonRgn` l’aide de la fonction, elle doit sélectionner la région hors du contexte de `DeleteObject` périphérique et utiliser la fonction pour la supprimer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

Crée une région composée d’une série de polygones fermés.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Paramètres

*lpPoints*<br/>
Pointe vers un tableau de `POINT` structures ou un tableau d' `CPoint` objets qui définit les vertex des polygones. Chaque polygone doit être explicitement fermé, car le système ne les ferme pas automatiquement. Les polygones sont spécifiés consécutivement. La `POINT` structure se présente sous la forme suivante :

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Pointe vers un tableau d’entiers. Le premier entier spécifie le nombre de vertex dans le premier polygone dans le tableau *lpPoints* , le deuxième entier spécifie le nombre de vertex dans le deuxième polygone, et ainsi de suite.

*nCount*<br/>
Spécifie le nombre total d’entiers dans le tableau *lpPolyCounts* .

*nPolyFillMode*<br/>
Spécifie le mode de remplissage du polygone. Cette valeur peut être alternative ou enroulement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La région obtenue est stockée dans `CRgn` l’objet.

Les polygones peuvent être disjoints ou se chevaucher.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsque le mode de remplissage polygone est alternatif, le système remplit la zone entre les côtés de polygones numérotés et pairs sur chaque ligne de numérisation. Autrement dit, le système remplit la zone entre le premier et le deuxième côté, entre le troisième et le quatrième côté, et ainsi de suite.

Lorsque le mode de remplissage de polygone est en cours d’enroulement, le système utilise la direction dans laquelle une figure a été dessinée pour déterminer s’il faut remplir une zone. Chaque segment de ligne d’un polygone est dessiné dans le sens horaire ou dans le sens inverse des aiguilles d’une montre. Chaque fois qu’une ligne imaginaire dessinée à partir d’une zone fermée à l’extérieur d’une figure passe par un segment de ligne dans le sens des aiguilles d’une montre, un nombre est incrémenté. Lorsque la ligne passe par un segment de ligne dans le sens inverse, le nombre est décrémenté. La zone est remplie si le nombre est différent de zéro lorsque la ligne atteint l’extérieur de la figure.

Lorsqu’une application a fini d’utiliser une région créée à `CreatePolyPolygonRgn` l’aide de la fonction, elle doit sélectionner la région hors du contexte de périphérique et utiliser la fonction membre [CGDIObject ::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour la supprimer.

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

Crée une zone rectangulaire qui est stockée dans `CRgn` l’objet.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x logique de l’angle supérieur gauche de la zone.

*y1*<br/>
Spécifie la coordonnée y logique de l’angle supérieur gauche de la zone.

*x2*<br/>
Spécifie la coordonnée x logique du coin inférieur droit de la zone.

*y2*<br/>
Spécifie la coordonnée y logique du coin inférieur droit de la zone.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsqu’il a fini d’utiliser une région créée `CreateRectRgn`par, une application doit utiliser la fonction membre [CGDIObject ::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer la région.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Pour obtenir un exemple supplémentaire, consultez [CRgn :: CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

Crée une zone rectangulaire qui est stockée dans `CRgn` l’objet.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une `RECT` structure ou `CRect` un objet qui contient les coordonnées logiques des angles supérieur gauche et inférieur droit de la zone. La `RECT` structure se présente sous la forme suivante :

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsqu’il a fini d’utiliser une région créée `CreateRectRgnIndirect`par, une application doit utiliser la fonction membre [CGDIObject ::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer la région.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

Crée une zone rectangulaire avec des angles arrondis stockés dans l' `CRgn` objet.

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x logique de l’angle supérieur gauche de la zone.

*y1*<br/>
Spécifie la coordonnée y logique de l’angle supérieur gauche de la zone.

*x2*<br/>
Spécifie la coordonnée x logique du coin inférieur droit de la zone.

*y2*<br/>
Spécifie la coordonnée y logique du coin inférieur droit de la zone.

*x3*<br/>
Spécifie la largeur de l’ellipse utilisée pour créer les angles arrondis.

*y3*<br/>
Spécifie la hauteur de l’ellipse utilisée pour créer les angles arrondis.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64 Ko de mémoire, la valeur la plus petite étant retenue.

Lorsqu’une application a fini d’utiliser une région créée à `CreateRoundRectRgn` l’aide de la fonction, elle doit sélectionner la région hors du contexte de périphérique et utiliser la fonction membre [CGDIObject ::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour la supprimer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

Construit un objet `CRgn`.

```
CRgn();
```

### <a name="remarks"></a>Notes

Le `m_hObject` membre de données ne contient pas de région GDI Windows valide tant que l’objet n’est pas initialisé avec une ou plusieurs `CRgn` autres fonctions membres.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CRgn :: CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>  CRgn::EqualRgn

Détermine si la région donnée équivaut à la région stockée dans l' `CRgn` objet.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Paramètres

*pRgn*<br/>
Identifie une région.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les deux régions sont équivalentes ; Sinon, 0.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

Retourne un pointeur vers un `CRgn` objet en fonction d’un handle vers une région Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Paramètres

*hRgn*<br/>
Spécifie un handle vers une région Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CRgn` . Si la fonction n’a pas réussi, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

Si un `CRgn` objet n’est pas déjà attaché au descripteur, `CRgn` un objet temporaire est créé et attaché. Cet objet `CRgn` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valide que pendant le traitement d’un message de fenêtre.

##  <a name="getregiondata"></a>  CRgn::GetRegionData

Remplit la mémoire tampon spécifiée avec des données décrivant la région.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Paramètres

*lpRgnData*<br/>
Pointe vers une structure de données [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) qui reçoit les informations. Si ce paramètre a la valeur NULL, la valeur de retour contient le nombre d’octets nécessaires pour les données de la région.

*nCount*<br/>
Spécifie la taille, en octets, de la mémoire tampon *lpRgnData* .

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie et que *nCount* spécifie un nombre d’octets suffisant, la valeur de retour est toujours *nCount*. Si la fonction échoue, ou si *nCount* spécifie un nombre d’octets inférieur au nombre suffisant, la valeur de retour est 0 (erreur).

### <a name="remarks"></a>Notes

Ces données incluent les dimensions des rectangles qui composent la région. Cette fonction est utilisée conjointement avec la `CRgn::CreateFromData` fonction.

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

Récupère les coordonnées du rectangle englobant de l' `CRgn` objet.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une `RECT` structure ou `CRect` un objet pour recevoir les coordonnées du rectangle englobant. La `RECT` structure se présente sous la forme suivante :

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Valeur de retour

Spécifie le type de la région. Il peut s’agir de l’une des valeurs suivantes :

- La région COMPLEXREGION a des bordures qui se chevauchent.

- La région NULLREGION est vide.

- L' `CRgn` objet d’erreur ne spécifie pas une région valide.

- La région SIMPLEREGION n’a pas de bordures se chevauchant.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRgn :: CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

Déplace la région stockée dans `CRgn` l’objet selon les décalages spécifiés.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités à déplacer vers la gauche ou vers la droite.

*y*<br/>
Spécifie le nombre d’unités à déplacer vers le haut ou vers le haut.

*point*<br/>
La coordonnée x du *point* spécifie le nombre d’unités à déplacer vers la gauche ou vers la droite. La coordonnée y du *point* spécifie le nombre d’unités à déplacer vers le haut ou vers le haut. Le paramètre *point* peut être une `POINT` structure ou un `CPoint` objet.

### <a name="return-value"></a>Valeur de retour

Type de la nouvelle région. Il peut s’agir de l’une des valeurs suivantes :

- La région COMPLEXREGION a des bordures qui se chevauchent.

- Le descripteur de la région d’erreur n’est pas valide.

- La région NULLREGION est vide.

- La région SIMPLEREGION n’a pas de bordures se chevauchant.

### <a name="remarks"></a>Notes

La fonction déplace les unités de la région *x* sur les unités de l’axe x et *y* le long de l’axe y.

Les valeurs de coordonnée d’une région doivent être inférieures ou égales à 32 767 et supérieures ou égales à-32 768. Les paramètres *x* et *y* doivent être choisis avec soin pour empêcher les coordonnées de région non valides.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRgn :: CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>CRgn :: Operator HRGN

Utilisez cet opérateur pour récupérer le handle Windows GDI attaché de l' `CRgn` objet.

```
operator HRGN() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers l’objet Windows GDI représenté par `CRgn` l’objet ; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HRGN.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez l’article [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

##  <a name="ptinregion"></a>  CRgn::PtInRegion

Vérifie si le point donné par *x* et *y* se trouve dans la région stockée `CRgn` dans l’objet.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie la coordonnée x logique du point à tester.

*y*<br/>
Spécifie la coordonnée y logique du point à tester.

*point*<br/>
Les coordonnées x et y du *point* spécifient les coordonnées x et y du point dont la valeur doit être testée. Le paramètre *point* peut être une `POINT` structure ou un `CPoint` objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le point se trouve dans la région ; Sinon, 0.

##  <a name="rectinregion"></a>  CRgn::RectInRegion

Détermine si une partie du rectangle spécifié par *lpRect* se trouve dans les limites de la région stockée dans `CRgn` l’objet.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une `RECT` structure ou `CRect` un objet. La `RECT` structure se présente sous la forme suivante :

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si une partie du rectangle spécifié se trouve dans les limites de la zone ; Sinon, 0.

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

Crée une zone rectangulaire.

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x de l’angle supérieur gauche de la zone rectangulaire.

*y1*<br/>
Spécifie la coordonnée y de l’angle supérieur gauche de la zone rectangulaire.

*x2*<br/>
Spécifie la coordonnée x du coin inférieur droit de la zone rectangulaire.

*y2*<br/>
Spécifie la coordonnée y du coin inférieur droit de la zone rectangulaire.

*lpRect*<br/>
Spécifie la zone rectangulaire. Il peut s’agir d’un pointeur `RECT` vers une structure `CRect` ou un objet.

### <a name="remarks"></a>Notes

Toutefois, contrairement à [CreateRectRgn](#createrectrgn), il n’alloue pas de mémoire supplémentaire à partir du tas de l’application Windows locale. Au lieu de cela, il utilise l’espace alloué pour la région `CRgn` stockée dans l’objet. Cela signifie que l' `CRgn` objet doit déjà avoir été initialisé avec une région Windows valide avant d’appeler `SetRectRgn`. Les points donnés par *x1*, *Y1*, *x2*et *Y2* spécifient la taille minimale de l’espace alloué.

Utilisez cette fonction à la place `CreateRectRgn` de la fonction membre pour éviter les appels au gestionnaire de mémoire local.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
