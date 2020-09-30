---
title: CRect, classe
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: f45090971e8dbb89ae281b408cc3a14e102ffe17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502877"
---
# <a name="crect-class"></a>CRect, classe

Semblable à une structure Windows [Rect](/windows/win32/api/windef/ns-windef-rect) .

## <a name="syntax"></a>Syntaxe

```
class CRect : public tagRECT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRect :: CRect](#crect)|Construit un objet `CRect`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRect :: BottomRight](#bottomright)|Retourne le point inférieur droit de `CRect` .|
|[CRect :: CenterPoint](#centerpoint)|Retourne le Centerpoint de `CRect` .|
|[CRect :: CopyRect](#copyrect)|Copie les dimensions d’un rectangle source dans `CRect` .|
|[CRect ::D eflateRect](#deflaterect)|Diminue la largeur et la hauteur de `CRect` .|
|[CRect :: EqualRect](#equalrect)|Détermine si `CRect` est égal au rectangle donné.|
|[CRect :: Height](#height)|Calcule la hauteur de `CRect` .|
|[CRect :: InflateRect](#inflaterect)|Augmente la largeur et la hauteur de `CRect` .|
|[CRect :: IntersectRect](#intersectrect)|Définit `CRect` égal à l’intersection de deux rectangles.|
|[CRect :: IsRectEmpty](#isrectempty)|Détermine si `CRect` est vide. `CRect` est vide si la largeur et/ou la hauteur sont égales à 0.|
|[CRect :: IsRectNull](#isrectnull)|Détermine si les `top` `bottom` `left` variables membres,, et `right` sont toutes égales à 0.|
|[CRect :: MoveToX](#movetox)|Passe `CRect` à la coordonnée x spécifiée.|
|[CRect :: MoveToXY](#movetoxy)|Déplace `CRect` vers les coordonnées x et y spécifiées.|
|[CRect :: MoveToY](#movetoy)|Déplace `CRect` vers la coordonnée y spécifiée.|
|[CRect :: NormalizeRect](#normalizerect)|Normalise la hauteur et la largeur de `CRect` .|
|[CRect :: OffsetRect](#offsetrect)|Se déplace `CRect` selon les décalages spécifiés.|
|[CRect ::P tInRect](#ptinrect)|Détermine si le point spécifié se trouve dans `CRect` .|
|[CRect :: SetRect](#setrect)|Définit les dimensions de `CRect` .|
|[CRect :: SetRectEmpty](#setrectempty)|Définit `CRect` sur un rectangle vide (toutes les coordonnées égales à 0).|
|[CRect :: Size](#size)|Calcule la taille de `CRect` .|
|[CRect :: SubtractRect](#subtractrect)|Soustrait un rectangle d’un autre.|
|[CRect :: Left](#topleft)|Retourne le point supérieur gauche de `CRect` .|
|[CRect :: UnionRect](#unionrect)|Définit `CRect` égal à l’Union de deux rectangles.|
|[CRect :: width](#width)|Calcule la largeur de `CRect` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRect :: Operator-](#operator_-)|Soustrait les offsets donnés de `CRect` ou déflate `CRect` et retourne le résultant `CRect` .|
|[CRect :: Operator LPCRECT](#operator_lpcrect)|Convertit `CRect` en `LPCRECT`.|
|[CRect :: Operator LPRECT](#operator_lprect)|Convertit `CRect` en `LPRECT`.|
|[CRect :: Operator ! =](#operator_neq)|Détermine si `CRect` n’est pas égal à un rectangle.|
|[CRect :: Operator &amp;](#operator_amp)|Crée l’intersection de `CRect` et d’un rectangle et retourne le résultant `CRect` .|
|[CRect :: Operator &amp;=](#operator_amp_eq)|Définit `CRect` égal à l’intersection de `CRect` et d’un rectangle.|
|[CRect :: Operator &#124;](#operator_or)|Crée l’Union de `CRect` et un rectangle et retourne le résultant `CRect` .|
|[CRect :: Operator &#124;=](#operator_or_eq)|Définit `CRect` égal à l’Union de `CRect` et un rectangle.|
|[CRect :: Operator +](#operator_add)|Ajoute les offsets donnés à `CRect` ou gonfle `CRect` et retourne le résultant `CRect` .|
|[CRect :: Operator + =](#operator_add_eq)|Ajoute les décalages spécifiés à `CRect` ou à `CRect` .|
|[CRect :: Operator =](#operator_eq)|Copie les dimensions d’un rectangle dans `CRect` .|
|[CRect :: Operator-=](#operator_-_eq)|Soustrait les offsets spécifiés de `CRect` ou déflate `CRect` .|
|[CRect :: Operator = =](#operator_eq_eq)|Détermine si `CRect` est égal à un rectangle.|

## <a name="remarks"></a>Remarques

`CRect` comprend également des fonctions membres pour manipuler `CRect` des objets et des `RECT` structures Windows.

Un `CRect` objet peut être passé comme paramètre de fonction chaque fois qu’une `RECT` structure, `LPCRECT` ou `LPRECT` peut être passée.

> [!NOTE]
> Cette classe est dérivée de la `tagRECT` structure. (Le nom `tagRECT` est un nom moins couramment utilisé pour la `RECT` structure.) Cela signifie que les membres de données ( `left` , `top` , `right` et `bottom` ) de la `RECT` structure sont des membres de données accessibles de `CRect` .

Un `CRect` contient des variables membres qui définissent les points supérieur à gauche et inférieur droit d’un rectangle.

Lorsque vous spécifiez un `CRect` , vous devez veiller à le construire afin qu’il soit normalisé, en d’autres termes, de telle sorte que la valeur de la coordonnée gauche soit inférieure à la droite et que le haut soit inférieur au bas. Par exemple, une partie supérieure gauche de (10, 10) et la partie inférieure droite de (20, 20) définissent un rectangle normalisé, tandis que le haut à gauche de (20, 20) et le bas à droite de (10, 10) définissent un rectangle non normalisé. Si le rectangle n’est pas normalisé, de nombreuses `CRect` fonctions membres peuvent retourner des résultats incorrects. (Pour obtenir la liste de ces fonctions, consultez [CRect :: NormalizeRect](#normalizerect) .) Avant d’appeler une fonction qui requiert des rectangles normalisés, vous pouvez normaliser des rectangles non normalisés en appelant la `NormalizeRect` fonction.

Soyez prudent lors de la manipulation d’un `CRect` avec les fonctions membres [cdc ::D Ptolp](../../mfc/reference/cdc-class.md#dptolp) et [CDC :: LPtoDP](../../mfc/reference/cdc-class.md#lptodp) . Si le mode de mappage d’un contexte d’affichage est tel que l’étendue y est négative, comme dans `MM_LOENGLISH` , `CDC::DPtoLP` transformera le `CRect` afin que sa valeur supérieure soit supérieure au bas. Les fonctions telles que `Height` et `Size` retournent ensuite des valeurs négatives pour la hauteur du transformé `CRect` , et le rectangle est non normalisé.

Lors de l’utilisation d’opérateurs surchargés `CRect` , le premier opérande doit être un `CRect` ; le second peut être soit une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , soit un `CRect` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagRECT`

