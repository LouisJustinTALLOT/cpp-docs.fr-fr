---
title: Classe CSize
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
ms.openlocfilehash: 6d1b82e3f60428e3a778709dc69de983a7f886bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317673"
---
# <a name="csize-class"></a>Classe CSize

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
|[CSize::opérateur -](#operator_-)|Soustraite deux tailles.|
|[CSize::opérateur !](#operator_neq)|Contrôle de `CSize` l’inégalité entre et une taille.|
|[CSize::opérateur](#operator_add)|Ajoute deux tailles.|
|[CSize::opérateur](#operator_add_eq)|Ajoute une `CSize`taille à .|
|[CSize::opérateur -MD](#operator_-_eq)|Soustraite une `CSize`taille de .|
|[CSize::opérateur](#operator_eq_eq)|Vérifications de `CSize` l’égalité entre et une taille.|

## <a name="remarks"></a>Notes

Cette classe est `SIZE` dérivée de la structure. Cela signifie que vous `CSize` pouvez passer un `SIZE` paramètre qui nécessite `SIZE` un et que `CSize`les membres des données de la structure sont des membres de données accessibles de .

Le `cx` `cy` et `SIZE` les `CSize`membres de (et ) sont publics. En outre, `CSize` met en œuvre les fonctions des membres pour manipuler la `SIZE` structure.

> [!NOTE]
> Pour plus d’informations sur `CSize`les cours d’utilité partagée (comme ), voir [Classes partagées](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagSIZE`

`CSize`

## <a name="requirements"></a>Spécifications

**En-tête:** atltypes.h

## <a name="csizecsize"></a><a name="csize"></a>CSize::CSize

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
Définit `cx` le membre `CSize`pour le .

*initCY*<br/>
Définit `cy` le membre `CSize`pour le .

*initSize*<br/>
[Structure](/windows/win32/api/windef/ns-windef-size) SIZE `CSize` ou objet `CSize`utilisé pour initialiser .

*initPt*<br/>
[Structure](/windows/win32/api/windef/ns-windef-point) POINT `CPoint` ou objet `CSize`utilisé pour initialiser .

*dwSize dwSize*<br/>
DWORD utilisé pour `CSize`l’initialisation . Le mot de bas `cx` ordre est le membre `cy` et le mot de haut ordre est le membre.

### <a name="remarks"></a>Notes

Si aucun argument `cx` n’est donné, et `cy` sont parasécés à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>CSize::opérateur

Vérifications de l’égalité entre deux tailles.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne nonzero si les tailles sont égales, otherwize 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::opérateur !

Contrôle de l’inégalité entre deux tailles.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Notes

Retourne nonzero si les tailles ne sont pas égales, sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>CSize::opérateur

Ajoute une taille `CSize`à cela .

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>CSize::opérateur -MD

Soustrait une taille `CSize`de cela .

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize::opérateur

Ces opérateurs `CSize` ajoutent cette valeur à la valeur du paramètre.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Notes

Voir les descriptions suivantes des opérateurs individuels :

- **opérateur** *(taille)* **)**

  Cette opération `CSize` ajoute deux valeurs.

- **opérateur** *(point)* **)**

  Cette opération compense (déplace) une valeur [POINT](/previous-versions/dd162805\(v=vs.85\)) (ou [CPoint)](../../atl-mfc-shared/reference/cpoint-class.md)par cette `CSize` valeur. La `cx` `cy` valeur et `CSize` les `x` membres de `y` cette valeur `POINT` sont ajoutés aux membres et aux données de la valeur. Il est analogue à la version de [CPoint::opérateur -](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) qui prend un paramètre [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **opérateur** *(lpRect* **)**

   Cette opération compense (déplace) une valeur [RECT](/previous-versions/dd162897\(v=vs.85\)) (ou `CSize` [CRect)](../../atl-mfc-shared/reference/crect-class.md)par cette valeur. La `cx` `cy` valeur et `CSize` les membres `left`de `top` `right`cette `bottom` valeur sont `RECT` ajoutés aux membres de la valeur, et les données. Il est analogue à la version de [CRect::opérateur -](../../atl-mfc-shared/reference/crect-class.md#operator_add) qui prend un paramètre [SIZE.](/windows/win32/api/windef/ns-windef-size)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize::opérateur -

Les trois premiers de ces `CSize` opérateurs soustraient cette valeur à la valeur du paramètre.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Notes

Le quatrième opérateur, l’unary moins, `CSize` change le signe de la valeur. Voir les descriptions suivantes des opérateurs individuels :

- **opérateur -(** *taille* **)**

  Cette opération soustrait deux `CSize` valeurs.

- **opérateur -(** *point* **)**

  Cette opération compense (déplace) une valeur [POINT](/previous-versions/dd162805\(v=vs.85\)) ou [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) par l’inverse additif de cette `CSize` valeur. La `cx` `cy` valeur `CSize` et de cette valeur `x` `y` sont soustraites des membres et des données de la `POINT` valeur. Il est analogue à la version de [CPoint::opérateur -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) qui prend un paramètre [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **opérateur -(** *lpRect* **)**

  Cette opération compense (déplace) une valeur [RECT](/previous-versions/dd162897\(v=vs.85\)) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) par l’inverse additif de cette `CSize` valeur. Le `cx` `cy` et les `CSize` membres de cette `left`valeur `top` `right`sont `bottom` soustraits `RECT` de la , , et les membres de données de la valeur. Il est analogue à la version de [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) qui prend un paramètre [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **opérateur -()**

  Cette opération renvoie l’inverse additif de cette `CSize` valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRect](../../atl-mfc-shared/reference/crect-class.md)<br/>
[Classe CPoint](../../atl-mfc-shared/reference/cpoint-class.md)
