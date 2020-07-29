---
title: CTypedPtrArray, classe
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: db24e3992e5db70895ccc2908dba108de843bcdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215944"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray, classe

Fournit un « wrapper » de type sécurisé pour les objets de la classe `CPtrArray` ou `CObArray`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés ; doit être une classe de tableau ( `CObArray` ou `CPtrArray` ).

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray :: Add](#add)|Ajoute un nouvel élément à la fin d’un tableau. Augmente le tableau si nécessaire|
|[CTypedPtrArray :: Append](#append)|Ajoute le contenu d’un tableau à la fin d’un autre. Augmente le tableau si nécessaire|
|[CTypedPtrArray :: Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CTypedPtrArray :: ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CTypedPtrArray :: GetAt](#getat)|Retourne la valeur à un index donné.|
|[CTypedPtrArray :: InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CTypedPtrArray :: SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CTypedPtrArray :: SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray ::, opérateur \[\]](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Lorsque vous utilisez `CTypedPtrArray` plutôt que `CPtrArray` ou `CObArray` , la fonctionnalité de contrôle de type C++ permet d’éliminer les erreurs provoquées par des types pointeur incompatibles.

En outre, le `CTypedPtrArray` Wrapper effectue une grande partie du cast qui serait nécessaire si vous utilisiez `CObArray` ou `CPtrArray` .

Étant donné que toutes les `CTypedPtrArray` fonctions sont Inline, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation de `CTypedPtrArray` , consultez les articles [Collections](../../mfc/collections.md) et [classes basées sur des modèles](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray :: Add

Cette fonction membre appelle `BASE_CLASS` **:: Add**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’élément à ajouter au tableau.

*newElement*<br/>
Élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

Index de l’élément ajouté.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [CObArray :: Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray :: Append

Cette fonction membre appelle `BASE_CLASS` :: Append * *.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés ; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

*src*<br/>
Source des éléments à ajouter à un tableau.

### <a name="return-value"></a>Valeur de retour

Index du premier élément ajouté.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray :: Copy

Cette fonction membre appelle `BASE_CLASS` **:: Copy**.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés ; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

*src*<br/>
Source des éléments à copier dans un tableau.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray :: ElementAt

Cette fonction inline appelle `BASE_CLASS` **:: ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans ce tableau.

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Référence temporaire à l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le *type*de paramètre de modèle.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray :: GetAt

Cette fonction inline appelle `BASE_CLASS` **:: GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Copie de l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le *type*de paramètre de modèle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [CObArray :: GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray :: InsertAt

Cette fonction membre appelle `BASE_CLASS` **:: InsertAt**.

```cpp
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui peut être supérieur à la valeur retournée par [CObArray :: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

*newElement*<br/>
Pointeur d’objet à placer dans ce tableau. Un *newelement* de valeur **null** est autorisé.

*nCount*<br/>
Nombre de fois où cet élément doit être inséré (1 par défaut).

*nStartIndex*<br/>
Index entier qui peut être supérieur à la valeur retournée par `CObArray::GetUpperBound` .

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés ; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Autre tableau qui contient les éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray :: Operator []

Ces opérateurs Inline appellent `BASE_CLASS` **:: Operator []**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour les tableaux qui ne le sont pas **`const`** , peut être utilisé sur le droit (r-value) ou sur la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour les **`const`** tableaux, peut être utilisée uniquement à droite.

La version de débogage de la bibliothèque déclare si l’indice (à gauche ou à droite d’une instruction d’assignation) est hors limites.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray :: SetAt

Cette fonction membre appelle `BASE_CLASS` **:: setat**.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [CObArray :: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

*ptr*<br/>
Pointeur vers l’élément à insérer dans le tableau au niveau du nIndex. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: setat](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray :: SetAtGrow

Cette fonction membre appelle `BASE_CLASS` **:: SetAtGrow**.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier supérieur ou égal à 0.

*TYPE*<br/>
Type des éléments stockés dans le tableau de la classe de base.

*newElement*<br/>
Pointeur d’objet à ajouter à ce tableau. Une valeur **null** est autorisée.

### <a name="remarks"></a>Notes

Pour obtenir des remarques plus détaillées, consultez [CObArray :: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray, classe](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
