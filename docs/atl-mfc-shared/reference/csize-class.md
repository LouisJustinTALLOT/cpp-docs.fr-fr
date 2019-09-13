---
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
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491658"
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
|[CSize::CSize](#csize)|Construit un objet `CSize`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSize :: Operator-](#operator_-)|Soustrait deux tailles.|
|[CSize :: Operator ! =](#operator_neq)|Vérifie l’inégalité entre `CSize` et une taille.|
|[CSize :: Operator +](#operator_add)|Ajoute deux tailles.|
|[CSize :: Operator + =](#operator_add_eq)|Ajoute une taille à `CSize`.|
|[CSize :: Operator-=](#operator_-_eq)|Soustrait une taille de `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Vérifie l’égalité entre `CSize` et une taille.|

## <a name="remarks"></a>Notes

Cette classe est dérivée de `SIZE` la structure. Cela signifie que vous pouvez passer `CSize` un dans un paramètre qui appelle pour `SIZE` un et que les données membres de `SIZE` la structure sont des membres de `CSize`données accessibles de.

Les `cx` membres `cy` et de `SIZE` ( et`CSize`) sont publics. En outre, `CSize` implémente des fonctions membres pour manipuler `SIZE` la structure.

> [!NOTE]
> Pour plus d’informations sur les classes d’utilitaire `CSize`partagées (comme), consultez [classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagSIZE`

`CSize`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes. h

##  <a name="csize"></a>  CSize::CSize

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
Définit le `cx` membre pour le `CSize`.

*initCY*<br/>
Définit le `cy` membre pour le `CSize`.

*initSize*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) ou objet `CSize` utilisé pour initialiser `CSize`.

*initPt*<br/>
Structure de [point](/windows/win32/api/windef/ns-windef-point) ou objet `CPoint` utilisé pour initialiser `CSize`.

*dwSize*<br/>
Valeur DWORD utilisée pour initialiser `CSize`. Le mot de poids faible est le `cx` membre et le mot de poids fort est le `cy` membre.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni `cx` , `cy` et sont initialisés à zéro.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator ==

Vérifie l’égalité entre deux tailles.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne une valeur différente de zéro si les tailles sont égales, otherwize 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize :: Operator ! =

Vérifie l’inégalité entre deux tailles.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne une valeur différente de zéro si les tailles ne sont pas égales ; sinon, 0.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize :: Operator + =

Ajoute une taille à ce `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize :: Operator-=

Soustrait une taille de ce `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize :: Operator +

Ces opérateurs ajoutent `CSize` cette valeur à la valeur du paramètre.

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

  Cette opération décale (déplace) une valeur [point](/previous-versions/dd162805\(v=vs.85\)) (ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) de cette `CSize` valeur. Les `cx` membres `cy` et de cette `CSize` valeur sont ajoutés aux `x` membres de `y` données et de la `POINT` valeur. Elle est analogue à la version de [CPoint :: Operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **opérateur + (** *lpRect* **)**

   Cette opération décale (déplace) une valeur [Rect](/previous-versions/dd162897\(v=vs.85\)) (ou [CRect](../../atl-mfc-shared/reference/crect-class.md)) de cette `CSize` valeur. Les `cx` membres `cy` et de cette `CSize` valeur sont ajoutés aux `left`données membres `top`, `right`, et `bottom` de la `RECT` valeur. Elle est analogue à la version de [CRect :: Operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize :: Operator-

Les trois premiers opérateurs soustraitnt cette `CSize` valeur à la valeur du paramètre.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Notes

Le quatrième opérateur, le signe moins unaire, modifie le signe `CSize` de la valeur. Consultez les descriptions suivantes des opérateurs individuels :

- **Operator-(** *taille* **)**

  Cette opération soustrait deux `CSize` valeurs.

- **Operator-(** *point* **)**

  Cette opération décale (déplace) une valeur [point](/previous-versions/dd162805\(v=vs.85\)) ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) par l’inverse additif de cette `CSize` valeur. `y` `x` Et de cette valeur`CSize` sont soustraites des membres de données et de la `POINT` valeur. `cy` `cx` Elle est analogue à la version de [CPoint :: Operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **operator -(** *lpRect* **)**

  Cette opération décale (déplace) une valeur [Rect](/previous-versions/dd162897\(v=vs.85\)) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) par l’inverse additif de cette `CSize` valeur. Les `cx` membres `cy` et de cette `CSize` `left` `top` `bottom` valeursont`RECT` soustraites des membres de données, ,etdelavaleur.`right` Elle est analogue à la version de [CRect :: Operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-) qui accepte un paramètre de [taille](/windows/win32/api/windef/ns-windef-size) .

- **operator -()**

  Cette opération retourne l’inverse additif de cette `CSize` valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint, classe](../../atl-mfc-shared/reference/cpoint-class.md)
