---
title: Classe CPoint
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
ms.openlocfilehash: a806cfa18119df9beef3e070a65bc238a12580a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317720"
---
# <a name="cpoint-class"></a>Classe CPoint

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
|[CPoint::Offset](#offset)|Ajoute des `x` valeurs `y` à `CPoint`la et les membres de la .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPoint::opérateur -](#operator_-)|Retourne la différence `CPoint` d’une taille et d’une taille, ou la négation d’un point, ou la différence de taille entre deux points, ou la compensation par une taille négative.|
|[CPoint::opérateur !](#operator_neq)|Contrôle de l’inégalité entre deux points.|
|[CPoint::opérateur](#operator_add)|Retourne la somme `CPoint` d’une taille ou `CRect` d’un point, ou d’un décalage par une taille.|
|[CPoint::opérateur](#operator_add_eq)|`CPoint` Compense en ajoutant une taille ou un point.|
|[CPoint::opérateur -MD](#operator_-_eq)|`CPoint` Compense en soustrayant une taille ou un point.|
|[CPoint::opérateur](#operator_eq_eq)|Vérifications de l’égalité entre deux points.|

## <a name="remarks"></a>Notes

Il comprend également des `CPoint` fonctions de membre pour manipuler et les structures [POINT.](/windows/win32/api/windef/ns-windef-point)

Un `CPoint` objet peut être `POINT` utilisé partout où une structure est utilisée. Les opérateurs de cette classe qui interagissent avec une "taille" acceptent soit des objets [CSize,](../../atl-mfc-shared/reference/csize-class.md) soit des structures [SIZE,](/windows/win32/api/windef/ns-windef-size) puisque les deux sont interchangeables.

> [!NOTE]
> Cette classe est `tagPOINT` dérivée de la structure. (Le `tagPOINT` nom est un nom moins `POINT` couramment utilisé pour la structure.) Cela signifie que les `POINT` membres `x` des `y`données de la `CPoint`structure, et , sont des membres de données accessibles de .

> [!NOTE]
> Pour plus d’informations sur `CPoint`les cours d’utilité partagée (comme ), voir [Classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Spécifications

**En-tête:** atltypes.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint::CPoint

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
[STRUCTURE](/windows/win32/api/windef/ns-windef-point) POINT `CPoint` ou qui spécifie `CPoint`les valeurs utilisées pour initialiser .

*initSize*<br/>
[STRUCTURE SIZE](/windows/win32/api/windef/ns-windef-size) ou [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie les valeurs utilisées pour initialiser `CPoint`.

*dwPoint (en)*<br/>
Définit `x` le membre au mot de bas ordre `y` de *dwPoint* et le membre au mot de haut ordre de *dwPoint*.

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

## <a name="cpointoffset"></a><a name="offset"></a>CPoint::Offset

Ajoute des `x` valeurs `y` à `CPoint`la et les membres de la .

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Paramètres

*xOffset (en anglais)*<br/>
Spécifie le `x` montant pour `CPoint`compenser le membre de la .

*yOffset (en anglais)*<br/>
Spécifie le `y` montant pour `CPoint`compenser le membre de la .

*Point*<br/>
Spécifie le `CPoint`montant ( `CPoint` [POINT](/windows/win32/api/windef/ns-windef-point) ou ) pour compenser le .

*Taille*<br/>
Spécifie le montant [(SIZE](/windows/win32/api/windef/ns-windef-size) ou `CPoint` [CSize](../../atl-mfc-shared/reference/csize-class.md)) pour compenser le .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::opérateur

Vérifications de l’égalité entre deux points.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Contient une structure `CPoint` ou un objet [POINT.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Valeur de retour

Nonzero si les points sont égaux; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::opérateur !

Contrôle de l’inégalité entre deux points.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Contient une structure `CPoint` ou un objet [POINT.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Valeur de retour

Nonzero si les points ne sont pas égaux; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::opérateur

La première surcharge ajoute une `CPoint`taille à la .

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
Contient une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Point*<br/>
Contient une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Notes

La deuxième surcharge ajoute un `CPoint`point à la .

Dans `x` les deux cas, l’addition `cx`est faite en ajoutant le `x` (ou) `CPoint` membre `y` de `cy`l’opéra de droite au membre `y` de `CPoint`l’opéra de droite et en ajoutant le (ou) membre de l’opéra de droite au membre de la .

Par exemple, `CPoint(5, -7)` ajouter à `CPoint(30, 40)` une variable `CPoint(35, 33)`qui contient des changements de la variable à .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::opérateur -MD

La première surcharge soustrait une `CPoint`taille de la .

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
Contient une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Point*<br/>
Contient une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Notes

La deuxième surcharge soustrait un `CPoint`point de la .

Dans les deux cas, la soustraction `x` se `cx`fait en soustrayant le `x` (ou) membre de l’opéra de droite du membre de l’opéra de droite et en `CPoint` soustrayant le `y` (ou) `cy`membre de l’opéra de droite du `y` membre de la `CPoint`.

Par exemple, soustraire `CPoint(5, -7)` d’une variable qui contient des `CPoint(30, 40)` modifications de la variable à `CPoint(25, 47)`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::opérateur

Utilisez cet opérateur `CPoint` pour `CPoint` `CSize` compenser par un `CRect` ou `CPoint`un objet, ou pour compenser un par un .

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
Contient une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Point*<br/>
Contient une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

*lpRect*<br/>
Contient un pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect.](../../atl-mfc-shared/reference/crect-class.md)

### <a name="return-value"></a>Valeur de retour

Un `CPoint` qui est compensé par `CPoint` une taille, une qui `CRect` est compensée par un point, ou un décalage par un point.

### <a name="remarks"></a>Notes

Par exemple, l’utilisation de l’une des `CPoint(25, -19)` deux `CPoint(15, 5)` premières `CSize(15, 5)` surcharges `CPoint(40, -14)`pour compenser le point d’un point ou d’une taille renvoie la valeur .

L’ajout d’un rectangle à un `x` point `y` renvoie le rectangle après avoir été compensé par le et les valeurs spécifiées dans le point. Par exemple, en utilisant la dernière `CRect(125, 219, 325, 419)` surcharge `CPoint(25, -19)` pour `CRect(150, 200, 350, 400)`compenser un rectangle par un point retourne .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::opérateur -

Utilisez l’une des deux premières surcharges `CSize` pour `CPoint`soustraire un `CPoint` ou l’objet de .

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Une structure [POINT](/windows/win32/api/windef/ns-windef-point) ou un objet [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

*Taille*<br/>
Une structure [SIZE](/windows/win32/api/windef/ns-windef-size) ou un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*lpRect*<br/>
Un pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect.](../../atl-mfc-shared/reference/crect-class.md)

### <a name="return-value"></a>Valeur de retour

C’est `CSize` la différence entre `CPoint` deux points, une compensation par la `CRect` négation d’une taille, une `CPoint` compensation par la négation d’un point, ou une négation d’un point.

### <a name="remarks"></a>Notes

La troisième surcharge compense `CRect` un par `CPoint`la négation de . Enfin, utilisez l’opérateur unary pour nier `CPoint`.

Par exemple, en utilisant la première surcharge `CPoint(25, -19)` pour `CPoint(15, 5)` `CSize(10, -24)`trouver la différence entre deux points et les rendements .

Soustraire `CSize` un `CPoint` de fait le même `CPoint` calcul que `CSize` ci-dessus, mais renvoie un objet, pas un objet. Par exemple, en utilisant la deuxième surcharge `CPoint(25, -19)` pour trouver `CSize(15, 5)` `CPoint(10, -24)`la différence entre le point et les rendements de taille .

Le soustraitement d’un rectangle à partir d’un point renvoie le rectangle compensé par les négatifs et les `x` `y` valeurs spécifiées dans le point. Par exemple, en utilisant la dernière `CRect(125, 200, 325, 400)` surcharge `CPoint(25, -19)` pour `CRect(100, 219, 300, 419)`compenser le rectangle par les retours de points .

Utilisez l’opérateur unary pour nier un point. Par exemple, en utilisant l’opérateur `CPoint(-25, 19)`unary avec les rendements de point `CPoint(25, -19)` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[POINT, structure](/windows/win32/api/windef/ns-windef-point)<br/>
[Classe CRect](../../atl-mfc-shared/reference/crect-class.md)<br/>
[Classe CSize](../../atl-mfc-shared/reference/csize-class.md)
