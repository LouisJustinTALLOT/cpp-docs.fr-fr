---
title: CPoint, classe
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: 85e469e1f52a22917580ce8616aaba5ff57d08ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252617"
---
# <a name="cpoint-class"></a>CPoint, classe

Semblable à la structure `POINT` Windows.

## <a name="syntax"></a>Syntaxe

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Construit un objet `CPoint`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPoint::Offset](#offset)|Ajoute des valeurs à la `x` et `y` membres de la `CPoint`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint::operator-](#operator_-)|Retourne la différence entre un `CPoint` et une taille ou la négation d’un point ou la différence de taille entre deux points, ou le décalage par une taille négative.|
|[CPoint::operator !=](#operator_neq)|Vérifie l’inégalité entre deux points.|
|[CPoint::operator +](#operator_add)|Retourne la somme d’un `CPoint` et une taille ou un point, ou un `CRect` compensée par une taille.|
|[CPoint::operator +=](#operator_add_eq)|Décalages `CPoint` en ajoutant une taille ou un point.|
|[CPoint::operator -=](#operator_-_eq)|Décalages `CPoint` en soustrayant une taille ou un point.|
|[CPoint::operator ==](#operator_eq_eq)|Vérifie l’égalité entre deux points.|

## <a name="remarks"></a>Notes

Il inclut également des fonctions de membre pour manipuler `CPoint` et [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structures.

Un `CPoint` objet peut être utilisé partout où une `POINT` structure est utilisée. Les opérateurs de cette classe qui interagissent avec une « taille » acceptent les deux [CSize](../../atl-mfc-shared/reference/csize-class.md) objets ou [taille](/windows/desktop/api/windef/ns-windef-tagsize) structures, étant donné que les deux sont interchangeables.

> [!NOTE]
>  Cette classe est dérivée de la `tagPOINT` structure. (Le nom `tagPOINT` est un nom moins couramment utilisé pour la `POINT` structure.) Cela signifie que les membres de données de la `POINT` structure, `x` et `y`, sont des membres de données accessibles de `CPoint`.

> [!NOTE]
>  Pour plus d’informations sur les classes de l’utilitaire de partagées (telles que `CPoint`), consultez [Classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes.h

##  <a name="cpoint"></a>  CPoint::CPoint

Construit un objet `CPoint`.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Paramètres

*initX*<br/>
Spécifie la valeur du membre `x` de `CPoint`.

*initY*<br/>
Spécifie la valeur du membre `y` de `CPoint`.

*initPt*<br/>
[POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou `CPoint` qui spécifie les valeurs utilisées pour initialiser `CPoint`.

*initSize*<br/>
[TAILLE](/windows/desktop/api/windef/ns-windef-tagsize) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie les valeurs utilisées pour initialiser `CPoint`.

*dwPoint*<br/>
Définit le `x` membre pour le mot de poids faible de *dwPoint* et `y` membre pour le mot de poids fort de *dwPoint*.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni, les membres `x` et `y` ont la valeur 0.

### <a name="example"></a>Exemple

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

##  <a name="offset"></a>  CPoint::Offset

Ajoute des valeurs à la `x` et `y` membres de la `CPoint`.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*xOffset*<br/>
Spécifie la valeur de décalage la `x` membre de la `CPoint`.

*yOffset*<br/>
Spécifie la valeur de décalage la `y` membre de la `CPoint`.

*point*<br/>
Spécifie la quantité ( [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) ou `CPoint`) pour décaler la `CPoint`.

*size*<br/>
Spécifie la quantité ( [taille](/windows/desktop/api/windef/ns-windef-tagsize) ou [CSize](../../atl-mfc-shared/reference/csize-class.md)) pour décaler la `CPoint`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CPoint::operator ==

Vérifie l’égalité entre deux points.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou `CPoint` objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les points sont égaux ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>  CPoint::operator ! =

Vérifie l’inégalité entre deux points.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou `CPoint` objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les points ne sont pas égaux ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CPoint::operator +=

La première surcharge ajoute une taille pour le `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.

*point*<br/>
Contient un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet.

### <a name="remarks"></a>Notes

La deuxième surcharge ajoute un point pour le `CPoint`.

Dans les deux cas, l’ajout s’effectue en ajoutant le `x` (ou `cx`) membre de l’opérande de droite au `x` membre de la `CPoint` et l’ajout de la `y` (ou `cy`) membre de l’opérande de droite à la `y` membre de la `CPoint`.

Par exemple, l’ajout `CPoint(5, -7)` à une variable qui contient `CPoint(30, 40)` modifie la variable à `CPoint(35, 33)`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CPoint::operator -=

La première surcharge soustrait une taille à partir de la `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.

*point*<br/>
Contient un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet.

### <a name="remarks"></a>Notes

La deuxième surcharge soustrait un point à partir de la `CPoint`.

Dans les deux cas, la soustraction est effectuée en soustrayant le `x` (ou `cx`) membre de l’opérande de droite à partir de la `x` membre de la `CPoint` et en soustrayant le `y` (ou `cy`) membre de la droite opérande à partir de la `y` membre de la `CPoint`.

Par exemple, la soustraction `CPoint(5, -7)` à partir d’une variable qui contient `CPoint(30, 40)` modifie la variable à `CPoint(25, 47)`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>  CPoint::operator +

Utilisez cet opérateur de décalage `CPoint` par un `CPoint` ou `CSize` objet, ou pour compenser une `CRect` par un `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.

*point*<br/>
Contient un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet.

*lpRect*<br/>
Contient un pointeur vers un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) structure ou [CRect](../../atl-mfc-shared/reference/crect-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Un `CPoint` qui est compensée par une taille, un `CPoint` qui est décalée par un point, ou un `CRect` compensé par un point.

### <a name="remarks"></a>Notes

Par exemple, à l’aide d’une des deux premières surcharges décalage `CPoint(25, -19)` par un point de `CPoint(15, 5)` ou taille `CSize(15, 5)` retourne la valeur `CPoint(40, -14)`.

Ajout d’un rectangle à un point retourne le rectangle après décalé par le `x` et `y` valeurs spécifiées dans le point. Par exemple, à l’aide de la dernière surcharge pour le décalage d’un rectangle `CRect(125, 219, 325, 419)` par un point de `CPoint(25, -19)` retourne `CRect(150, 200, 350, 400)`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>  CPoint::operator -

Utilisez une des deux premières surcharges à soustraire un `CPoint` ou `CSize` à partir de l’objet `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Un [POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet.

*size*<br/>
Un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.

*lpRect*<br/>
Un pointeur vers un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) structure ou un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Un `CSize` qui est la différence entre deux points, une `CPoint` qui est compensée par la négation d’une taille, un `CRect` qui est compensée par la négation d’un point, ou un `CPoint` qui est la négation d’un point.

### <a name="remarks"></a>Notes

La troisième surcharge décalages un `CRect` selon la négation de `CPoint`. Enfin, utilisez l’opérateur unaire à inverser `CPoint`.

Par exemple, à l’aide de la première surcharge pour rechercher la différence entre deux points `CPoint(25, -19)` et `CPoint(15, 5)` retourne `CSize(10, -24)`.

En soustrayant un `CSize` de `CPoint` effectue le même calcul comme indiqué ci-dessus, mais retourne un `CPoint` de l’objet, pas un `CSize` objet. Par exemple, à l’aide de la deuxième surcharge pour rechercher la différence entre le point de `CPoint(25, -19)` et la taille `CSize(15, 5)` retourne `CPoint(10, -24)`.

En soustrayant un rectangle à partir d’un point retourne le décalage du rectangle par les négatifs de la `x` et `y` valeurs spécifiées dans le point. Par exemple, à l’aide de la dernière surcharge pour décaler le rectangle `CRect(125, 200, 325, 400)` par le point de `CPoint(25, -19)` retourne `CRect(100, 219, 300, 419)`.

Utilisez l’opérateur unaire à inverser un point. Par exemple, à l’aide de l’opérateur unaire avec le point de `CPoint(25, -19)` retourne `CPoint(-25, 19)`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[POINT, Structure](/windows/desktop/api/windef/ns-windef-tagpoint)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize, classe](../../atl-mfc-shared/reference/csize-class.md)
