---
title: CSize, classe
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
ms.openlocfilehash: 5e19ab9b9339f3e6f61abf7731a40ed3832b50c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252686"
---
# <a name="csize-class"></a>CSize, classe

Semblable à la structure [SIZE](/windows/desktop/api/windef/ns-windef-tagsize) Windows, qui implémente une coordonnée ou une position relative.

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
|[CSize::operator-](#operator_-)|Soustrait deux tailles.|
|[CSize::operator !=](#operator_neq)|Vérifie l’inégalité entre `CSize` et une taille.|
|[CSize::operator +](#operator_add)|Ajoute deux tailles.|
|[CSize::operator +=](#operator_add_eq)|Ajoute une taille à `CSize`.|
|[CSize::operator -=](#operator_-_eq)|Soustrait une taille de `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Vérifie l’égalité entre `CSize` et une taille.|

## <a name="remarks"></a>Notes

Cette classe est dérivée de la `SIZE` structure. Cela signifie que vous pouvez passer un `CSize` dans un paramètre qui demande un `SIZE` et que les membres de données de la `SIZE` structure sont membres de données accessibles de `CSize`.

Le `cx` et `cy` membres de `SIZE` (et `CSize`) sont publics. En outre, `CSize` implémente les fonctions de membre pour manipuler le `SIZE` structure.

> [!NOTE]
> Pour plus d’informations sur les classes de l’utilitaire de partagées (telles que `CSize`), consultez [Classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagSIZE`

`CSize`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltypes.h

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
[TAILLE](/windows/desktop/api/windef/ns-windef-tagsize) structure ou `CSize` objet utilisé pour initialiser `CSize`.

*initPt*<br/>
[POINT](/windows/desktop/api/windef/ns-windef-tagpoint) structure ou `CPoint` objet utilisé pour initialiser `CSize`.

*dwSize*<br/>
DWORD permettant d’initialiser `CSize`. Le mot de poids faible est le `cx` membre et le mot de poids fort est le `cy` membre.

### <a name="remarks"></a>Notes

Si aucun argument n’est fourni, `cx` et `cy` sont initialisés à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator ==

Vérifie l’égalité entre deux tailles.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne zéro si les tailles sont égales, otherwize 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator !=

Vérifie l’inégalité entre deux tailles.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne zéro si la taille n’est pas égale, sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator +=

Ajoute une taille à ce `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator -=

Soustrait une taille à partir de ce `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

Ces opérateurs ajouter cela `CSize` valeur à la valeur du paramètre.

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

  Cette opération offsets (déplace) un [POINT](/previous-versions/dd162805\(v=vs.85\)) (ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) la valeur par ce `CSize` valeur. Le `cx` et `cy` membres de ce `CSize` valeur sont ajoutés à la `x` et `y` membres de données de la `POINT` valeur. Elle est analogue à la version de [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) qui accepte un [taille](/windows/desktop/api/windef/ns-windef-tagsize) paramètre.

- **operator +(** *lpRect* **)**

   Cette opération offsets (déplace) un [RECT](/previous-versions/dd162897\(v=vs.85\)) (ou [CRect](../../atl-mfc-shared/reference/crect-class.md)) la valeur par ce `CSize` valeur. Le `cx` et `cy` membres de ce `CSize` valeur sont ajoutés à la `left`, `top`, `right`, et `bottom` membres de données de la `RECT` valeur. Elle est analogue à la version de [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) qui accepte un [taille](/windows/desktop/api/windef/ns-windef-tagsize) paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator -

Les trois premiers de ces opérateurs soustraire cela `CSize` valeur à la valeur du paramètre.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Notes

L’opérateur quatrième, l’unaire, modifie le signe de la `CSize` valeur. Consultez les descriptions suivantes des opérateurs individuels :

- **opérateur-(** *taille* **)**

  Cette opération Soustrait deux `CSize` valeurs.

- **operator -(** *point* **)**

  Cette opération offsets (déplace) un [POINT](/previous-versions/dd162805\(v=vs.85\)) ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) valeur par l’inverse additif de ce `CSize` valeur. Le `cx` et `cy` de ce `CSize` valeur sont soustraites de la `x` et `y` membres de données de la `POINT` valeur. Elle est analogue à la version de [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) qui accepte un [taille](/windows/desktop/api/windef/ns-windef-tagsize) paramètre.

- **operator -(** *lpRect* **)**

  Cette opération offsets (déplace) un [RECT](/previous-versions/dd162897\(v=vs.85\)) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) valeur par l’inverse additif de ce `CSize` valeur. Le `cx` et `cy` membres de ce `CSize` valeur sont soustraites de la `left`, `top`, `right`, et `bottom` membres de données de la `RECT` valeur. Elle est analogue à la version de [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) qui accepte un [taille](/windows/desktop/api/windef/ns-windef-tagsize) paramètre.

- **operator -()**

  Cette opération retourne l’inverse additif de ce `CSize` valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint, classe](../../atl-mfc-shared/reference/cpoint-class.md)
