---
title: Classe CRect
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
ms.openlocfilehash: b99eca7fe3a9c84f8b79ef3d694e27b6dd74dcd9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747058"
---
# <a name="crect-class"></a>Classe CRect

Semblable à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) Windows.

## <a name="syntax"></a>Syntaxe

```
class CRect : public tagRECT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRect::CRect](#crect)|Construit un objet `CRect`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Retourne le point inférieur `CRect`droit de .|
|[CRect::CenterPoint](#centerpoint)|Retourne le point `CRect`central de .|
|[CRect::CopyRect](#copyrect)|Copie les dimensions d’un rectangle source à `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Diminue la largeur et `CRect`la hauteur de .|
|[CRect::EqualRect](#equalrect)|Détermine si `CRect` elle est égale au rectangle donné.|
|[CRect::Hauteur](#height)|Calcule la `CRect`hauteur de .|
|[CRect::InflateRect](#inflaterect)|Augmente la largeur `CRect`et la hauteur de .|
|[CRect::IntersectRect](#intersectrect)|Ensembles `CRect` égaux à l’intersection de deux rectangles.|
|[CRect::IsRectEmpty](#isrectempty)|Détermine s’il `CRect` est vide. `CRect`est vide si la largeur et/ou la hauteur sont de 0.|
|[CRect::IsRectNull](#isrectnull)|Détermine si `top`les `bottom` `left`variables, `right` , et les membres sont tous égaux à 0.|
|[CRect::MoveToX](#movetox)|Passe `CRect` à la x-coordonnées spécifiée.|
|[CRect::MoveToXY](#movetoxy)|Passe `CRect` aux coordonnées x et y spécifiées.|
|[CRect::MoveToy](#movetoy)|Passe `CRect` à la y-coordinate spécifiée.|
|[CRect::NormalizeRect](#normalizerect)|Normalise la hauteur et `CRect`la largeur de .|
|[CRect::OffsetRect](#offsetrect)|Déplace `CRect` par les décalages spécifiés.|
|[CRect::PtInRect](#ptinrect)|Détermine si le point `CRect`spécifié se trouve à l’intérieur .|
|[CRect::SetRect](#setrect)|Définit les `CRect`dimensions de .|
|[CRect::SetRectEmpty](#setrectempty)|Ensemble `CRect` à un rectangle vide (toutes les coordonnées égales à 0).|
|[CRect::Taille](#size)|Calcule la `CRect`taille de .|
|[CRect::SoustractRect](#subtractrect)|Soustrait un rectangle d’un autre.|
|[CRect::TopLeft](#topleft)|Retourne le point supérieur `CRect`gauche de .|
|[CRect::UnionRect](#unionrect)|Ensembles `CRect` égaux à l’union de deux rectangles.|
|[CRect::Largeur](#width)|Calcule la `CRect`largeur de .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRect::opérateur -](#operator_-)|Soustrait les décalages `CRect` donnés `CRect` ou se `CRect`dégonfle et renvoie le résultat .|
|[CRect::opérateur LPCRECT](#operator_lpcrect)|Convertit `CRect` en `LPCRECT`.|
|[CRect::opérateur LPRECT](#operator_lprect)|Convertit `CRect` en `LPRECT`.|
|[CRect::opérateur !](#operator_neq)|Détermine si `CRect` n’est pas égal à un rectangle.|
|[CRect::opérateur&amp;](#operator_amp)|Crée l’intersection et `CRect` un rectangle `CRect`et renvoie le résultat .|
|[CRect::opérateur&amp;=](#operator_amp_eq)|Ensembles `CRect` égaux à `CRect` l’intersection et un rectangle.|
|[CRect::opérateur &#124;](#operator_or)|Crée l’union et `CRect` un rectangle `CRect`et renvoie le résultat .|
|[CRect::opérateur &#124;](#operator_or_eq)|Ensembles `CRect` égaux à `CRect` l’union et à un rectangle.|
|[CRect::opérateur](#operator_add)|Ajoute les compensations `CRect` données `CRect` ou gonfle `CRect`et retourne le résultat .|
|[CRect::opérateur](#operator_add_eq)|Ajoute les compensations `CRect` spécifiées `CRect`ou gonfle .|
|[CRect::opérateur](#operator_eq)|Copie les dimensions d’un rectangle à `CRect`.|
|[CRect::opérateur -MD](#operator_-_eq)|Soustrait les décalages `CRect` spécifiés `CRect`ou dégonfle.|
|[CRect::opérateur](#operator_eq_eq)|Détermine si `CRect` elle est égale à un rectangle.|

## <a name="remarks"></a>Notes

`CRect`comprend également des fonctions de membre pour manipuler des `CRect` objets et des structures Windows. `RECT`

Un `CRect` objet peut être passé comme `RECT` un `LPCRECT`paramètre de fonction où qu’une structure, ou `LPRECT` peut être passé.

> [!NOTE]
> Cette classe est `tagRECT` dérivée de la structure. (Le `tagRECT` nom est un nom moins couramment `RECT` utilisé pour la structure.) Cela signifie que les`left` `top`membres `right`des `bottom`données `RECT` ( , , `CRect`, et ) de la structure sont des membres de données accessibles de .

Un `CRect` contient des variables de membre qui définissent les points supérieurs gauche et en bas-droit d’un rectangle.

Lors de `CRect`la spécifier un , vous devez faire attention à le construire de sorte qu’il soit normalisé - en d’autres termes, de sorte que la valeur de la coordonnées gauche est inférieure à la droite et le haut est inférieur au fond. Par exemple, un haut à gauche de (10,10) et en bas à droite de (20,20) définit un rectangle normalisé, mais un haut à gauche de (20,20) et en bas à droite de (10,10) définit un rectangle non normalisé. Si le rectangle n’est `CRect` pas normalisé, de nombreuses fonctions de membre peuvent retourner des résultats incorrects. (Voir [CRect::NormalizeRect](#normalizerect) pour une liste de ces fonctions.) Avant d’appeler une fonction qui nécessite des rectangles normalisés, vous `NormalizeRect` pouvez normaliser les rectangles non normalisés en appelant la fonction.

Faites preuve de `CRect` prudence lorsque vous manipulez un avec le [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) et [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) fonctions membres. Si le mode de cartographie d’un contexte d’affichage `MM_LOENGLISH`est `CDC::DPtoLP` tel que `CRect` le y-extent est négatif, comme dans, alors transformer le de sorte que son dessus est plus grand que le fond. Fonctions telles `Height` `Size` que et retournera ensuite des `CRect`valeurs négatives pour la hauteur de la transformation, et le rectangle sera non normalisé.

Lorsque vous utilisez `CRect` des opérateurs surchargés, `CRect`le premier opérande doit être un ; la seconde peut être soit une `CRect` structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagRECT`

`CRect`

## <a name="requirements"></a>Spécifications

**En-tête:** atltypes.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::BottomRight

Les coordonnées sont retournées en référence à un `CRect`objet [CPoint](cpoint-class.md) qui est contenu dans .

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées du coin inférieur droit du rectangle.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour obtenir ou régler le coin inférieur droit du rectangle. Réglez le coin en utilisant cette fonction sur le côté gauche de l’opérateur d’affectation.

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::CenterPoint

Calcule le point `CRect` central de en ajoutant les valeurs de gauche et de droite et de diviser par deux, et en ajoutant les valeurs supérieures et inférieures et en divisant par deux.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un `CPoint` objet qui est `CRect`le point central de .

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

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::CopyRect

Copie `lpSrcRect` le `CRect`rectangle en .

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Paramètres

*lpSrcRect*<br/>
Points à la structure `CRect` ou objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui doit être copié.

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

## <a name="crectcrect"></a><a name="crect"></a>CRect::CRect

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

*L*<br/>
Spécifie la `CRect`position gauche de .

*t*<br/>
Specifie le `CRect`sommet de .

*r*<br/>
Spécifie la `CRect`bonne position de .

*B*<br/>
Specifie le `CRect`fond de .

*srcRect*<br/>
Se réfère à la structure [RECT](/windows/win32/api/windef/ns-windef-rect) avec les coordonnées pour `CRect`.

*lpSrcRect*<br/>
Points à `RECT` la structure avec `CRect`les coordonnées pour .

*Point*<br/>
Spécifie le point d’origine pour la construction du rectangle. Correspond au coin supérieur gauche.

*size*<br/>
Spécifie le déplacement du coin supérieur gauche jusqu’au coin inférieur-droit du rectangle à construire.

*topLeft*<br/>
Spécifie la position `CRect`de haut à gauche de .

*bottomRight*<br/>
Spécifie la position `CRect`en bas à droite de .

### <a name="remarks"></a>Notes

Si aucun argument `left`n’est donné, , `top`, `right`et `bottom` les membres ne sont pas initialisés.

Les `CRect``const RECT&`constructeurs `CRect``LPCRECT`() et ) exécutent un [CopyRect](#copyrect). Les autres constructeurs initialisent directement les variables membres de l’objet.

### <a name="example"></a>Exemple

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::DeflateRect

`DeflateRect`se dégonfle `CRect` en déplaçant ses côtés vers son centre.

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités pour dégonfler les côtés gauche et droit de `CRect`.

*y*<br/>
Spécifie le nombre d’unités pour `CRect`dégonfler le haut et le bas de .

*size*<br/>
Un [SIZE](/windows/win32/api/windef/ns-windef-size) ou [CSize](csize-class.md) qui spécifie `CRect`le nombre d’unités à dégonfler. La `cx` valeur spécifie le nombre d’unités pour `cy` dégonfler les côtés gauche et droit et la valeur spécifie le nombre d’unités pour dégonfler le haut et le bas.

*lpRect*<br/>
Indique une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou `CRect` qui spécifie le nombre d’unités à dégonfler de chaque côté.

*L*<br/>
Spécifie le nombre d’unités pour `CRect`dégonfler le côté gauche de .

*t*<br/>
Specifie le nombre d’unités pour `CRect`dégonfler le haut de .

*r*<br/>
Spécifie le nombre d’unités pour `CRect`dégonfler le côté droit de .

*B*<br/>
Spécifie le nombre d’unités `CRect`pour dégonfler le bas de .

### <a name="remarks"></a>Notes

Pour ce `DeflateRect` faire, ajoute des unités à gauche et en haut et soustrait les unités de la droite et du bas. Les paramètres `DeflateRect` sont des valeurs signées; valeurs positives se `CRect` dégonflent et les valeurs négatives la gonflent.

Les deux premières surcharges dégonflent les `CRect` deux paires de côtés opposés `cx`de sorte que sa largeur totale `cy`est diminuée de deux fois *x* (ou ) et sa hauteur totale est diminuée de deux fois *y* (ou ). Les deux autres surcharges se dégonflent de chaque côté de `CRect` indépendamment des autres.

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

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::EqualRect

Détermine si `CRect` elle est égale au rectangle donné.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une structure ou `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient les coordonnées du coin supérieur gauche et inférieur-droit d’un rectangle.

### <a name="return-value"></a>Valeur de retour

Nonzero si les deux rectangles ont les mêmes valeurs supérieures, gauche, inférieures et droites; sinon 0.

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

## <a name="crectheight"></a><a name="height"></a>CRect::Hauteur

Calcule la `CRect` hauteur de en soustrayant la valeur supérieure de la valeur inférieure.

```
int Height() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur `CRect`de .

### <a name="remarks"></a>Notes

La valeur qui en résulte peut être négative.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::InflateRect

`InflateRect`gonfle `CRect` en éloignant ses côtés de son centre.

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Specifie le nombre d’unités pour gonfler les côtés gauche et droit de `CRect`.

*y*<br/>
Spécifie le nombre d’unités `CRect`pour gonfler le haut et le bas de .

*size*<br/>
Un [SIZE](/windows/win32/api/windef/ns-windef-size) ou [CSize](csize-class.md) qui spécifie le nombre d’unités à gonfler. `CRect` La `cx` valeur spécifie le nombre d’unités `cy` pour gonfler les côtés gauche et droit et la valeur spécifie le nombre d’unités pour gonfler le haut et le bas.

*lpRect*<br/>
Indique une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou `CRect` qui spécifie le nombre d’unités pour gonfler chaque côté.

*L*<br/>
Spécifie le nombre d’unités `CRect`pour gonfler le côté gauche de .

*t*<br/>
Spécifie le nombre d’unités pour gonfler le haut de `CRect`.

*r*<br/>
Spécifie le nombre d’unités `CRect`pour gonfler le côté droit de .

*B*<br/>
Spécifie le nombre d’unités pour gonfler le bas de `CRect`.

### <a name="remarks"></a>Notes

Pour ce `InflateRect` faire, soustraite les unités de la gauche et du haut et ajoute des unités à droite et en bas. Les paramètres `InflateRect` sont des valeurs signées; valeurs positives `CRect` gonflent et les valeurs négatives le dégonflent.

Les deux premières surcharges gonflent les `CRect` deux paires de côtés opposés `cx`de sorte que sa largeur totale `cy`est augmentée de deux fois *x* (ou ) et sa hauteur totale est augmentée de deux fois *y* (ou ). Les deux autres surcharges gonflent de chaque côté de `CRect` indépendamment de l’autre.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::IntersectRect

Fait `CRect` un égal à l’intersection de deux rectangles existants.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Indique une structure OU `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient un rectangle source.

*lpRect2*<br/>
Indique une `RECT` structure `CRect` ou un objet qui contient un rectangle source.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’intersection n’est pas vide; 0 si l’intersection est vide.

### <a name="remarks"></a>Notes

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::IsRectEmpty

Détermine s’il `CRect` est vide.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Nonzero `CRect` si est vide; 0 `CRect` s’il n’est pas vide.

### <a name="remarks"></a>Notes

Un rectangle est vide si la largeur et/ou la hauteur sont 0 ou négatives. Diffère de `IsRectNull`, qui détermine si toutes les coordonnées du rectangle sont nulles.

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

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::IsRectNull

Détermine si les valeurs supérieures, gauche, `CRect` inférieure et droite sont toutes égales à 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valeur de retour

Nonzero `CRect`si «les valeurs supérieures, gauche, en bas et à droite sont toutes égales à 0; sinon 0.

### <a name="remarks"></a>Notes

Diffère de `IsRectEmpty`, qui détermine si le rectangle est vide.

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

## <a name="crectmovetox"></a><a name="movetox"></a>CRect::MoveToX

Appelez cette fonction pour déplacer le rectangle vers la x-coordonnées absolue spécifiée par *x*.

```cpp
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Le x-coordonner absolu pour le coin supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>CRect::MoveToXY

Appelez cette fonction pour déplacer le rectangle vers les coordonnées X et y spécifiées.

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Le x-coordonner absolu pour le coin supérieur gauche du rectangle.

*y*<br/>
Le y-coordinate absolu pour le coin supérieur gauche du rectangle.

*Point*<br/>
Une `POINT` structure spécifiant le coin supérieur gauche absolu du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>CRect::MoveToy

Appelez cette fonction pour déplacer le rectangle vers le y-coordinate absolu spécifié par *y*.

```cpp
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Le y-coordinate absolu pour le coin supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::NormalizeRect

Normalise `CRect` de sorte que la hauteur et la largeur sont positives.

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>Notes

Le rectangle est normalisé pour le positionnement du quatrième quadrant, que Windows utilise généralement pour les coordonnées. `NormalizeRect`compare les valeurs supérieures et inférieures, et les échange si le dessus est supérieur au bas. De même, il échange les valeurs gauche et droite si la gauche est supérieure à la droite. Cette fonction est utile lorsqu’il s’agit de différents modes de cartographie et de rectangles inversés.

> [!NOTE]
> Les `CRect` fonctions membres suivantes nécessitent des rectangles normalisés afin de fonctionner correctement : [Hauteur,](#height) [Largeur,](#width) [Taille](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [opérateur](#operator_eq_eq), [opérateur ! , opérateur](#operator_neq) [&#124;](#operator_or), [opérateur &#124;](#operator_or_eq), [opérateur &](#operator_amp), et [opérateur &](#operator_amp_eq).

### <a name="example"></a>Exemple

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::OffsetRect

Déplace `CRect` par les décalages spécifiés.

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le montant à déplacer à gauche ou à droite. Il doit être négatif de se déplacer à gauche.

*y*<br/>
Spécifie le montant à déplacer vers le haut ou vers le bas. Il doit être négatif de monter.

*Point*<br/>
Contient une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) spécifiant les deux dimensions par lesquelles se déplacer.

*size*<br/>
Contient une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](csize-class.md) spécifiant les deux dimensions par lesquelles se déplacer.

### <a name="remarks"></a>Notes

Déplace `CRect` *x* unités le long de l’axe x et *y* unités le long de l’axe y. Les paramètres *x* et *y* sont `CRect` des valeurs signées, de sorte qu’ils peuvent être déplacés à gauche ou à droite et à la hausse ou vers le bas.

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::opérateur LPCRECT Convertit un `CRect` à un [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Notes

Lorsque vous utilisez cette fonction, vous n’avez**&** pas besoin de l’adresse de l’opérateur . Cet opérateur sera automatiquement utilisé lorsque `CRect` vous passez un `LPCRECT`objet à une fonction qui s’attend à un .

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::opérateur LPRECT

Convertit `CRect` un [en LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Notes

Lorsque vous utilisez cette fonction, vous n’avez**&** pas besoin de l’adresse de l’opérateur . Cet opérateur sera automatiquement utilisé lorsque `CRect` vous passez un `LPRECT`objet à une fonction qui s’attend à un .

### <a name="example"></a>Exemple

Voir l’exemple pour [CRect::opérateur LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::opérateur

Assigne *srcRect* à `CRect`.

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Paramètres

*srcRect*<br/>
Se réfère à un rectangle source. Peut être un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou .

### <a name="example"></a>Exemple

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::opérateur

Détermine si `rect` elle `CRect` est égale en comparant les coordonnées de leurs coins supérieurs gauche et inférieurs à droite.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Se réfère à un rectangle source. Peut être un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou .

### <a name="return-value"></a>Valeur de retour

Nonzero si égal; sinon 0.

### <a name="remarks"></a>Notes

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

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::opérateur !

Détermine si *le rect* `CRect` n’est pas égal en comparant les coordonnées de leurs coins supérieurs gauche et inférieur-droit.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Se réfère à un rectangle source. Peut être un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou .

### <a name="return-value"></a>Valeur de retour

Nonzero sinon égal; sinon 0.

### <a name="remarks"></a>Notes

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::opérateur

Les deux premières surcharges se déplacent `CRect` par les décalages spécifiés.

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités pour déplacer le rectangle.

*size*<br/>
Une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](csize-class.md) qui spécifie le nombre d’unités pour déplacer le rectangle.

*lpRect*<br/>
Indique une structure ou `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient `CRect`le nombre d’unités pour gonfler chaque côté de .

### <a name="remarks"></a>Notes

Les valeurs *x* et *y* `cy`du paramètre `CRect`sont `cx` ajoutées à .

La troisième surcharge `CRect` se gonfle par le nombre d’unités spécifiées dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::opérateur -MD

Les deux premières surcharges se déplacent `CRect` par les décalages spécifiés.

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités pour déplacer le rectangle.

*size*<br/>
Une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](csize-class.md) qui spécifie le nombre d’unités pour déplacer le rectangle.

*lpRect*<br/>
Indique une structure ou `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient le `CRect`nombre d’unités pour dégonfler de chaque côté de .

### <a name="remarks"></a>Notes

Les valeurs *x* *y* et y `cx` `cy`(ou) du paramètre sont soustraites de `CRect`.

La troisième surcharge se `CRect` dégonfle par le nombre d’unités spécifiées dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect).

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::opérateur&amp;=

Ensembles `CRect` égaux à `CRect` `rect`l’intersection de et .

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Contient un [RECT](/windows/win32/api/windef/ns-windef-rect) ou `CRect`.

### <a name="remarks"></a>Notes

L’intersection est le plus grand rectangle qui est contenu dans les deux rectangles.

> [!NOTE]
> Les deux rectangles doivent être normalisés ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRect:IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::opérateur &#124;

Ensembles `CRect` égaux à `CRect` `rect`l’union et .

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Contient `CRect` un ou [RECT](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles sources.

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

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::opérateur

Les deux premières surcharges `CRect` renvoient un `CRect` objet qui est égal aux décalages spécifiés.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](cpoint-class.md) qui spécifie le nombre d’unités pour déplacer la valeur de retour.

*size*<br/>
Une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](csize-class.md) qui précise le nombre d’unités pour déplacer la valeur de retour.

*lpRect*<br/>
Indique une structure ou `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient le nombre d’unités pour gonfler chaque côté de la valeur de retour.

### <a name="return-value"></a>Valeur de retour

Le `CRect` résultat du déplacement `CRect` ou du gonflage par le nombre d’unités spécifiées dans le paramètre.

### <a name="remarks"></a>Notes

Les paramètres *x* et *y* `cy`du paramètre (ou) `CRect` `cx` sont ajoutés à la position de '.

La troisième surcharge renvoie une `CRect` `CRect` nouvelle qui est égale à gonflée par le nombre d’unités spécifiées dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::opérateur -

Les deux premières surcharges `CRect` renvoient un `CRect` objet qui est égal aux décalages spécifiés.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Une [POINT](/windows/win32/api/windef/ns-windef-point) structure `CPoint` OU un objet POINT qui spécifie le nombre d’unités pour déplacer la valeur de retour.

*size*<br/>
Une [SIZE](/windows/win32/api/windef/ns-windef-size) structure `CSize` OU un objet SIZE qui spécifie le nombre d’unités pour déplacer la valeur de retour.

*lpRect*<br/>
Indique une structure ou `CRect` un objet [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient le nombre d’unités pour dégonfler chaque côté de la valeur de retour.

### <a name="return-value"></a>Valeur de retour

Le `CRect` résultat du déplacement `CRect` ou du dégonflage par le nombre d’unités spécifiées dans le paramètre.

### <a name="remarks"></a>Notes

Les paramètres *x* *y* et y `cx` `cy`du paramètre (ou) `CRect`sont soustraits de la position de '.

La troisième surcharge renvoie une `CRect` `CRect` nouvelle qui est égale à dégonflée par le nombre d’unités spécifiées dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect), pas [SoustractRect](#subtractrect).

### <a name="example"></a>Exemple

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::opérateur&amp;

Retourne `CRect` un qui est `CRect` l’intersection de et *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [RECT](/windows/win32/api/windef/ns-windef-rect) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

A `CRect` qui est `CRect` l’intersection de et *rect2*.

### <a name="remarks"></a>Notes

L’intersection est le plus grand rectangle qui est contenu dans les deux rectangles.

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

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::opérateur &#124;

Retourne `CRect` un qui est `CRect` l’union de *et rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [RECT](/windows/win32/api/windef/ns-windef-rect) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

A `CRect` qui est `CRect` l’union de *et rect2*.

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles.

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

## <a name="crectptinrect"></a><a name="ptinrect"></a>CRect::PtInRect

Détermine si le point `CRect`spécifié se trouve à l’intérieur .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Contient une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint.](cpoint-class.md)

### <a name="return-value"></a>Valeur de retour

Nonzero si le `CRect`point se trouve à l’intérieur; sinon 0.

### <a name="remarks"></a>Notes

Un point `CRect` est à l’intérieur s’il se trouve sur le côté gauche ou supérieur ou est dans les quatre côtés. Un point sur le côté `CRect`droit ou inférieur est à l’extérieur .

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

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

Définit les `CRect` dimensions des coordonnées spécifiées.

```cpp
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la x-coordonnées du coin supérieur gauche.

*y1 (en)*<br/>
Spécifie la y-coordonnées du coin supérieur gauche.

*x2*<br/>
Spécifie la x-coordonnées du coin inférieur droit.

*y2*<br/>
Spécifie la y-coordonnées du coin inférieur droit.

### <a name="example"></a>Exemple

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::SetRectEmpty

Fait `CRect` un rectangle nul en définissant toutes les coordonnées à zéro.

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

## <a name="crectsize"></a><a name="size"></a>CRect::SIZE

La `cx` `cy` valeur de retour et les membres `CRect`contiennent la hauteur et la largeur de .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un objet [CSize](csize-class.md) qui `CRect`contient la taille de .

### <a name="remarks"></a>Notes

La hauteur ou la largeur peuvent être négatives.

> [!NOTE]
> Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::SoustractRect

Rend les dimensions `CRect` de l’égal `lpRectSrc2` à `lpRectSrc1`la soustraction de .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRectSrc1*<br/>
Points à la structure `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou objet à partir duquel un rectangle doit être soustrait.

*lpRectSrc2*<br/>
Points à `RECT` la `CRect` structure ou l’objet qui doit être soustrait du rectangle pointé vers le paramètre *lpRectSrc1.*

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

La soustraction est le plus petit rectangle qui contient tous les points dans *lpRectScr1* qui ne sont pas dans *l’intersection de lpRectScr1* et *lpRectScr2*.

Le rectangle spécifié par *lpRectSrc1* sera inchangé si le rectangle spécifié par *lpRectSrc2* ne chevauche pas complètement le rectangle spécifié par *lpRectSrc1* dans au moins une des directions x ou y.

Par exemple, si *lpRectSrc1* étaient (10,10, 100.100) et *lpRectSrc2* étaient (50,50, 150.150), le rectangle indiqué par *lpRectSrc1* serait inchangé lorsque la fonction est revenue. Si *lpRectSrc1* étaient (10,10, 100.100) et *lpRectSrc2* étaient (50,10, 150.150), cependant, le rectangle indiqué par *lpRectSrc1* contiendrait les coordonnées (10,10, 50.100) quand la fonction retournée.

`SubtractRect`n’est pas la même chose que [l’opérateur -](#operator_-) ni [l’opérateur -](#operator_-_eq). Aucun de ces `SubtractRect`opérateurs n’appelle jamais .

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

## <a name="crecttopleft"></a><a name="topleft"></a>CRect::TopLeft

Les coordonnées sont retournées en référence à un `CRect`objet [CPoint](cpoint-class.md) qui est contenu dans .

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées du coin supérieur gauche du rectangle.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour obtenir ou définir le coin supérieur gauche du rectangle. Réglez le coin en utilisant cette fonction sur le côté gauche de l’opérateur d’affectation.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRect::CenterPoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::UnionRect

Rend les `CRect` dimensions de l’égal à l’union des deux rectangles source.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Points à un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou qui contient un rectangle source.

*lpRect2*<br/>
Points à `RECT` `CRect` un ou qui contient un rectangle source.

### <a name="return-value"></a>Valeur de retour

Nonzero si le syndicat n’est pas vide; 0 si le syndicat est vide.

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles sources.

Windows ignore les dimensions d’un rectangle vide; c’est-à-dire un rectangle qui n’a pas de hauteur ou qui n’a pas de largeur.

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

## <a name="crectwidth"></a><a name="width"></a>CRect::Largeur

Calcule la `CRect` largeur de en soustrayant la valeur gauche de la valeur droite.

```
int Width() const throw();
```

### <a name="return-value"></a>Valeur de retour

La largeur `CRect`de .

### <a name="remarks"></a>Notes

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

[Classe CPoint](cpoint-class.md)<br/>
[Classe CSize](csize-class.md)<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect)
