---
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
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491229"
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
|[CPoint::CPoint](#cpoint)|Construit un objet `CPoint`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPoint::Offset](#offset)|Ajoute des valeurs aux `x` membres `y` et de `CPoint`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint :: Operator-](#operator_-)|Retourne la différence entre un `CPoint` et une taille, ou la négation d’un point, ou la différence de taille entre deux points, ou le décalage par une taille négative.|
|[CPoint :: Operator ! =](#operator_neq)|Vérifie l’inégalité entre deux points.|
|[CPoint :: Operator +](#operator_add)|Retourne la somme d’un `CPoint` et d’une taille ou d’un point `CRect` , ou un décalage d’une taille.|
|[CPoint :: Operator + =](#operator_add_eq)|Offsets `CPoint` par ajout d’une taille ou d’un point.|
|[CPoint :: Operator-=](#operator_-_eq)|Décale `CPoint` en soustrayant une taille ou un point.|
|[CPoint::operator ==](#operator_eq_eq)|Vérifie l’égalité entre deux points.|

## <a name="remarks"></a>Notes

Il comprend également des fonctions membres pour `CPoint` manipuler et des structures de [point](/windows/win32/api/windef/ns-windef-point) .

Un `CPoint` objet peut être utilisé partout où `POINT` une structure est utilisée. Les opérateurs de cette classe qui interagissent avec une « taille » acceptent les objets [CSize](../../atl-mfc-shared/reference/csize-class.md) ou les structures de [taille](/windows/win32/api/windef/ns-windef-size) , puisque les deux sont interchangeables.

> [!NOTE]
>  Cette classe est dérivée de `tagPOINT` la structure. (Le `tagPOINT` nom est un nom moins couramment utilisé pour la `POINT` structure.) Cela signifie que les membres de données de `POINT` la structure `x` , `y`et, sont des membres de `CPoint`données accessibles de.

> [!NOTE]
>  Pour plus d’informations sur les classes d’utilitaire `CPoint`partagées (comme), consultez [classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes. h

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

*initialisation*<br/>
Spécifie la valeur du membre `y` de `CPoint`.

*initPt*<br/>
[Point](/windows/win32/api/windef/ns-windef-point) , ou `CPoint` qui spécifie les valeurs `CPoint`utilisées pour initialiser.

*initSize*<br/>
[Size](/windows/win32/api/windef/ns-windef-size) structure ou [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie les valeurs utilisées `CPoint`pour initialiser.

*dwPoint*<br/>
Définit le `x` membre sur le mot de poids faible de *dwPoint* et le `y` membre sur le mot de poids fort de *dwPoint*.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni, les membres `x` et `y` ont la valeur 0.

### <a name="example"></a>Exemples

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

Ajoute des valeurs aux `x` membres `y` et de `CPoint`.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*xOffset*<br/>
Spécifie la quantité de décalage `x` du membre `CPoint`de.

*yOffset*<br/>
Spécifie la quantité de décalage `y` du membre `CPoint`de.

*point*<br/>
Spécifie la quantité ( [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint`) pour l'offset de `CPoint`.

*size*<br/>
Spécifie la quantité ( [Size](/windows/win32/api/windef/ns-windef-size) ou [CSize](../../atl-mfc-shared/reference/csize-class.md)) pour l' `CPoint`offset de.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CPoint::operator ==

Vérifie l’égalité entre deux points.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient une structure [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint` un objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les points sont égaux ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint :: Operator ! =

Vérifie l’inégalité entre deux points.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Contient une structure [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint` un objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les points ne sont pas égaux ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint :: Operator + =

La première surcharge ajoute une taille au `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Notes

La deuxième surcharge ajoute un point à `CPoint`.

Dans les deux cas, l’ajout s’effectue en `x` ajoutant le `cx`membre (ou) de l’opérande de droite `CPoint` au `x` membre du et en ajoutant le `y` membre ( `cy`ou) de l’opérande de droite à l’élément `y` membre`CPoint`de.

Par exemple, en `CPoint(5, -7)` ajoutant à une variable qui `CPoint(30, 40)` contient les modifications apportées à `CPoint(35, 33)`la variable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint :: Operator-=

La première surcharge soustrait une taille de `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Contient une structure de [taille](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contient une structure de [point](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Notes

La deuxième surcharge soustrait un point de `CPoint`.

Dans les deux cas `x` , la soustraction est effectuée en soustrayant le membre (ou `cx`) de l’opérande `x` de droite du membre de `CPoint` et en soustrayant le `cy` `y` membre (ou) de la partie droite. opérande du `CPoint`membre de. `y`

Par exemple, la soustraction `CPoint(5, -7)` d’une variable qui contient `CPoint(30, 40)` remplace la variable `CPoint(25, 47)`par.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint :: Operator +

Utilisez cet opérateur pour effectuer `CPoint` un décalage `CPoint` par `CSize` un objet ou, ou pour `CRect` décaler un par un `CPoint`.

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

### <a name="return-value"></a>Valeur de retour

Qui est décalée d’une taille, d' `CPoint` un décalage par `CRect` un point ou d’un décalage par un point. `CPoint`

### <a name="remarks"></a>Notes

Par exemple, l’utilisation de l’une des deux premières surcharges pour décaler le point `CPoint(25, -19)` d' `CSize(15, 5)` un point `CPoint(15, 5)` ou `CPoint(40, -14)`d’une taille retourne la valeur.

L’ajout d’un rectangle à un point retourne le rectangle après avoir été `x` décalé `y` par les valeurs et spécifiées dans le point. Par exemple, l’utilisation de la dernière surcharge pour décaler un `CPoint(25, -19)` rectangle `CRect(150, 200, 350, 400)` `CRect(125, 219, 325, 419)` par un point retourne.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint :: Operator-

Utilisez l’une des deux premières surcharges pour soustraire `CPoint` un `CSize` objet ou `CPoint`de.

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

### <a name="return-value"></a>Valeur de retour

Qui est la différence entre deux points, un `CPoint` qui est décalé par la négation d’une taille, un `CRect` qui est décalé par la négation d’un point ou un `CPoint` qui est la négation d’un point. `CSize`

### <a name="remarks"></a>Notes

La troisième surcharge décale un `CRect` par la négation de. `CPoint` Enfin, utilisez l’opérateur unaire pour nier `CPoint`.

Par exemple, à l’aide de la première surcharge pour rechercher la différence `CPoint(25, -19)` entre `CPoint(15, 5)` deux `CSize(10, -24)`points et retourne.

La soustraction `CSize` d' `CPoint` un de effectue le même calcul que ci- `CPoint` dessus, mais retourne `CSize` un objet, et non un objet. Par exemple, l’utilisation de la deuxième surcharge pour rechercher la différence entre `CPoint(25, -19)` le point et `CSize(15, 5)` la `CPoint(10, -24)`taille est retournée.

La soustraction d’un rectangle d’un point retourne l’offset du rectangle par les négatifs `x` des `y` valeurs et spécifiées dans le point. Par exemple, l’utilisation de la dernière surcharge pour décaler le `CPoint(25, -19)` rectangle `CRect(100, 219, 300, 419)` `CRect(125, 200, 325, 400)` par le point retourne.

Utilisez l’opérateur unaire pour nier un point. Par exemple, l’utilisation de l’opérateur unaire `CPoint(25, -19)` avec `CPoint(-25, 19)`le point retourne.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[POINT, structure](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize, classe](../../atl-mfc-shared/reference/csize-class.md)
