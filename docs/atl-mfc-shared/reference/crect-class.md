---
title: CRect, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8033ceb709ab66c37e1801cd4033e6830467f2b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808613"
---
# <a name="crect-class"></a>CRect, classe

Similaire à un Windows [RECT](../../mfc/reference/rect-structure.md) structure.

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
|[CRect::BottomRight](#bottomright)|Retourne le point en bas à droite de `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Retourne le point central de `CRect`.|
|[CRect::CopyRect](#copyrect)|Copie les dimensions d’un rectangle source à `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Diminue la largeur et la hauteur de `CRect`.|
|[CRect::EqualRect](#equalrect)|Détermine si `CRect` est égal au rectangle donné.|
|[CRect::Height](#height)|Calcule la hauteur de `CRect`.|
|[CRect::InflateRect](#inflaterect)|Augmente la largeur et la hauteur de `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Jeux `CRect` égal à l’intersection de deux rectangles.|
|[CRect::IsRectEmpty](#isrectempty)|Détermine si `CRect` est vide. `CRect` est vide si la largeur et/ou la hauteur est 0.|
|[CRect::IsRectNull](#isrectnull)|Détermine si le `top`, `bottom`, `left`, et `right` les variables membres sont toujours égaux à 0.|
|[CRect::MoveToX](#movetox)|Déplace `CRect` à la coordonnée x spécifiée.|
|[CRect::MoveToXY](#movetoxy)|Déplace `CRect` aux coordonnées x et y spécifiées.|
|[CRect::MoveToY](#movetoy)|Déplace `CRect` à la coordonnée y spécifiée.|
|[CRect::NormalizeRect](#normalizerect)|Normalise la hauteur et largeur de `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Déplace `CRect` par offsets spécifiés.|
|[CRect::PtInRect](#ptinrect)|Détermine si le point spécifié se trouve dans `CRect`.|
|[CRect::SetRect](#setrect)|Définit les dimensions de `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Jeux `CRect` à un rectangle vide (toutes les coordonnées égal à 0).|
|[CRect::Size](#size)|Calcule la taille de `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Soustrait un rectangle à partir d’un autre.|
|[CRect::TopLeft](#topleft)|Retourne le point supérieur gauche de `CRect`.|
|[CRect::UnionRect](#unionrect)|Jeux `CRect` égal à l’union de deux rectangles.|
|[CRect::Width](#width)|Calcule la largeur de `CRect`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRect::operator-](#operator_-)|Soustrait les décalages donnés à partir de `CRect` ou dégonfle `CRect` et retourne le résultat `CRect`.|
|[CRect::operator LPCRECT](#operator_lpcrect)|Convertit `CRect` en `LPCRECT`.|
|[CRect::operator LPRECT](#operator_lprect)|Convertit `CRect` en `LPRECT`.|
|[CRect::operator ! =](#operator_neq)|Détermine si `CRect` n’est pas égal à un rectangle.|
|[CRect::operator &amp;](#operator_amp)|Crée l’intersection de `CRect` et un rectangle et retourne le résultat `CRect`.|
|[CRect::operator &amp;=](#operator_amp_eq)|Jeux `CRect` égal à l’intersection de `CRect` et un rectangle.|
|[CRect::operator |](#operator_or)|Crée l’union de `CRect` et un rectangle et retourne le résultat `CRect`.|
|[CRect::operator |=](#operator_or_eq)|Jeux `CRect` égal à l’union de `CRect` et un rectangle.|
|[CRect::operator +](#operator_add)|Ajoute les décalages donnés à `CRect` ou augmente `CRect` et retourne le résultat `CRect`.|
|[CRect::operator +=](#operator_add_eq)|Ajoute des offsets spécifiés au `CRect` ou augmente `CRect`.|
|[CRect::operator =](#operator_eq)|Copie les dimensions d’un rectangle à `CRect`.|
|[CRect::operator =](#operator_-_eq)|Soustrait des offsets spécifiés à partir de `CRect` ou dégonfle `CRect`.|
|[CRect::operator ==](#operator_eq_eq)|Détermine si `CRect` est égal à un rectangle.|

## <a name="remarks"></a>Notes

`CRect` comprend également des fonctions de membre pour manipuler `CRect` objets et Windows `RECT` structures.

Un `CRect` objet peut être passé comme paramètre de fonction partout où un `RECT` structure, `LPCRECT`, ou `LPRECT` peuvent être passés.

> [!NOTE]
>  Cette classe est dérivée de la `tagRECT` structure. (Le nom `tagRECT` est un nom moins couramment utilisés pour le `RECT` structure.) Cela signifie que les membres de données (`left`, `top`, `right`, et `bottom`) de la `RECT` structure sont membres de données accessibles de `CRect`.

Un `CRect` contient des variables de membres qui définissent les points en haut à gauche et en bas à droite d’un rectangle.

Lorsque vous spécifiez un `CRect`, vous devez être attentif à la construire afin qu’il est normalisé — en d’autres termes, tel que la valeur de la coordonnée gauche est inférieure à droite et le haut est inférieure à la partie inférieure. Par exemple, un haut à gauche de (10,10) et bas à droite de (20,20) définit un rectangle normalisé, mais un haut à gauche de (20,20) et bas à droite de (10,10) définit un rectangle non normalisée. Si le rectangle n’est pas normalisé, nombreuses `CRect` fonctions membres peuvent retourner des résultats incorrects. (Consultez [CRect::NormalizeRect](#normalizerect) pour obtenir la liste de ces fonctions.) Avant d’appeler une fonction qui nécessite des rectangles normalisées, vous pouvez normaliser non normalisée des rectangles en appelant le `NormalizeRect` (fonction).

Soyez prudent lors de la manipulation un `CRect` avec la [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) et [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) fonctions membres. Si le mode de mappage d’un contexte d’affichage est comme l’étendue y est négatif, comme dans `MM_LOENGLISH`, puis `CDC::DPtoLP` transformera le `CRect` afin que son supérieur est supérieure à la partie inférieure. Les fonctions comme `Height` et `Size` retournera ensuite les valeurs négatives pour la hauteur de transformée `CRect`, et le rectangle sera non normalisée.  


Quand à l’aide de surchargé `CRect` opérateurs, le premier opérande doit être un `CRect`; la seconde peut être soit un [RECT](../../mfc/reference/rect-structure.md) structure ou un `CRect` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagRECT`

`CRect`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes.h

##  <a name="bottomright"></a>  CRect::BottomRight

Les coordonnées sont retournées sous la forme d’une référence à un [CPoint](cpoint-class.md) objet qui est contenue dans `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées de l’angle inférieur droit du rectangle.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour obtenir ou définir le coin inférieur droit du rectangle. Définir l’angle à l’aide de cette fonction sur le côté gauche de l’opérateur d’assignation.

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

##  <a name="centerpoint"></a>  CRect::CenterPoint

Calcule le point central de `CRect` en ajoutant les valeurs de gauche et droite et division par deux et les valeurs supérieure et inférieure divisant par deux.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un `CPoint` objet qui est le point central de `CRect`.

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

##  <a name="copyrect"></a>  CRect::CopyRect

Copie le `lpSrcRect` rectangle dans `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw(); 
```

### <a name="parameters"></a>Paramètres

*lpSrcRect*<br/>
Pointe vers le [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet doit être copié.

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


##  <a name="crect"></a>  CRect::CRect

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
Spécifie la position gauche de `CRect`.

*t*<br/>
Spécifie la partie supérieure de `CRect`.

*r*<br/>
Spécifie la position droite de `CRect`.

*b*<br/>
Spécifie la partie inférieure de `CRect`.

*srcRect*<br/>
Fait référence à la [RECT](../../mfc/reference/rect-structure.md) structure avec les coordonnées pour `CRect`.

*lpSrcRect*<br/>
Pointe vers le `RECT` structure avec les coordonnées pour `CRect`.

*point*<br/>
Spécifie le point d’origine pour le rectangle doit être construit. Correspond à l’angle supérieur gauche.

*size*<br/>
Spécifie la distance de déplacement à partir de l’angle supérieur gauche au coin inférieur droit du rectangle doit être construit.

*topLeft*<br/>
Spécifie la position de l’angle supérieur gauche de `CRect`.

*bottomRight*<br/>
Spécifie la position de l’angle inférieur droit de `CRect`.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni, `left`, `top`, `right`, et `bottom` membres ne sont pas initialisés.

Le `CRect`(`const RECT&`) et `CRect`(`LPCRECT`) constructeurs effectuer un [CopyRect](#copyrect). Les autres constructeurs initialisent les variables de membre de l’objet directement.

### <a name="example"></a>Exemple

```cpp  
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT stucture
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

##  <a name="deflaterect"></a>  CRect::DeflateRect

`DeflateRect` dégonfle `CRect` en déplaçant ses côtés vers son centre.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités à deflate gauche et droite du `CRect`.

*y*<br/>
Spécifie le nombre d’unités à deflate haut et bas de `CRect`.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) ou [CSize](csize-class.md) qui spécifie le nombre d’unités à deflate `CRect`. Le `cx` valeur spécifie le nombre d’unités à compresser les côtés gauche et droite et la `cy` valeur spécifie le nombre d’unités à deflate haut et bas.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` qui spécifie le nombre d’unités à deflate chaque côté.

*l*<br/>
Spécifie le nombre d’unités à compresser le côté gauche de `CRect`.

*t*<br/>
Spécifie le nombre d’unités à deflate haut de `CRect`.

*r*<br/>
Spécifie le nombre d’unités à compresser le côté droit de `CRect`.

*b*<br/>
Spécifie le nombre d’unités à deflate bas de `CRect`.

### <a name="remarks"></a>Notes

Pour ce faire, `DeflateRect` ajoute des unités vers la gauche et le haut et soustrait des unités de la droite et bas. Les paramètres de `DeflateRect` sont signés valeurs ; les valeurs positives deflate `CRect` et valeurs négatives la majoration.

Tout d’abord deux surcharges deflate les deux paires de côtés opposés de `CRect` afin que sa largeur totale est réduite par deux fois *x* (ou `cx`) et sa hauteur totale est réduite par deux fois *y* () ou `cy`). Les deux autres surcharges deflate chaque côté de `CRect` indépendamment des autres.

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

##  <a name="equalrect"></a>  CRect::EqualRect

Détermine si `CRect` est égal au rectangle donné.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient les coordonnées du coin supérieur gauche et inférieur droit d’un rectangle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les deux rectangles ont les même haut, gauche, bas et les valeurs appropriées ; sinon 0.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

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

##  <a name="height"></a>  CRect::Height

Calcule la hauteur de `CRect` en soustrayant la valeur supérieure à partir de la valeur du bas.

```
int Height() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur de `CRect`.

### <a name="remarks"></a>Notes

La valeur résultante peut être négative.

> [!NOTE]
>  Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) à normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

```cpp  
   CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

   // nHt is now 40
   ASSERT(nHt == 40);   
```


##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect` augmente `CRect` en privilégiant ses côtés en son centre.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie le nombre d’unités augmentation de la gauche et droite du `CRect`.

*y*<br/>
Spécifie le nombre d’unités vers le haut et bas de la majoration `CRect`.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) ou [CSize](csize-class.md) qui spécifie le nombre d’unités de la majoration `CRect`. Le `cx` valeur spécifie le nombre d’unités pour les côtés gauche et droit de la majoration et `cy` valeur spécifie le nombre d’unités de la majoration haut et bas.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` qui spécifie le nombre d’unités de chaque côté de la majoration.

*l*<br/>
Spécifie le nombre d’unités pour le côté gauche de la majoration `CRect`.

*t*<br/>
Spécifie le nombre d’unités pour la partie supérieure de la majoration `CRect`.

*r*<br/>
Spécifie le nombre d’unités pour le côté droit de la majoration `CRect`.

*b*<br/>
Spécifie le nombre d’unités au bas de la majoration `CRect`.

### <a name="remarks"></a>Notes

Pour ce faire, `InflateRect` soustrait des unités de la gauche et de haut et ajoute des unités vers la droite et le bas. Les paramètres de `InflateRect` sont signés égales ; positif valeurs majoration `CRect` et valeurs négatives il deflate.

Les deux paires de côtés opposés de la majoration tout d’abord deux surcharges `CRect` afin que sa largeur totale est augmentée par deux fois *x* (ou `cx`) et sa hauteur totale est augmentée par deux fois *y* () ou `cy`). Les deux autres surcharges chaque côté de la majoration `CRect` indépendamment des autres.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));  
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

Rend un `CRect` égal à l’intersection de deux rectangles existants.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient un rectangle source.

*lpRect2*<br/>
Pointe vers un `RECT` structure ou `CRect` objet qui contient un rectangle source.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’intersection n’est pas vide. 0 si l’intersection est vide.

### <a name="remarks"></a>Notes

L’intersection est le plus grand rectangle contenu dans les deux rectangles existants.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rectOne(125, 0, 150, 200);
CRect rectTwo(0, 75, 350,  95);
CRect rectInter;

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

##  <a name="isrectempty"></a>  CRect::IsRectEmpty

Détermine si `CRect` est vide.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si `CRect` est vide ; 0 si `CRect` n’est pas vide.

### <a name="remarks"></a>Notes

Un rectangle est vide si la largeur et/ou la hauteur est 0 ou négatif. Diffère `IsRectNull`, qui détermine si toutes les coordonnées du rectangle sont nuls.

> [!NOTE]
>  Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) à normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());   
```


##  <a name="isrectnull"></a>  CRect::IsRectNull

Détermine si le haut, gauche, bas et à droite des valeurs de `CRect` sont toujours égaux à 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si `CRect`du haut, gauche, en bas et valeurs appropriées sont tout égale à 0 ; sinon 0.

### <a name="remarks"></a>Notes

Diffère `IsRectEmpty`, qui détermine si le rectangle est vide.

### <a name="example"></a>Exemple

```cpp  
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());  
```

##  <a name="movetox"></a>  CRect::MoveToX

Appelez cette fonction pour déplacer le rectangle à l’abscisse absolu spécifié par *x*.

```
void MoveToX(int x) throw();  
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x absolue pour l’angle supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

```cpp  
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));   
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

Appelez cette fonction pour déplacer le rectangle pour l’absolu - coordonnées x et y-spécifié.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x absolue pour l’angle supérieur gauche du rectangle.

*y*<br/>
Coordonnée y absolue pour l’angle supérieur gauche du rectangle.

*point*<br/>
Un `POINT` structure qui spécifie l’angle supérieur gauche absolue du rectangle.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));   
```


##  <a name="movetoy"></a>  CRect::MoveToY

Appelez cette fonction pour déplacer le rectangle à l’axe des ordonnées absolue spécifiée par *y*.

```
void MoveToY(int y) throw();  
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Coordonnée y absolue pour l’angle supérieur gauche du rectangle.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));   
```


##  <a name="normalizerect"></a>  CRect::NormalizeRect

Normalise `CRect` afin que la hauteur et la largeur sont positives.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Notes

Le rectangle est normalisé pour le positionnement de la quatrième-quadrant, Windows utilise généralement des coordonnées. `NormalizeRect` Compare les valeurs supérieure et inférieure et les échanges si le haut est supérieur à la partie inférieure. De même, il échange les valeurs de gauche et droit si gauche est supérieure à droite. Cette fonction est utile lorsque vous traitez des modes de mappage différents et inversée rectangles.

> [!NOTE]
>  Ce qui suit `CRect` fonctions membres requièrent des rectangles normalisées pour pouvoir fonctionner correctement : [hauteur](#height), [largeur](#width), [taille](#size), [ IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [ SubtractRect](#subtractrect), [opérateur ==](#operator_eq_eq), [opérateur ! =](#operator_neq), [opérateur &#124; ](#operator_or), [opérateur &#124;=](#operator_or_eq), [opérateur &](#operator_amp), et [opérateur & =](#operator_amp_eq).

### <a name="example"></a>Exemple

```cpp  
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);

```cpp  
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
   rect2.NormalizeRect();
ASSERT(rect1 == rect2);  
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

Déplace `CRect` par offsets spécifiés.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();  
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie la quantité à déplacer vers la gauche ou droite. Il doit être négatif pour le déplacer vers la gauche.

*y*<br/>
Spécifie la quantité pour faire monter ou Descendre. Il doit être négatif pour le déplacer vers le haut.

*point*<br/>
Contient un [POINT](../../mfc/reference/point-structure.md) structure ou [CPoint](cpoint-class.md) objet spécifiant les deux dimensions de déplacement.

*size*<br/>
Contient un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure ou [CSize](csize-class.md) objet spécifiant les deux dimensions de déplacement.

### <a name="remarks"></a>Notes

Déplace `CRect` *x* unités sur l’axe x et *y* unités sur l’axe y. Le *x* et *y* paramètres sont donc les valeurs signées, `CRect` peut être déplacée vers la gauche ou droite et vers le haut ou vers le bas.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

```cpp  
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));   
```


##  <a name="operator_lpcrect"></a>  CRect::operator LPCRECT convertit un `CRect` à un [LPCRECT](../../mfc/reference/data-types-mfc.md).  


```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Notes

Lorsque vous utilisez cette fonction, vous n’avez pas besoin l’adresse de (**&**) opérateur. Cet opérateur est automatiquement utilisé quand vous passez un `CRect` objet à une fonction qui attend un `LPCRECT`.

##  <a name="operator_lprect"></a>  CRect::operator LPRECT

Convertit un `CRect` à un [LPRECT](../../mfc/reference/data-types-mfc.md).  


```
operator LPRECT() throw();
```

### <a name="remarks"></a>Notes

Lorsque vous utilisez cette fonction, vous n’avez pas besoin l’adresse de (**&**) opérateur. Cet opérateur est automatiquement utilisé quand vous passez un `CRect` objet à une fonction qui attend un `LPRECT`.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRect::operator LPCRECT](#operator_lpcrect).

##  <a name="operator_eq"></a>  CRect::operator =

Assigne *srcRect* à `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Paramètres

*srcRect*<br/>
Fait référence à un rectangle source. Peut être un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="example"></a>Exemple

```cpp  
CRect rect(0, 0, 127, 168);
CRect rect2;

```cpp  
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));   
```


##  <a name="operator_eq_eq"></a>  CRect::operator ==

Détermine si `rect` est égal à `CRect` en comparant les coordonnées de leurs angles supérieur gauche et inférieur droit.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Fait référence à un rectangle source. Peut être un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si elle est égale ; sinon 0.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);

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


##  <a name="operator_neq"></a>  CRect::operator ! =

Détermine si *rect* n’est pas égal à `CRect` en comparant les coordonnées de leurs angles supérieur gauche et inférieur droit.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Fait référence à un rectangle source. Peut être un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si non égal ; sinon 0.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);  
```

##  <a name="operator_add_eq"></a>  CRect::operator +=

Déplacement les deux premières surcharges `CRect` par offsets spécifiés.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Un [POINT](../../mfc/reference/point-structure.md) structure ou [CPoint](cpoint-class.md) objet qui spécifie le nombre d’unités à déplacer le rectangle.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure ou [CSize](csize-class.md) objet qui spécifie le nombre d’unités à déplacer le rectangle.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient le nombre d’unités de chaque côté de la majoration `CRect`.

### <a name="remarks"></a>Notes

Le paramètre *x* et *y* (ou `cx` et `cy`) valeurs sont ajoutées à `CRect`.

La troisième surcharge augmente `CRect` par le nombre de spécifié d’unités dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp  
CRect rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect rect2(135, 300, 235, 400);

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);   
```

##  <a name="operator_-_eq"></a>  CRect::operator =

Déplacement les deux premières surcharges `CRect` par offsets spécifiés.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Un [POINT](../../mfc/reference/point-structure.md) structure ou [CPoint](cpoint-class.md) objet qui spécifie le nombre d’unités à déplacer le rectangle.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure ou [CSize](csize-class.md) objet qui spécifie le nombre d’unités à déplacer le rectangle.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient le nombre d’unités à deflate de chaque côté de `CRect`.

### <a name="remarks"></a>Notes

Le paramètre *x* et *y* (ou `cx` et `cy`) valeurs sont soustraits `CRect`.

La troisième surcharge dégonfle `CRect` par le nombre de spécifié d’unités dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect).

### <a name="example"></a>Exemple

```cpp  
CRect rect1(100, 235, 200, 335);
CPoint pt(35, 65);
rect1 -= pt;

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);   
```

##  <a name="operator_amp_eq"></a>  CRect::operator &amp;=

Jeux `CRect` égal à l’intersection de `CRect` et `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Contient un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="remarks"></a>Notes

L’intersection est le plus grand rectangle qui est contenu dans les deux rectangles.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRect::IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>  CRect::operator &#124;=

Jeux `CRect` égal à l’union de `CRect` et `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Contient un `CRect` ou [RECT](../../mfc/reference/rect-structure.md).

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles source.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect1(100,   0, 200, 300);
CRect rect2( 0, 100, 300, 200);
rect1 |= rect2;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);   
```


##  <a name="operator_add"></a>  CRect::operator +

Tout d’abord deux surcharges retournent un `CRect` objet est égal à `CRect` déplacé par offsets spécifiés.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Un [POINT](../../mfc/reference/point-structure.md) structure ou [CPoint](cpoint-class.md) objet qui spécifie le nombre d’unités à déplacer la valeur de retour.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure ou [CSize](csize-class.md) objet qui spécifie le nombre d’unités à déplacer la valeur de retour.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient le nombre d’unités de chaque côté de la valeur de retour de la majoration.

### <a name="return-value"></a>Valeur de retour

Le `CRect` résultant de déplacement ou de gonfler `CRect` par le nombre d’unités spécifié dans le paramètre.

### <a name="remarks"></a>Notes

Le paramètre *x* et *y* (ou `cx` et `cy`) paramètres sont ajoutés à `CRect`de position.

La troisième surcharge retourne un nouvel `CRect` qui est égal à `CRect` augmenté le nombre de spécifié d’unités dans chaque membre du paramètre.

### <a name="example"></a>Exemple

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);   
```


##  <a name="operator_-"></a>  CRect::operator-

Tout d’abord deux surcharges retournent un `CRect` objet est égal à `CRect` déplacé par offsets spécifiés.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Un [POINT](../../mfc/reference/point-structure.md) structure ou `CPoint` objet qui spécifie le nombre d’unités à déplacer la valeur de retour.

*size*<br/>
Un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure ou `CSize` objet qui spécifie le nombre d’unités à déplacer la valeur de retour.

*lpRect*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet qui contient le nombre d’unités à deflate de chaque côté de la valeur de retour.

### <a name="return-value"></a>Valeur de retour

Le `CRect` résultant de déplacement ou de DÉGONFLAGE `CRect` par le nombre d’unités spécifié dans le paramètre.

### <a name="remarks"></a>Notes

Le paramètre *x* et *y* (ou `cx` et `cy`) paramètres sont soustraits `CRect`de position.

La troisième surcharge retourne un nouvel `CRect` qui est égal à `CRect` réduite par le nombre de spécifié d’unités dans chaque membre du paramètre. Notez que cette surcharge fonctionne comme [DeflateRect](#deflaterect), et non [SubtractRect](#subtractrect).

### <a name="example"></a>Exemple

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);   
```


##  <a name="operator_amp"></a>  CRect::operator &amp;

Retourne un `CRect` qui est l’intersection de `CRect` et *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

Un `CRect` qui est l’intersection de `CRect` et *rect2*.

### <a name="remarks"></a>Notes

L’intersection est le plus grand rectangle qui est contenu dans les deux rectangles.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);   
```


##  <a name="operator_or"></a>  CRect::operator&#124;

Retourne un `CRect` qui est l’union de `CRect` et *rect2*.

``` 
CRect operator|(const RECT& 
rect2) const throw(); 
```

### <a name="parameters"></a>Paramètres

*rect2*<br/>
Contient un [RECT](../../mfc/reference/rect-structure.md) ou `CRect`.

### <a name="return-value"></a>Valeur de retour

Un `CRect` qui est l’union de `CRect` et *rect2*.

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect1(100,   0, 200, 300);
CRect rect2( 0, 100, 300, 200);
CRect rect3;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```


##  <a name="ptinrect"></a>  CRect::PtInRect

Détermine si le point spécifié se trouve dans `CRect`.

``` 
BOOL PtInRect(POINT point) const throw(); 
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient un [POINT](../../mfc/reference/point-structure.md) structure ou [CPoint](cpoint-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le point se trouve dans `CRect`; sinon, 0.

### <a name="remarks"></a>Notes

Un point se trouve dans `CRect` si elle se trouve sur le côté gauche ou supérieur, soit dans les quatre côtés. Un point sur le côté droit ou inférieur est en dehors de `CRect`.

> [!NOTE]
>  Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) à normaliser le rectangle avant d’appeler cette fonction.

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

##  <a name="setrect"></a>  CRect::SetRect

Définit les dimensions de `CRect` aux coordonnées spécifiées.

``` 
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```

### <a name="parameters"></a>Paramètres

*x1*<br/>
Spécifie la coordonnée x du coin supérieur gauche.

*y1*<br/>
Spécifie la coordonnée y du coin supérieur gauche.

*x2*<br/>
Spécifie la coordonnée x du coin inférieur droit.

*y2*<br/>
Spécifie la coordonnée y du coin inférieur droit.

### <a name="example"></a>Exemple

```cpp  
CRect rect;
rect.SetRect(256, 256, 512, 512);

```cpp  
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));   
```


##  <a name="setrectempty"></a>  CRect::SetRectEmpty

Rend `CRect` un rectangle null en définissant toutes les coordonnées à zéro.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Exemple

```cpp  
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());  
```

##  <a name="size"></a>  CRect::SIZE

Le `cx` et `cy` membres de la valeur de retour contient la hauteur et largeur de `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un [CSize](csize-class.md) objet qui contient la taille de `CRect`.

### <a name="remarks"></a>Notes

La hauteur ou la largeur peut être négative.

> [!NOTE]
>  Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) à normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

Rend les dimensions de la `CRect` égale à la soustraction de `lpRectSrc2` de `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRectSrc1*<br/>
Pointe vers le [RECT](../../mfc/reference/rect-structure.md) structure ou `CRect` objet à partir de laquelle un rectangle doit être soustrait.

*lpRectSrc2*<br/>
Pointe vers le `RECT` structure ou `CRect` objet doit être soustrait du rectangle vers lequel pointe le *lpRectSrc1* paramètre.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

La soustraction est le plus petit rectangle qui contient tous les points dans *lpRectScr1* qui ne sont pas dans l’intersection de *lpRectScr1* et *lpRectScr2*.

Le rectangle spécifié par *lpRectSrc1* sera inchangée si le rectangle spécifié par *lpRectSrc2* ne se chevauchent pas complètement le rectangle spécifié par *lpRectSrc1*dans au moins un de la direction x ou y.

Par exemple, si *lpRectSrc1* ont été (10,10, 100,100) et *lpRectSrc2* ont été (50,50, 150,150), le rectangle vers lequel pointe *lpRectSrc1* est inchangé lorsque le fonction retournée. Si *lpRectSrc1* ont été (10,10, 100,100) et *lpRectSrc2* ont été (50,10, 150,150), toutefois, le rectangle vers lequel pointe *lpRectSrc1* contiendrait les coordonnées (10,10, 50,100) quand la fonction retournée.

`SubtractRect` n’est pas le même que [opérateur -](#operator_-) ni [opérateur-=](#operator_-_eq). Aucune de ces opérateurs n’appelle jamais `SubtractRect`.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

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

##  <a name="topleft"></a>  CRect::TopLeft

Les coordonnées sont retournées sous la forme d’une référence à un [CPoint](cpoint-class.md) objet qui est contenue dans `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées de l’angle supérieur gauche du rectangle.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour obtenir ou définir l’angle supérieur gauche du rectangle. Définir l’angle à l’aide de cette fonction sur le côté gauche de l’opérateur d’assignation.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRect::CenterPoint](#centerpoint).

##  <a name="unionrect"></a>  CRect::UnionRect

Rend les dimensions de `CRect` égal à l’union des rectangles de deux sources.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Paramètres

*lpRect1*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure.md) ou `CRect` qui contient un rectangle source.

*lpRect2*<br/>
Pointe vers un `RECT` ou `CRect` qui contient un rectangle source.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’union n’est pas vide. 0 si l’union est vide.

### <a name="remarks"></a>Notes

L’union est le plus petit rectangle qui contient les deux rectangles source.

Windows ignore les dimensions d’un rectangle vide ; Autrement dit, un rectangle qui n’a aucune hauteur ou aucune largeur.

> [!NOTE]
>  Les rectangles doivent être normalisées ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) pour normaliser les rectangles avant d’appeler cette fonction.

### <a name="example"></a>Exemple

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```

##  <a name="width"></a>  CRect::Width

Calcule la largeur de `CRect` en soustrayant la valeur de gauche à partir de la valeur appropriée.

```
int Width() const throw();
```

### <a name="return-value"></a>Valeur de retour

La largeur de `CRect`.

### <a name="remarks"></a>Notes

La largeur peut être négative.

> [!NOTE]
>  Le rectangle doit être normalisé ou cette fonction peut échouer. Vous pouvez appeler [NormalizeRect](#normalizerect) à normaliser le rectangle avant d’appeler cette fonction.

### <a name="example"></a>Exemple  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>Voir aussi

[CPoint, classe](cpoint-class.md)<br/>
[CSize, classe](csize-class.md)<br/>
[RECT](../../mfc/reference/rect-structure.md)