`CRect`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes. h

## <a name="crectbottomright"></a><a name="bottomright"></a> CRect :: BottomRight

Les coordonnées sont retournées en tant que référence à un objet [CPoint](cpoint-class.md) contenu dans `CRect` .

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Coordonnées du coin inférieur droit du rectangle.

### <a name="remarks"></a>Remarques

Vous pouvez utiliser cette fonction pour récupérer ou définir le coin inférieur droit du rectangle. Définissez l’angle à l’aide de cette fonction sur le côté gauche de l’opérateur d’assignation.

### <a name="example"></a>Exemple

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

## <a name="crectcenterpoint"></a><a name="centerpoint"></a> CRect :: CenterPoint

Calcule le Centerpoint de `CRect` en ajoutant les valeurs de gauche et de droite, en les divisant par deux, et en ajoutant les valeurs supérieure et inférieure, puis en les divisant par deux.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

`CPoint`Objet qui est le Centerpoint de `CRect` .

### <a name="example"></a>Exemple

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

## <a name="crectcopyrect"></a><a name="copyrect"></a> CRect :: CopyRect

Copie le `lpSrcRect` rectangle dans `CRect` .

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Paramètres

*lpSrcRect*<br/>
Pointe vers la structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou l' `CRect` objet à copier.

