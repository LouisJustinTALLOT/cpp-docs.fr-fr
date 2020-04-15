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
ms.openlocfilehash: a996bca471ce82a7c2adaaad67670ddef417eda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373277"
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
Classe de base de la classe de tableau de pointeur dactylographie; doit être une `CObArray` classe `CPtrArray`de tableau ( ou ).

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray::Ajouter](#add)|Ajoute un nouvel élément à la fin d’un tableau. Développe le tableau si nécessaire|
|[CTypedPtrArray::Append](#append)|Ajoute le contenu d’un tableau à la fin d’un autre. Développe le tableau si nécessaire|
|[CTypedPtrArray::Copie](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CTypedPtrArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CTypedPtrArray::GetAt](#getat)|Retourne la valeur à un index donné.|
|[CTypedPtrArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CTypedPtrArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray::opérateur \[\]](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Lorsque vous `CTypedPtrArray` utilisez `CPtrArray` `CObArray`plutôt que ou, l’installation de vérification de type CMD aide à éliminer les erreurs causées par des types de pointeurs dépareillés.

En outre, `CTypedPtrArray` l’emballage effectue une grande partie de `CObArray` la `CPtrArray`coulée qui serait nécessaire si vous avez utilisé ou .

Étant `CTypedPtrArray` donné que toutes les fonctions sont inlines, l’utilisation de ce modèle n’affecte pas de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation `CTypedPtrArray`, voir les articles [Collections](../../mfc/collections.md) et [Template-Based Classes](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray::Ajouter

Cette fonction `BASE_CLASS`de membre appelle **::Ajouter**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’élément à ajouter au tableau.

*nouvel Element*<br/>
L’élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::Ajouter](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray::Append

Cette fonction `BASE_CLASS`de membre appelle ::Append.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeur dactylographie; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

*src*<br/>
Source des éléments à annexer à un tableau.

### <a name="return-value"></a>Valeur de retour

L’index du premier élément joint.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray::Copie

Cette fonction `BASE_CLASS`de membre appelle **::Copie**.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeur dactylographie; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

*src*<br/>
Source des éléments à copier à un tableau.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Cette fonction en `BASE_CLASS`ligne appelle **::ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans ce tableau.

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `BASE_CLASS`ou égal à la valeur retournée par **::GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Une référence temporaire à l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre type *TYPE*.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Cette fonction en `BASE_CLASS`ligne appelle **::GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans le tableau.

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `BASE_CLASS`ou égal à la valeur retournée par **::GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Une copie de l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre type *TYPE*.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Cette fonction `BASE_CLASS`de membre appelle **::InsertAt**.

```
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
Un indice d’intégrateur qui peut être supérieur à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

*nouvel Element*<br/>
Le pointeur d’objet à placer dans ce tableau. Un *nouvel Element* de la valeur **NULL** est autorisé.

*nCompte*<br/>
Le nombre de fois cet élément doit être inséré (par défaut à 1).

*nStartIndex*<br/>
Un indice d’intégration qui peut `CObArray::GetUpperBound`être supérieur à la valeur retournée par .

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeur dactylographie; doit être une classe de tableau ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray (en)*<br/>
Un autre tableau qui contient des éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray::opérateur [ ]

Ces opérateurs en `BASE_CLASS`ligne appellent **::opérateur [ ]**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments stockés dans le tableau.

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `BASE_CLASS`ou égal à la valeur retournée par **::GetUpperBound**.

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour des tableaux qui ne sont pas **const**, peut être utilisé soit sur la droite (r-valeur) ou la gauche (l-valeur) d’une déclaration d’affectation. Le second, invoqué pour les tableaux **de cônes,** ne peut être utilisé que sur la droite.

La version Debug de la bibliothèque affirme si le sous-scriptum (soit sur le côté gauche ou à droite d’une déclaration d’affectation) est hors limites.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Cette fonction `BASE_CLASS`de membre appelle **::SetAt**.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

*Ptr*<br/>
Un pointeur à l’élément à insérer dans le tableau à l’index n. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Cette fonction `BASE_CLASS`de membre appelle **::SetAtGrow**.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0.

*TYPE*<br/>
Type des éléments stockés dans le tableau de base.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à ce tableau. Une valeur **NULL** est autorisée.

### <a name="remarks"></a>Notes

Pour des remarques plus détaillées, voir [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray, classe](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
