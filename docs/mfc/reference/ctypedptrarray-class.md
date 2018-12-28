---
title: CTypedPtrArray (classe)
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
ms.openlocfilehash: 767d4782ec637a0404051e6871d584f73cefdcd2
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657472"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray (classe)

Fournit un « wrapper » de type sécurisé pour les objets de la classe `CPtrArray` ou `CObArray`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( `CObArray` ou `CPtrArray`).

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|Ajoute un nouvel élément à la fin d’un tableau. Étend le tableau si nécessaire|
|[CTypedPtrArray::Append](#append)|Ajoute le contenu d’un tableau à la fin d’un autre. Étend le tableau si nécessaire|
|[CTypedPtrArray::Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CTypedPtrArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CTypedPtrArray::GetAt](#getat)|Retourne la valeur à un index donné.|
|[CTypedPtrArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CTypedPtrArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTypedPtrArray::operator \[ \]](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Lorsque vous utilisez `CTypedPtrArray` plutôt que `CPtrArray` ou `CObArray`, la fonctionnalité de vérification de type C++ permet d’éliminer les erreurs provoquées par les types de pointeur qui ne correspondent pas.

En outre, le `CTypedPtrArray` wrapper effectue une grande partie des opérations de cast qui serait nécessaire si vous avez utilisé `CObArray` ou `CPtrArray`.

Étant donné que tous les `CTypedPtrArray` fonctions inline, utilisation de ce modèle ne pas affecte de manière significative la taille ou la vitesse de votre code.

Pour plus d’informations sur l’utilisation de `CTypedPtrArray`, consultez les articles [Collections](../../mfc/collections.md) et [Classes basées sur le modèle](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

Cette fonction membre appelle `BASE_CLASS` **:: ajouter**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’élément à ajouter au tableau.

*newElement*<br/>
L’élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

##  <a name="append"></a>  CTypedPtrArray::Append

Cette fonction membre appelle `BASE_CLASS`:: Append **.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

*src*<br/>
Source des éléments à ajouter à un tableau.

### <a name="return-value"></a>Valeur de retour

L’index du premier élément ajouté.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

##  <a name="copy"></a>  CTypedPtrArray::Copy

Cette fonction membre appelle `BASE_CLASS` **:: copie**.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Paramètres

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

*src*<br/>
Source des éléments à copier vers un tableau.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

Cette fonction inline s’appelle `BASE_CLASS` **:: ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans ce tableau.

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Une référence temporaire à l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre de modèle *TYPE*.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

##  <a name="getat"></a>  CTypedPtrArray::GetAt

Cette fonction inline s’appelle `BASE_CLASS` **:: GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Valeur de retour

Une copie de l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre de modèle *TYPE*.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

Cette fonction membre appelle `BASE_CLASS` **:: InsertAt**.

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
Un index d’entiers qui peut être supérieur à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

*newElement*<br/>
Le pointeur d’objet est placé dans ce tableau. Un *newElement* de valeur **NULL** est autorisée.

*nCount*<br/>
Le nombre de fois où que cet élément doit être inséré (1 par défaut).

*nStartIndex*<br/>
Un index d’entiers qui peut être supérieur à la valeur retournée par `CObArray::GetUpperBound`.

*BASE_CLASS*<br/>
Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Un autre tableau qui contient les éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

##  <a name="operator_at"></a>  [] CTypedPtrArray::operator

Ces opérateurs inline appellent `BASE_CLASS` **:: [] opérateur**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.

### <a name="remarks"></a>Notes

Le premier opérateur, appelée pour les tableaux qui ne sont pas **const**, peut être utilisé sur la droite (r-value) ou la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour **const** tableaux, peut être utilisé uniquement sur la droite.

La version Debug de la bibliothèque déclare si l’indice (soit sur le côté gauche ou droit d’une instruction d’assignation) est hors limites.

##  <a name="setat"></a>  CTypedPtrArray::SetAt

Cette fonction membre appelle `BASE_CLASS` **:: SetAt**.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

*ptr*<br/>
Pointeur vers l’élément à insérer dans le tableau à partir de la nIndex. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

Cette fonction membre appelle `BASE_CLASS` **:: SetAtGrow**.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0.

*TYPE*<br/>
Type des éléments stockés dans le tableau de classe de base.

*newElement*<br/>
Le pointeur d’objet à ajouter à ce tableau. Un **NULL** la valeur est autorisée.

### <a name="remarks"></a>Notes

Pour plus de remarques, consultez [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray, classe](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
