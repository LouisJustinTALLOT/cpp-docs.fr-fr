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
ms.openlocfilehash: e84526eec8f4fd4b1935fa39bc7f4ed3c4d5dd71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754480"
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
|[CRgn::CombineRgn](#combinergn)|Définit `CRgn` un objet de sorte qu’il `CRgn` soit équivalent à l’union de deux objets spécifiés.|
|[CRgn::CopyRgn](#copyrgn)|Définit `CRgn` un objet de sorte qu’il s’agit d’une copie d’un objet spécifié. `CRgn`|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Initialise un `CRgn` objet avec une région elliptique.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Initialise un `CRgn` objet avec une région elliptique définie par une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateFromData](#createfromdata)|Crée une région à partir de la région donnée et des données de transformation.|
|[CRgn::CreateDePath](#createfrompath)|Crée une région à partir du chemin qui est sélectionné dans le contexte de l’appareil donné.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Initialise un `CRgn` objet avec une région polygonale. Le système ferme automatiquement le polygone, si nécessaire, en traçant une ligne du dernier vertex au premier.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Initialise un `CRgn` objet avec une région composée d’une série de polygones fermés. Les polygones peuvent être disjoints, ou ils peuvent se chevaucher.|
|[CRgn::CreateRectRgn](#createrectrgn)|Initialise un `CRgn` objet avec une région rectangulaire.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Initialise un `CRgn` objet avec une région rectangulaire définie par une trêve [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Initialise un `CRgn` objet avec une région rectangulaire avec des coins arrondis.|
|[CRgn::EqualRgn](#equalrgn)|Vérifie `CRgn` deux objets pour déterminer s’ils sont équivalents.|
|[CRgn::DeHandle](#fromhandle)|Retourne un pointeur à un `CRgn` objet lorsqu’on lui donne une poignée vers une région Windows.|
|[CRgn::GetRegionData](#getregiondata)|Remplit le tampon spécifié avec des données décrivant la région donnée.|
|[CRgn::GetRgnBox](#getrgnbox)|Récupère les coordonnées du rectangle de `CRgn` délimitation d’un objet.|
|[CRgn::OffsetRgn](#offsetrgn)|Déplace `CRgn` un objet par les décalages spécifiés.|
|[CRgn::PtInRegion](#ptinregion)|Détermine si un point spécifié se trouve dans la région.|
|[CRgn::RectInRegion](#rectinregion)|Détermine si une partie d’un rectangle spécifié se trouve à l’intérieur des limites de la région.|
|[CRgn::SetRectRgn](#setrectrgn)|Définit `CRgn` l’objet vers la région rectangulaire spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRgn::opérateur HRGN](#operator_hrgn)|Retourne la poignée Windows `CRgn` contenue dans l’objet.|

## <a name="remarks"></a>Notes

Une région est une zone elliptique ou polygonale à l’intérieur d’une fenêtre. Pour utiliser les régions, vous `CRgn` utilisez les fonctions membres de `CDC`la classe avec les fonctions de coupure définies comme des membres de la classe .

Les fonctions `CRgn` membres de créer, modifier et récupérer des informations sur l’objet de la région pour lequel ils sont appelés.

Pour plus d’informations sur l’utilisation `CRgn`, voir Objets [graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::CombineRgn

Crée une nouvelle région GDI en combinant deux régions existantes.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Paramètres

*pRgn1 (en)*<br/>
Identifie une région existante.

*pRgn2 (en)*<br/>
Identifie une région existante.

*nCombineMode*<br/>
Précise l’opération à effectuer lors de la combinaison des deux régions sources. Il peut s’agir de l’une des valeurs suivantes :

- RGN_AND utilise des zones qui se chevauchent des deux régions (intersection).

- RGN_COPY Crée une copie de la région 1 (identifiée par *pRgn1*).

- RGN_DIFF Crée une région composée des zones de la région 1 (identifiées par *pRgn1*) qui ne font pas partie de la région 2 (identifiée par *pRgn2*).

- RGN_OR Combine les deux régions dans leur intégralité (union).

- RGN_XOR combine les deux régions, mais élimine les zones qui se chevauchent.

### <a name="return-value"></a>Valeur de retour

Spécifie le type de région qui en résulte. Ce peut être l’une des valeurs suivantes :

- COMPLEXREGION Nouvelle région a des frontières qui se chevauchent.

- ERROR Aucune nouvelle région créée.

- NULLREGION Nouvelle région est vide.

- SIMPLEREGION Nouvelle région n’a pas de frontières qui se chevauchent.

### <a name="remarks"></a>Notes

Les régions sont combinées comme spécifié par *nCombineMode*.

Les deux régions spécifiées sont combinées, `CRgn` et la poignée de la région qui en résulte est stockée dans l’objet. Ainsi, quelle que soit `CRgn` la région stockée dans l’objet est remplacée par la région combinée.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Utilisez [CopyRgn](#copyrgn) pour simplement copier une région dans une autre région.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::CopyRgn

Copies de la région définie par `CRgn` *pRgnSrc* dans l’objet.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Paramètres

*pRgnSrc (en)*<br/>
Identifie une région existante.

### <a name="return-value"></a>Valeur de retour

Spécifie le type de région qui en résulte. Ce peut être l’une des valeurs suivantes :

- COMPLEXREGION Nouvelle région a des frontières qui se chevauchent.

- ERROR Aucune nouvelle région créée.

- NULLREGION Nouvelle région est vide.

- SIMPLEREGION Nouvelle région n’a pas de frontières qui se chevauchent.

### <a name="remarks"></a>Notes

La nouvelle région remplace la région `CRgn` autrefois stockée dans l’objet. Cette fonction est un cas spécial de la fonction membre [CombineRgn.](#combinergn)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRgn:CreateEllipticRgn](#createellipticrgn).

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::CreateEllipticRgn

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
Spécifie la logique x-coordonner le coin supérieur gauche du rectangle de délimitation de l’ellipse.

*y1 (en)*<br/>
Spécifie la logique y-coordinate du coin supérieur gauche du rectangle de délimitation de l’ellipse.

*x2*<br/>
Spécifie la x-coordonnées logique du coin inférieur droit du rectangle de délimitation de l’ellipse.

*y2*<br/>
Spécifie la logique y-coordinate du coin inférieur droit du rectangle de délimitation de l’ellipse.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La région est définie par le rectangle de délimitation spécifié par *x1*, *y1*, *x2*, et *y2*. La région est `CRgn` stockée dans l’objet.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsqu’elle a fini d’utiliser une région créée avec la `CreateEllipticRgn` fonction, une `DeleteObject` application doit sélectionner la région hors du contexte de l’appareil et utiliser la fonction pour l’enlever.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Crée une région elliptique.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `RECT` structure `CRect` ou un objet qui contient les coordonnées logiques des coins supérieurs gauche et inférieur-droit du rectangle de délimitation de l’ellipse.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La région est définie par la structure ou l’objet pointé par *lpRect* et est stockée dans l’objet. `CRgn`

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsqu’elle a fini d’utiliser une région créée avec la `CreateEllipticRgnIndirect` fonction, une `DeleteObject` application doit sélectionner la région hors du contexte de l’appareil et utiliser la fonction pour l’enlever.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRgn:CreateRectRgnIndirect](#createrectrgnindirect).

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::CreateFromData

Crée une région à partir de la région donnée et des données de transformation.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Paramètres

*lpXForm*<br/>
Indique une structure [ata XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)qui définit la transformation à effectuer sur la région. Si ce pointeur est NULL, la transformation de l’identité est utilisée.

*nCompte*<br/>
Précise le nombre d’octets pointés par *pRgnData*.

*pRgnData (en)*<br/>
Indique une structure de données [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) qui contient les données de la région.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Une application peut récupérer des données `CRgn::GetRegionData` pour une région en appelant la fonction.

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::CreateDePath

Crée une région à partir du chemin qui est sélectionné dans le contexte de l’appareil donné.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Identifie un contexte d’appareil qui contient un chemin fermé.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Le contexte de l’appareil identifié par le paramètre *pDC* doit contenir un chemin fermé. Après `CreateFromPath` avoir converti un chemin en une région, Windows écarte le chemin fermé du contexte de l’appareil.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn

Crée une région polygonale.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Paramètres

*lpPoints (en)*<br/>
Points à un `POINT` tableau de `CPoint` structures ou une gamme d’objets. Chaque structure spécifie le x-coordonner et y-coordonner d’un vertéx du polygone. La `POINT` structure a la forme suivante :

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCompte*<br/>
Spécifie `POINT` le `CPoint` nombre de structures ou d’objets dans le tableau pointé par *lpPoints*.

*nMode*<br/>
Spécifie le mode de remplissage de la région. Ce paramètre peut être ALTERNATE ou WINDING.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

Le système ferme automatiquement le polygone, si nécessaire, en traçant une ligne du dernier vertex au premier. La région qui en `CRgn` résulte est stockée dans l’objet.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsque le mode de remplissage du polygone est ALTERNATE, le système remplit la zone entre les côtés polygones impairs et numérotés sur chaque ligne d’analyse. Autrement dit, le système remplit la zone entre le premier et le deuxième côté, entre le troisième et le quatrième côté, et ainsi de suite.

Lorsque le mode de remplissage du polygone est WINDING, le système utilise la direction dans laquelle un chiffre a été établi pour déterminer s’il faut remplir une zone. Chaque segment de ligne dans un polygone est dessiné dans le sens des aiguilles d’une montre ou dans le sens inverse des aiguilles d’une montre. Chaque fois qu’une ligne imaginaire dessinée d’une zone fermée à l’extérieur d’une figure passe par un segment de ligne dans le sens des aiguilles d’une montre, un compte est incrémenté. Lorsque la ligne passe à travers un segment de ligne dans le sens inverse des aiguilles d’une montre, le nombre est décrète. La zone est remplie si le nombre est nonzero lorsque la ligne atteint l’extérieur de la figure.

Lorsqu’une application a terminé l’utilisation d’une région créée avec la `CreatePolygonRgn` `DeleteObject` fonction, elle doit sélectionner la région hors du contexte de l’appareil et utiliser la fonction pour l’supprimer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn

Crée une région composée d’une série de polygones fermés.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Paramètres

*lpPoints (en)*<br/>
Points à un `POINT` tableau de `CPoint` structures ou une gamme d’objets qui définit les vertices des polygones. Chaque polygone doit être explicitement fermé parce que le système ne les ferme pas automatiquement. Les polygones sont spécifiés consécutivement. La `POINT` structure a la forme suivante :

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyComptes*<br/>
Points à un tableau d’intégreurs. Le premier integer spécifie le nombre de vertices dans le premier polygone dans le tableau *lpPoints,* le second integer spécifie le nombre de vertices dans le deuxième polygone, et ainsi de suite.

*nCompte*<br/>
Spécifie le nombre total d’intégrateurs dans le tableau *lpPolyCounts.*

*nPolyFillMode*<br/>
Spécifie le mode de remplissage du polygone. Cette valeur peut être ALTERNATIVE ou WINDING.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La région qui en `CRgn` résulte est stockée dans l’objet.

Les polygones peuvent être disjoints, ou ils peuvent se chevaucher.

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsque le mode de remplissage du polygone est ALTERNATE, le système remplit la zone entre les côtés polygones impairs et numérotés sur chaque ligne d’analyse. Autrement dit, le système remplit la zone entre le premier et le deuxième côté, entre le troisième et le quatrième côté, et ainsi de suite.

Lorsque le mode de remplissage du polygone est WINDING, le système utilise la direction dans laquelle un chiffre a été établi pour déterminer s’il faut remplir une zone. Chaque segment de ligne dans un polygone est dessiné dans le sens des aiguilles d’une montre ou dans le sens inverse des aiguilles d’une montre. Chaque fois qu’une ligne imaginaire dessinée d’une zone fermée à l’extérieur d’une figure passe par un segment de ligne dans le sens des aiguilles d’une montre, un compte est incrémenté. Lorsque la ligne passe à travers un segment de ligne dans le sens inverse des aiguilles d’une montre, le nombre est décrète. La zone est remplie si le nombre est nonzero lorsque la ligne atteint l’extérieur de la figure.

Lorsqu’une application a terminé l’utilisation d’une région créée avec la `CreatePolyPolygonRgn` fonction, elle doit sélectionner la région hors du contexte de l’appareil et utiliser la fonction de membre [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour l’enlever.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::CreateRectRgn

Crée une région rectangulaire qui `CRgn` est stockée dans l’objet.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la logique x-coordonner du coin supérieur gauche de la région.

*y1 (en)*<br/>
Spécifie la logique y-coordinate du coin supérieur gauche de la région.

*x2*<br/>
Spécifie la x-coordonner logique du coin inférieur droit de la région.

*y2*<br/>
Spécifie la logique y-coordinate du coin inférieur droit de la région.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsqu’elle a fini d’utiliser une région créée par `CreateRectRgn`, une application doit utiliser la fonction de membre [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer la région.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Pour un autre exemple, voir [CRgn::CombineRgn](#combinergn).

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect

Crée une région rectangulaire qui `CRgn` est stockée dans l’objet.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `RECT` structure `CRect` ou un objet qui contient les coordonnées logiques des coins supérieurs gauche et inférieur-droit de la région. La `RECT` structure a la forme suivante :

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsqu’elle a fini d’utiliser une région créée par `CreateRectRgnIndirect`, une application doit utiliser la fonction de membre [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer la région.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn

Crée une région rectangulaire avec des `CRgn` coins arrondis qui est stocké dans l’objet.

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
Spécifie la logique x-coordonner du coin supérieur gauche de la région.

*y1 (en)*<br/>
Spécifie la logique y-coordinate du coin supérieur gauche de la région.

*x2*<br/>
Spécifie la x-coordonner logique du coin inférieur droit de la région.

*y2*<br/>
Spécifie la logique y-coordinate du coin inférieur droit de la région.

*x3*<br/>
Spécifie la largeur de l’ellipse utilisée pour créer les coins arrondis.

*y3 (en)*<br/>
Spécifie la hauteur de l’ellipse utilisée pour créer les coins arrondis.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a réussi; sinon 0.

### <a name="remarks"></a>Notes

La taille d’une région est limitée à 32 767 par 32 767 unités logiques ou 64K de mémoire, selon le plus petit.

Lorsqu’une application a terminé l’utilisation d’une région créée avec la `CreateRoundRectRgn` fonction, elle doit sélectionner la région hors du contexte de l’appareil et utiliser la fonction de membre [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour l’enlever.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn::CRgn

Construit un objet `CRgn`.

```
CRgn();
```

### <a name="remarks"></a>Notes

Le `m_hObject` membre des données ne contient pas une région valide de Windows GDI jusqu’à ce que l’objet soit para initialisé avec une ou plusieurs des autres `CRgn` fonctions du membre.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRgn::CreateRoundRectRgn](#createroundrectrgn).

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::EqualRgn

Détermine si la région donnée est équivalente `CRgn` à la région stockée dans l’objet.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Paramètres

*pRgn (en)*<br/>
Identifie une région.

### <a name="return-value"></a>Valeur de retour

Nonzero si les deux régions sont équivalentes; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::DeHandle

Retourne un pointeur à un `CRgn` objet lorsqu’on lui donne une poignée vers une région Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Paramètres

*hRgn (en)*<br/>
Spécifie une poignée vers une région Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CRgn`. Si la fonction n’a pas été couronnée de succès, la valeur de rendement est NULL.

### <a name="remarks"></a>Notes

Si `CRgn` un objet n’est pas déjà `CRgn` attaché à la poignée, un objet temporaire est créé et attaché. Cet `CRgn` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. Une autre façon de dire cela est que l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn::GetRegionData

Remplit le tampon spécifié avec des données décrivant la région.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Paramètres

*lpRgnData*<br/>
Indique une structure de données [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) qui reçoit l’information. Si ce paramètre est NULL, la valeur de retour contient le nombre d’octets nécessaires pour les données de la région.

*nCompte*<br/>
Spécifie la taille, dans les octets, du tampon *lpRgnData.*

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit et *nCount* spécifie un nombre suffisant d’octets, la valeur de retour est toujours *nCount*. Si la fonction échoue, ou si *nCount* spécifie moins d’un nombre suffisant d’octets, la valeur de retour est de 0 (erreur).

### <a name="remarks"></a>Notes

Ces données comprennent les dimensions des rectangles qui composent la région. Cette fonction est utilisée `CRgn::CreateFromData` en conjonction avec la fonction.

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

Récupère les coordonnées du rectangle de `CRgn` délimitation de l’objet.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `RECT` structure `CRect` ou un objet pour recevoir les coordonnées du rectangle de délimitation. La `RECT` structure a la forme suivante :

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Valeur de retour

Spécifie le type de région. Il peut s’agir de l’une des valeurs suivantes :

- COMPLEXREGION Region a des frontières qui se chevauchent.

- NULLREGION Région est vide.

- L’objet ERROR `CRgn` ne spécifie pas une région valide.

- LA région DE SIMPLEREGION n’a pas de frontières qui se chevauchent.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRgn:CreatePolygonRgn](#createpolygonrgn).

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::OffsetRgn

Déplace la région `CRgn` stockée dans l’objet par les décalages spécifiés.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités à déplacer à gauche ou à droite.

*y*<br/>
Spécifie le nombre d’unités à déplacer vers le haut ou vers le bas.

*Point*<br/>
La x-coordonner le *point* précise le nombre d’unités à déplacer à gauche ou à droite. La y-coordinate du *point* précise le nombre d’unités à déplacer vers le haut ou vers le bas. Le paramètre *de* `POINT` point peut `CPoint` être soit une structure ou un objet.

### <a name="return-value"></a>Valeur de retour

Le type de la nouvelle région. Il peut s’agir de l’une des valeurs suivantes :

- COMPLEXREGION Region a des frontières qui se chevauchent.

- La poignée de la région ERROR n’est pas valide.

- NULLREGION Région est vide.

- LA région DE SIMPLEREGION n’a pas de frontières qui se chevauchent.

### <a name="remarks"></a>Notes

La fonction déplace la région *x* unités le long de l’axe x et *y* unités le long de l’axe y.

Les valeurs de coordonnées d’une région doivent être inférieures ou égales à 32 767 et supérieures ou égales à -32 768. Les paramètres *x* et *y* doivent être soigneusement choisis pour empêcher les coordonnées de région non valides.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRgn:CreateEllipticRgn](#createellipticrgn).

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::opérateur HRGN

Utilisez cet opérateur pour obtenir la poignée `CRgn` Windows GDI attachée de l’objet.

```
operator HRGN() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée à `CRgn` l’objet GDI Windows représenté par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HRGN.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir l’article [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::PtInRegion

Vérifie si le point donné par *x* et `CRgn` *y* est stocké dans la région stockée dans l’objet.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie la x-coordonner logique du point à tester.

*y*<br/>
Spécifie la logique y-coordinate du point à tester.

*Point*<br/>
Les coordonnées x et *y-points* spécifient les coordonnées x et y du point pour tester la valeur de. Le paramètre *de* `POINT` point peut `CPoint` être une structure ou un objet.

### <a name="return-value"></a>Valeur de retour

Nonzero si le point est dans la région; sinon 0.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::RectInRegion

Détermine si une partie du rectangle spécifiée par *lpRect* se trouve `CRgn` à l’intérieur des limites de la région stockée dans l’objet.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `RECT` structure `CRect` ou un objet. La `RECT` structure a la forme suivante :

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si une partie du rectangle spécifié se trouve dans les limites de la région; sinon 0.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::SetRectRgn

Crée une région rectangulaire.

```cpp
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la x-coordonner le coin supérieur gauche de la région rectangulaire.

*y1 (en)*<br/>
Spécifie le y-coordinate du coin supérieur gauche de la région rectangulaire.

*x2*<br/>
Spécifie la x-coordonner le coin inférieur droit de la région rectangulaire.

*y2*<br/>
Spécifie la y-coordonnées du coin inférieur droit de la région rectangulaire.

*lpRect*<br/>
Spécifie la région rectangulaire. Peut être soit un `RECT` pointeur `CRect` d’une structure ou un objet.

### <a name="remarks"></a>Notes

Contrairement à [CreateRectRgn](#createrectrgn), cependant, il n’alloue pas de mémoire supplémentaire du tas local d’application Windows. Au lieu de cela, il utilise l’espace alloué pour la région stockée dans l’objet. `CRgn` Cela signifie `CRgn` que l’objet doit déjà avoir été `SetRectRgn`paradé avec une région Windows valide avant d’appeler . Les points donnés par *x1*, *y1*, *x2*, et *y2* spécifier la taille minimale de l’espace alloué.

Utilisez cette fonction `CreateRectRgn` au lieu de la fonction membre pour éviter les appels au gestionnaire de mémoire local.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