### <a name="example"></a>Exemple

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

## <a name="crectcrect"></a><a name="crect"></a> CRect :: CRect

Construit un objet `CRect`.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Paramètres

*l*<br/>
Spécifie la position gauche de `CRect` .

*t*<br/>
Spécifie le haut de `CRect` .

*r*<br/>
Spécifie la position de droite de `CRect` .

*b*<br/>
Spécifie le bas de `CRect` .

*srcRect*<br/>
Fait référence à la structure [Rect](/windows/win32/api/windef/ns-windef-rect) avec les coordonnées de `CRect` .

*lpSrcRect*<br/>
Pointe vers la `RECT` structure avec les coordonnées de `CRect` .

*point*<br/>
Spécifie le point d’origine du rectangle à construire. Correspond à l’angle supérieur gauche.

*size*<br/>
Spécifie le déplacement à partir du coin supérieur gauche vers le coin inférieur droit du rectangle à construire.

*topLeft*<br/>
Spécifie la position en haut à gauche de `CRect` .

*bottomRight*<br/>
Spécifie la position en bas à droite de `CRect` .

### <a name="remarks"></a>Remarques

Si aucun argument n’est fourni `left` , `top` les membres,,, `right` et ont la `bottom` valeur 0.

Les `CRect` `const RECT&` constructeurs () et `CRect` ( `LPCRECT` ) effectuent un [CopyRect](#copyrect). Les autres constructeurs initialisent les variables membres de l’objet directement.

### <a name="example"></a>Exemple

```cpp
// default constructor is equivalent to CRect(0, 0, 0, 0)
CRect emptyRect;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

## <a name="crectdeflaterect"></a><a name="deflaterect"></a> CRect ::D eflateRect

`DeflateRect` déflate `CRect` en déplaçant ses côtés vers son centre.

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités pour déflater les côtés gauche et droit de `CRect` .

*y*<br/>
Spécifie le nombre d’unités pour déflater le haut et le bas de `CRect` .

*size*<br/>
[Size](/windows/win32/api/windef/ns-windef-size) ou [CSize](csize-class.md) qui spécifie le nombre d’unités à déflater `CRect` . La `cx` valeur spécifie le nombre d’unités de déflateur des côtés gauche et droit, et la `cy` valeur spécifie le nombre d’unités à déflater le haut et le bas.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` qui spécifie le nombre d’unités à déflater chaque côté.

*l*<br/>
Spécifie le nombre d’unités pour déflater le côté gauche de `CRect` .

*t*<br/>
Spécifie le nombre d’unités pour déflater le haut de `CRect` .

*r*<br/>
Spécifie le nombre d’unités pour déflater le côté droit de `CRect` .

*b*<br/>
Spécifie le nombre d’unités pour déflater le bas de `CRect` .

### <a name="remarks"></a>Remarques

Pour ce faire, `DeflateRect` ajoute des unités à gauche et en haut et soustrait les unités à partir de la droite et du bas. Les paramètres de `DeflateRect` sont des valeurs signées ; les valeurs positives décompressées `CRect` et les valeurs négatives le gonflent.

Les deux premières surcharges déflatent les deux paires de côtés opposés de `CRect` afin que sa largeur totale soit réduite de deux fois *x* (ou `cx` ) et que sa hauteur totale soit réduite de deux fois *y* (ou `cy` ). Les deux autres surcharges déflatent chaque côté de `CRect` indépendamment des autres.

### <a name="example"></a>Exemple

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

## <a name="crectequalrect"></a><a name="equalrect"></a> CRect :: EqualRect

Détermine si `CRect` est égal au rectangle donné.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient les coordonnées de l’angle supérieur gauche et du coin inférieur droit d’un rectangle.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les deux rectangles ont les mêmes valeurs haut, gauche, bas et droite ; Sinon, 0.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

## <a name="crectheight"></a><a name="height"></a> CRect :: Height

Calcule la hauteur de `CRect` en soustrayant la valeur supérieure de la valeur inférieure.

```
int Height() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Hauteur de `CRect` .

### <a name="remarks"></a>Remarques

La valeur obtenue peut être négative.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a> CRect :: InflateRect

`InflateRect` augmente `CRect` en déplaçant ses côtés de son centre.

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités d’augmentation des côtés gauche et droit de `CRect` .

*y*<br/>
Spécifie le nombre d’unités pour augmenter le haut et le bas de `CRect` .

*size*<br/>
[Size](/windows/win32/api/windef/ns-windef-size) ou [CSize](csize-class.md) qui spécifie le nombre d’unités à gonfler `CRect` . La `cx` valeur spécifie le nombre d’unités pour l’augmentation des côtés gauche et droit et la `cy` valeur spécifie le nombre d’unités pour augmenter le haut et le bas.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` qui spécifie le nombre d’unités d’augmentation de chaque côté.

*l*<br/>
Spécifie le nombre d’unités d’augmentation du côté gauche de `CRect` .

*t*<br/>
Spécifie le nombre d’unités d’augmentation du haut de `CRect` .

*r*<br/>
Spécifie le nombre d’unités d’augmentation du côté droit de `CRect` .

*b*<br/>
Spécifie le nombre d’unités d’augmentation du bas de `CRect` .

### <a name="remarks"></a>Remarques

Pour ce faire, `InflateRect` soustrait des unités de gauche et supérieure et ajoute des unités à droite et en bas. Les paramètres de `InflateRect` sont des valeurs signées, les valeurs positives gonflé `CRect` et les valeurs négatives déflatées.

Les deux premières surcharges gonflent les deux paires de côtés opposés de `CRect` afin que sa largeur totale soit augmentée de deux fois *x* (ou `cx` ) et que sa hauteur totale soit augmentée de deux fois *y* (ou `cy` ). Les deux autres surcharges gonflent chaque côté de `CRect` indépendamment des autres.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a> CRect :: IntersectRect

Fait `CRect` égal à l’intersection de deux rectangles existants.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient un rectangle source.

*lpRect2*<br/>
Pointe vers une `RECT` structure ou un `CRect` objet qui contient un rectangle source.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’intersection n’est pas vide ; 0 si l’intersection est vide.

### <a name="remarks"></a>Remarques

L’intersection est le plus grand rectangle contenu dans les deux rectangles existants.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

## <a name="crectisrectempty"></a><a name="isrectempty"></a> CRect :: IsRectEmpty

Détermine si `CRect` est vide.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si `CRect` est vide ; 0 si `CRect` n’est pas vide.

### <a name="remarks"></a>Remarques

Un rectangle est vide si la largeur et/ou la hauteur sont égales à 0 ou négatives. Est différent de `IsRectNull` , qui détermine si toutes les coordonnées du rectangle sont égales à zéro.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a> CRect :: IsRectNull

Détermine si les valeurs supérieure, gauche, inférieure et droite de `CRect` sont toutes égales à 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si `CRect` les valeurs haut, gauche, bas et droite de sont toutes égales à 0 ; sinon, 0.

### <a name="remarks"></a>Remarques

Diffère de `IsRectEmpty` , qui détermine si le rectangle est vide.

### <a name="example"></a>Exemple

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

## <a name="crectmovetox"></a><a name="movetox"></a> CRect :: MoveToX

Appelez cette fonction pour déplacer le rectangle vers la coordonnée x absolue spécifiée par *x*.

```cpp
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x absolue pour l’angle supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a> CRect :: MoveToXY

Appelez cette fonction pour déplacer le rectangle vers les coordonnées absolues x et y spécifiées.

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x absolue pour l’angle supérieur gauche du rectangle.

*y*<br/>
Coordonnée y absolue de l’angle supérieur gauche du rectangle.

*point*<br/>
`POINT`Structure spécifiant l’angle supérieur gauche absolu du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a> CRect :: MoveToY

Appelez cette fonction pour déplacer le rectangle vers la coordonnée y absolue spécifiée par *y*.

```cpp
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Coordonnée y absolue de l’angle supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a> CRect :: NormalizeRect

Normalise `CRect` pour que la hauteur et la largeur soient positives.

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>Remarques

Le rectangle est normalisé pour le positionnement de quatrième quadrant, que Windows utilise généralement pour les coordonnées. `NormalizeRect` compare les valeurs supérieure et inférieure, et les permute si le haut est supérieur au bas. De même, il permute les valeurs de gauche et de droite si le côté gauche est supérieur à la droite. Cette fonction est utile pour gérer différents modes de mappage et rectangles inversés.

> [!NOTE]
> Les `CRect` fonctions membres suivantes requièrent des rectangles normalisés afin de fonctionner correctement [: hauteur](#height), [largeur](#width), [taille](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [opérateur = =](#operator_eq_eq), [opérateur ! =](#operator_neq), [opérateur &#124;](#operator_or), [opérateur &#124;=](#operator_or_eq), [opérateur &](#operator_amp)et [opérateur &=](#operator_amp_eq).

### <a name="example"></a>Exemple

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a> CRect :: OffsetRect

Se déplace `CRect` selon les décalages spécifiés.

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie la quantité à déplacer vers la gauche ou vers la droite. Elle doit être négative pour se déplacer vers la gauche.

*y*<br/>
Spécifie la quantité à déplacer vers le haut ou vers le haut. Elle doit être négative pour pouvoir monter.

*point*<br/>
Contient une structure de [points](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) spécifiant les deux dimensions selon lesquelles se déplacer.

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](csize-class.md) spécifiant les deux dimensions selon lesquelles se déplacer.

### <a name="remarks"></a>Remarques

Déplace les `CRect` unités *x* sur les unités de l’axe x et *y* le long de l’axe y. Les paramètres *x* et *y* sont des valeurs signées, donc vous `CRect` pouvez les déplacer vers la gauche ou vers la droite, vers le haut ou vers le haut.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a> CRect :: Operator LPCRECT convertit un `CRect` en [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Remarques

Lorsque vous utilisez cette fonction, vous n’avez pas besoin de l’opérateur address-of ( **&** ). Cet opérateur est utilisé automatiquement quand vous transmettez un `CRect` objet à une fonction qui attend un `LPCRECT` .

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a> CRect :: Operator LPRECT

Convertit un `CRect` en [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Remarques

Lorsque vous utilisez cette fonction, vous n’avez pas besoin de l’opérateur address-of ( **&** ). Cet opérateur est utilisé automatiquement quand vous transmettez un `CRect` objet à une fonction qui attend un `LPRECT` .

### <a name="example"></a>Exemple

Consultez l’exemple pour [CRect :: Operator LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a> CRect :: Operator =

Affecte la valeur de *srcRect* à `CRect` .

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Paramètres

*srcRect*<br/>
Fait référence à un rectangle source. Peut être un [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` .

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a> CRect :: Operator = =

Détermine si `rect` est égal à `CRect` en comparant les coordonnées de leurs angles supérieur gauche et inférieur droit.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Fait référence à un rectangle source. Peut être un [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si elle est égale ; Sinon, 0.

### <a name="remarks"></a>Remarques

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

## <a name="crectoperator-"></a><a name="operator_neq"></a> CRect :: Operator ! =

Détermine si *Rect* n’est pas égal à `CRect` en comparant les coordonnées de leurs angles supérieur gauche et inférieur droit.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Fait référence à un rectangle source. Peut être un [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` .

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro s’il n’est pas égal à ; Sinon, 0.

### <a name="remarks"></a>Remarques

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

## <a name="crectoperator-"></a><a name="operator_add_eq"></a> CRect :: Operator + =

Les deux premières surcharges se déplacent `CRect` selon les décalages spécifiés.

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités de déplacement du rectangle.

*size*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou objet [CSize](csize-class.md) qui spécifie le nombre d’unités de déplacement du rectangle.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient le nombre d’unités pour l’augmentation de chaque côté de `CRect` .

### <a name="remarks"></a>Remarques

Les valeurs *x* et *y* (ou et) du paramètre `cx` `cy` sont ajoutées à `CRect` .

La troisième surcharge augmente `CRect` par le nombre d’unités spécifiées dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a> CRect :: Operator-=

Les deux premières surcharges se déplacent `CRect` selon les décalages spécifiés.

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités de déplacement du rectangle.

*size*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou objet [CSize](csize-class.md) qui spécifie le nombre d’unités de déplacement du rectangle.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient le nombre d’unités de déflation de chaque côté de `CRect` .

### <a name="remarks"></a>Remarques

Les valeurs *x* et *y* (ou et) du paramètre `cx` `cy` sont soustraites de `CRect` .

La troisième surcharge déflate `CRect` par le nombre d’unités spécifiées dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect).

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a> CRect :: Operator &amp;=

Définit `CRect` égal à l’intersection de `CRect` et `rect` .

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Contient un [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` .

### <a name="remarks"></a>Remarques

L’intersection est le plus grand rectangle contenu dans les deux rectangles.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CRect :: IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a> CRect :: Operator &#124;=

Définit `CRect` égal à l’Union de `CRect` et `rect` .

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Contient un `CRect` ou un [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Remarques

L’Union est le plus petit rectangle qui contient les deux rectangles sources.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a> CRect :: Operator +

Les deux premières surcharges retournent un `CRect` objet qui est égal à `CRect` deplaced par les offsets spécifiés.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités de déplacement de la valeur de retour.

*size*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou objet [CSize](csize-class.md) qui spécifie le nombre d’unités de déplacement de la valeur de retour.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient le nombre d’unités pour augmenter chaque côté de la valeur de retour.

### <a name="return-value"></a>Valeur renvoyée

`CRect`Résultant du déplacement ou de la déflatation `CRect` du nombre d’unités spécifié dans le paramètre.

### <a name="remarks"></a>Remarques

Les paramètres *x* et *y* (ou et) du paramètre `cx` `cy` sont ajoutés à la `CRect` position de.

La troisième surcharge retourne un nouveau `CRect` qui est égal à `CRect` augmenté du nombre d’unités spécifiées dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a> CRect :: Operator-

Les deux premières surcharges retournent un `CRect` objet qui est égal à `CRect` deplaced par les offsets spécifiés.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Structure [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint` objet qui spécifie le nombre d’unités de déplacement de la valeur de retour.

*size*<br/>
Structure ou objet de [taille](/windows/win32/api/windef/ns-windef-size) `CSize` qui spécifie le nombre d’unités de déplacement de la valeur de retour.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un `CRect` objet qui contient le nombre d’unités pour déflater chaque côté de la valeur de retour.

### <a name="return-value"></a>Valeur renvoyée

`CRect`Résultant du déplacement ou de la déflatation `CRect` du nombre d’unités spécifié dans le paramètre.

### <a name="remarks"></a>Remarques

Les paramètres *x* et *y* (ou et) du paramètre `cx` `cy` sont soustraits de la `CRect` position de.

La troisième surcharge retourne un nouveau `CRect` qui est égal au `CRect` déflateur du nombre d’unités spécifié dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect), et non [SubtractRect](#subtractrect).

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a> CRect :: Operator &amp;

Retourne un `CRect` qui est l’intersection entre `CRect` et *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` .

### <a name="return-value"></a>Valeur renvoyée

`CRect`Qui est l’intersection de `CRect` et de *rect2*.

### <a name="remarks"></a>Remarques

L’intersection est le plus grand rectangle contenu dans les deux rectangles.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a> CRect :: Operator &#124;

Retourne un `CRect` qui est l’Union de `CRect` et de *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` .

### <a name="return-value"></a>Valeur renvoyée

`CRect`Qui est l’Union de `CRect` et de *rect2*.

### <a name="remarks"></a>Remarques

L’Union est le plus petit rectangle qui contient les deux rectangles.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a> CRect ::P tInRect

Détermine si le point spécifié se trouve dans `CRect` .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le point se trouve dans `CRect` ; sinon, 0.

### <a name="remarks"></a>Remarques

Un point se trouve dans `CRect` s’il se trouve sur le côté gauche ou supérieur ou se trouve dans les quatre côtés. Un point situé à droite ou en bas est en dehors de `CRect` .

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

## <a name="crectsetrect"></a><a name="setrect"></a> CRect :: SetRect

Définit les dimensions de `CRect` aux coordonnées spécifiées.

```cpp
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x de l’angle supérieur gauche.

*Y1*<br/>
Spécifie la coordonnée y de l’angle supérieur gauche.

*x2*<br/>
Spécifie la coordonnée x de l’angle inférieur droit.

*Y2*<br/>
Spécifie la coordonnée y de l’angle inférieur droit.

### <a name="example"></a>Exemple

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a> CRect :: SetRectEmpty

Crée `CRect` un rectangle null en affectant à toutes les coordonnées la valeur zéro.

```cpp
void SetRectEmpty() throw();
```

### <a name="example"></a>Exemple

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a> CRect :: SIZE

Les `cx` `cy` membres et de la valeur de retour contiennent la hauteur et la largeur de `CRect` .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Objet [CSize](csize-class.md) qui contient la taille de `CRect` .

### <a name="remarks"></a>Remarques

La hauteur ou la largeur peut être négative.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a> CRect :: SubtractRect

Rend les dimensions du `CRect` égal à la soustraction de `lpRectSrc2` `lpRectSrc1` .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRectSrc1*<br/>
Pointe vers la structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou l' `CRect` objet à partir duquel un rectangle doit être soustrait.

*lpRectSrc2*<br/>
Pointe vers la `RECT` structure ou l' `CRect` objet qui doit être soustrait du rectangle vers lequel pointe le paramètre *lpRectSrc1* .

### <a name="return-value"></a>Valeur renvoyée

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Remarques

La soustraction est le plus petit rectangle qui contient tous les points de *lpRectScr1* qui ne sont pas dans l’intersection de *lpRectScr1* et *lpRectScr2*.

Le rectangle spécifié par *lpRectSrc1* sera inchangé si le rectangle spécifié par *lpRectSrc2* ne chevauche pas complètement le rectangle spécifié par *lpRectSrc1* dans au moins l’une des directions x ou y.

Par exemple, si *lpRectSrc1* était (10, 10, 100 100) et *lpRectSrc2* étaient (50, 50, 150 150), le rectangle vers lequel pointe *lpRectSrc1* serait inchangé lorsque la fonction était retournée. Si *lpRectSrc1* était (10, 10, 100 100) et *lpRectSrc2* étaient (50, 10, 150 150), toutefois, le rectangle vers lequel pointe *lpRectSrc1* contiendrait les coordonnées (10, 10, 50 100) lorsque la fonction est retournée.

`SubtractRect` n’est pas le même que [Operator-](#operator_-) ni [Operator-=](#operator_-_eq). Aucun de ces opérateurs n’appelle `SubtractRect` .

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

## <a name="crecttopleft"></a><a name="topleft"></a> CRect :: Left

Les coordonnées sont retournées en tant que référence à un objet [CPoint](cpoint-class.md) contenu dans `CRect` .

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Coordonnées du coin supérieur gauche du rectangle.

### <a name="remarks"></a>Remarques

Vous pouvez utiliser cette fonction pour récupérer ou définir l’angle supérieur gauche du rectangle. Définissez l’angle à l’aide de cette fonction sur le côté gauche de l’opérateur d’assignation.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CRect :: Centerpoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a> CRect :: UnionRect

Rend les dimensions `CRect` égales à l’Union des deux rectangles sources.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Pointe vers un [Rect](/windows/win32/api/windef/ns-windef-rect) ou `CRect` qui contient un rectangle source.

*lpRect2*<br/>
Pointe vers un `RECT` ou contenant `CRect` un rectangle source.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’Union n’est pas vide ; 0 si l’Union est vide.

### <a name="remarks"></a>Remarques

L’Union est le plus petit rectangle qui contient les deux rectangles sources.

Windows ignore les dimensions d’un rectangle vide ; autrement dit, un rectangle qui n’a pas de hauteur ou n’a pas de largeur.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a> CRect :: width

Calcule la largeur de `CRect` en soustrayant la valeur de gauche de la valeur de droite.

```
int Width() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Largeur de `CRect` .

### <a name="remarks"></a>Remarques

La largeur peut être négative.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Voir aussi

[CPoint (classe)](cpoint-class.md)<br/>
[CSize (classe)](csize-class.md)<br/>
[RECTANGULAIRE](/windows/win32/api/windef/ns-windef-rect)
