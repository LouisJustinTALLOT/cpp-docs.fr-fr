---
description: 'En savoir plus sur : CPoint, classe'
title: CPoint (classe)
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
ms.openlocfilehash: 9d1c6ecb628e4d47d80503bb7a441efc4deb1252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166757"
---
# <a name="cpoint-class"></a>CPoint (classe)

Semblable à la structure `POINT` Windows.

## <a name="syntax"></a>Syntaxe

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint :: CPoint](#cpoint)|Construit un objet `CPoint`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPoint :: offset](#offset)|Ajoute des valeurs aux `x` `y` membres et de `CPoint` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint :: Operator-](#operator_-)|Retourne la différence entre un `CPoint` et une taille, ou la négation d’un point, ou la différence de taille entre deux points, ou le décalage par une taille négative.|
|[CPoint :: Operator ! =](#operator_neq)|Vérifie l’inégalité entre deux points.|
|[CPoint :: Operator +](#operator_add)|Retourne la somme d’un `CPoint` et d’une taille ou d’un point, ou un `CRect` décalage d’une taille.|
|[CPoint :: Operator + =](#operator_add_eq)|Offsets `CPoint` par ajout d’une taille ou d’un point.|
|[CPoint :: Operator-=](#operator_-_eq)|Décale `CPoint` en soustrayant une taille ou un point.|
|[CPoint :: Operator = =](#operator_eq_eq)|Vérifie l’égalité entre deux points.|

## <a name="remarks"></a>Notes

Il comprend également des fonctions membres pour manipuler `CPoint` et des structures de [point](/windows/win32/api/windef/ns-windef-point) .

Un `CPoint` objet peut être utilisé partout où une `POINT` structure est utilisée. Les opérateurs de cette classe qui interagissent avec une « taille » acceptent les objets [CSize](../../atl-mfc-shared/reference/csize-class.md) ou les structures de [taille](/windows/win32/api/windef/ns-windef-size) , puisque les deux sont interchangeables.

> [!NOTE]
> Cette classe est dérivée de la `tagPOINT` structure. (Le nom `tagPOINT` est un nom moins couramment utilisé pour la `POINT` structure.) Cela signifie que les membres de données de la `POINT` structure, `x` et `y` , sont des membres de données accessibles de `CPoint` .

> [!NOTE]
> Pour plus d’informations sur les classes d’utilitaire partagées (comme `CPoint` ), consultez [classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Spécifications

**En-tête :** atltypes. h

## <a name="cpointcpoint"></a><a name="cpoint"></a> CPoint :: CPoint

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

*initialisation*<br/>
Spécifie la valeur du membre `y` de `CPoint`.

*initPt*<br/>
[Point](/windows/win32/api/windef/ns-windef-point) , ou `CPoint` qui spécifie les valeurs utilisées pour initialiser `CPoint` .

*initSize*<br/>
[Size](/windows/win32/api/windef/ns-windef-size) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie les valeurs utilisées pour initialiser `CPoint` .

*dwPoint*<br/>
Définit le `x` membre sur le mot de poids faible de *dwPoint* et le `y` membre sur le mot de poids fort de *dwPoint*.

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

## <a name="cpointoffset"></a><a name="offset"></a> CPoint :: offset

Ajoute des valeurs aux `x` `y` membres et de `CPoint` .

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*xOffset*<br/>
Spécifie la quantité de décalage du `x` membre de `CPoint` .

*yOffset*<br/>
Spécifie la quantité de décalage du `y` membre de `CPoint` .

*point*<br/>
Spécifie la quantité ( [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint` ) pour l’offset de `CPoint` .

*size*<br/>
Spécifie la quantité ( [Size](/windows/win32/api/windef/ns-windef-size) ou [CSize](../../atl-mfc-shared/reference/csize-class.md)) pour l’offset de `CPoint` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a> CPoint :: Operator = =

Vérifie l’égalité entre deux points.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient une structure [point](/windows/win32/api/windef/ns-windef-point) ou un `CPoint` objet.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les points sont égaux ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a> CPoint :: Operator ! =

Vérifie l’inégalité entre deux points.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient une structure [point](/windows/win32/api/windef/ns-windef-point) ou un `CPoint` objet.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les points ne sont pas égaux ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a> CPoint :: Operator + =

La première surcharge ajoute une taille au `CPoint` .

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Notes

La deuxième surcharge ajoute un point à `CPoint` .

Dans les deux cas, l’ajout s’effectue en ajoutant le `x` membre (ou `cx` ) de l’opérande de droite au `x` membre du `CPoint` et en ajoutant le `y` membre (ou `cy` ) de l’opérande de droite au `y` membre du `CPoint` .

Par exemple, `CPoint(5, -7)` en ajoutant à une variable qui contient les `CPoint(30, 40)` modifications apportées à la variable `CPoint(35, 33)` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a> CPoint :: Operator-=

La première surcharge soustrait une taille de `CPoint` .

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Notes

La deuxième surcharge soustrait un point de `CPoint` .

Dans les deux cas, la soustraction est effectuée en soustrayant le membre `x` (ou `cx` ) de l’opérande de droite du `x` membre de `CPoint` et en soustrayant le membre `y` (ou `cy` ) de l’opérande de droite du `y` membre du `CPoint` .

Par exemple, la soustraction `CPoint(5, -7)` d’une variable qui contient `CPoint(30, 40)` remplace la variable par `CPoint(25, 47)` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a> CPoint :: Operator +

Utilisez cet opérateur pour effectuer `CPoint` un décalage par un `CPoint` `CSize` objet ou, ou pour décaler un `CRect` par un `CPoint` .

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*lpRect*<br/>
Contient un pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Valeur renvoyée

`CPoint`Qui est décalée d’une taille, d’un `CPoint` décalage par un point ou d’un `CRect` décalage par un point.

### <a name="remarks"></a>Notes

Par exemple, l’utilisation de l’une des deux premières surcharges pour décaler le point d' `CPoint(25, -19)` un point ou d’une `CPoint(15, 5)` taille `CSize(15, 5)` retourne la valeur `CPoint(40, -14)` .

L’ajout d’un rectangle à un point retourne le rectangle après avoir été décalé par les `x` `y` valeurs et spécifiées dans le point. Par exemple, l’utilisation de la dernière surcharge pour décaler un rectangle `CRect(125, 219, 325, 419)` par un point `CPoint(25, -19)` retourne `CRect(150, 200, 350, 400)` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a> CPoint :: Operator-

Utilisez l’une des deux premières surcharges pour soustraire `CPoint` un `CSize` objet ou de `CPoint` .

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*size*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*lpRect*<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Valeur renvoyée

`CSize`Qui est la différence entre deux points, un `CPoint` qui est décalé par la négation d’une taille, un `CRect` qui est décalé par la négation d’un point ou un `CPoint` qui est la négation d’un point.

### <a name="remarks"></a>Notes

La troisième surcharge décale un `CRect` par la négation de `CPoint` . Enfin, utilisez l’opérateur unaire pour nier `CPoint` .

Par exemple, à l’aide de la première surcharge pour rechercher la différence entre deux points `CPoint(25, -19)` et `CPoint(15, 5)` retourne `CSize(10, -24)` .

La soustraction `CSize` d’un de `CPoint` effectue le même calcul que ci-dessus, mais retourne un `CPoint` objet, et non un `CSize` objet. Par exemple, l’utilisation de la deuxième surcharge pour rechercher la différence entre le point `CPoint(25, -19)` et la taille est `CSize(15, 5)` retournée `CPoint(10, -24)` .

La soustraction d’un rectangle d’un point retourne l’offset du rectangle par les négatifs `x` des `y` valeurs et spécifiées dans le point. Par exemple, l’utilisation de la dernière surcharge pour décaler le rectangle `CRect(125, 200, 325, 400)` par le point `CPoint(25, -19)` retourne `CRect(100, 219, 300, 419)` .

Utilisez l’opérateur unaire pour nier un point. Par exemple, l’utilisation de l’opérateur unaire avec le point `CPoint(25, -19)` retourne `CPoint(-25, 19)` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[POINT, structure](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize (classe)](../../atl-mfc-shared/reference/csize-class.md)
