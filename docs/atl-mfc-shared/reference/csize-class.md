---
description: 'En savoir plus sur : CSize, classe'
title: CSize (classe)
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 0a63a7e0c48948406bf5650a1b095713f701a325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166640"
---
# <a name="csize-class"></a>CSize (classe)

Semblable à la structure [SIZE](/windows/win32/api/windef/ns-windef-size) Windows, qui implémente une coordonnée ou une position relative.

## <a name="syntax"></a>Syntaxe

```
class CSize : public tagSIZE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSize :: CSize](#csize)|Construit un objet `CSize`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSize :: Operator-](#operator_-)|Soustrait deux tailles.|
|[CSize :: Operator ! =](#operator_neq)|Vérifie l’inégalité entre `CSize` et une taille.|
|[CSize :: Operator +](#operator_add)|Ajoute deux tailles.|
|[CSize :: Operator + =](#operator_add_eq)|Ajoute une taille à `CSize` .|
|[CSize :: Operator-=](#operator_-_eq)|Soustrait une taille de `CSize` .|
|[CSize :: Operator = =](#operator_eq_eq)|Vérifie l’égalité entre `CSize` et une taille.|

## <a name="remarks"></a>Notes

Cette classe est dérivée de la `SIZE` structure. Cela signifie que vous pouvez passer un `CSize` dans un paramètre qui appelle pour un `SIZE` et que les données membres de la `SIZE` structure sont des membres de données accessibles de `CSize` .

Les `cx` `cy` membres et de `SIZE` (et `CSize` ) sont publics. En outre, `CSize` implémente des fonctions membres pour manipuler la `SIZE` structure.

> [!NOTE]
> Pour plus d’informations sur les classes d’utilitaire partagées (comme `CSize` ), consultez [classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagSIZE`

`CSize`

## <a name="requirements"></a>Spécifications

**En-tête :** atltypes. h

## <a name="csizecsize"></a><a name="csize"></a> CSize :: CSize

Construit un objet `CSize`.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Paramètres

*initCX*<br/>
Définit le `cx` membre pour le `CSize` .

*initCY*<br/>
Définit le `cy` membre pour le `CSize` .

*initSize*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou `CSize` objet utilisé pour initialiser `CSize` .

*initPt*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou `CPoint` objet utilisé pour initialiser `CSize` .

*dwSize nul*<br/>
Valeur DWORD utilisée pour initialiser `CSize` . Le mot de poids faible est le `cx` membre et le mot de poids fort est le `cy` membre.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni, `cx` et `cy` sont initialisés à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a> CSize :: Operator = =

Vérifie l’égalité entre deux tailles.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne une valeur différente de zéro si les tailles sont égales, otherwize 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a> CSize :: Operator ! =

Vérifie l’inégalité entre deux tailles.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne une valeur différente de zéro si les tailles ne sont pas égales ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a> CSize :: Operator + =

Ajoute une taille à ce `CSize` .

```cpp
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a> CSize :: Operator-=

Soustrait une taille de ce `CSize` .

```cpp
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a> CSize :: Operator +

Ces opérateurs ajoutent cette `CSize` valeur à la valeur du paramètre.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Notes

Consultez les descriptions suivantes des opérateurs individuels :

- **opérateur + (** *taille* **)**

  Cette opération ajoute deux `CSize` valeurs.

- **opérateur + (** *point* **)**

  Cette opération décale (déplace) une valeur [point](/windows/win32/api/windef/ns-windef-point) (ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) de cette `CSize` valeur. Les `cx` `cy` membres et de cette `CSize` valeur sont ajoutés aux `x` `y` membres de données et de la `POINT` valeur. Elle est analogue à la version de [CPoint :: Operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **opérateur + (** *lpRect* **)**

   Cette opération décale (déplace) une valeur [Rect](/windows/win32/api/windef/ns-windef-rect) (ou [CRect](../../atl-mfc-shared/reference/crect-class.md)) de cette `CSize` valeur. Les `cx` `cy` membres et de cette `CSize` valeur sont ajoutés aux `left` données membres,, `top` `right` et `bottom` de la `RECT` valeur. Elle est analogue à la version de [CRect :: Operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a> CSize :: Operator-

Les trois premiers opérateurs soustraitnt cette `CSize` valeur à la valeur du paramètre.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Notes

Le quatrième opérateur, le signe moins unaire, modifie le signe de la `CSize` valeur. Consultez les descriptions suivantes des opérateurs individuels :

- **Operator-(** *taille* **)**

  Cette opération soustrait deux `CSize` valeurs.

- **Operator-(** *point* **)**

  Cette opération décale (déplace) une valeur [point](/windows/win32/api/windef/ns-windef-point) ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) par l’inverse additif de cette `CSize` valeur. `cx`Et `cy` de cette `CSize` valeur sont soustraites des `x` `y` membres de données et de la `POINT` valeur. Elle est analogue à la version de [CPoint :: Operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **Operator-(** *lpRect* **)**

  Cette opération décale (déplace) une valeur [Rect](/windows/win32/api/windef/ns-windef-rect) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) par l’inverse additif de cette `CSize` valeur. Les `cx` `cy` membres et de cette `CSize` valeur sont soustraites des `left` `top` `right` membres de données,, et `bottom` de la `RECT` valeur. Elle est analogue à la version de [CRect :: Operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **Operator-()**

  Cette opération retourne l’inverse additif de cette `CSize` valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint (classe)](../../atl-mfc-shared/reference/cpoint-class.md)
