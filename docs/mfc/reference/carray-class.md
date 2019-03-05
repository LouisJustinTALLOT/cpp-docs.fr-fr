---
title: CArray (classe)
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 342eea1d5bcf8adfe9a9ff0e8d915c9155b413ca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266131"
---
# <a name="carray-class"></a>CArray (classe)

Prend en charge les tableaux qui ressemblent à des tableaux C, mais peuvent réduire et dynamiquement selon les besoins de la croissance.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des objets stockés dans le tableau. *TYPE* est un paramètre qui est retourné par `CArray`.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’argument qui est utilisé pour accéder aux objets stockés dans le tableau. Souvent, une référence à *TYPE*. *ARG_TYPE* est un paramètre qui est passé à `CArray`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArray::CArray](#carray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CArray::Add](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CArray::Append](#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire|
|[CArray::Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CArray::FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CArray::GetAt](#getat)|Retourne la valeur à un index donné.|
|[CArray::GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CArray::GetData](#getdata)|Autorise l'accès aux éléments du tableau. Peut être NULL.|
|[CArray::GetSize](#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CArray::GetUpperBound](#getupperbound)|Retourne le plus grand index valide.|
|[CArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CArray::IsEmpty](#isempty)|Détermine si le tableau est vide.|
|[CArray::RemoveAll](#removeall)|Supprime tous les éléments de ce tableau.|
|[CArray::RemoveAt](#removeat)|Supprime un élément à un index spécifique.|
|[CArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CArray::SetSize](#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut corriger la limite supérieure ou activer le tableau développer lorsque vous ajoutez des éléments au-delà de cours lié. Mémoire est allouée de façon contiguë à la limite supérieure, même si certains éléments sont null.

> [!NOTE]
>  La plupart des méthodes redimensionner un `CArray` de l’objet ou ajouter des éléments à ce dernier utilisent [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) pour déplacer des éléments. C’est un problème, car `memcpy_s` n’est pas compatible avec tous les objets qui nécessitent le constructeur à appeler. Si les éléments dans le `CArray` ne sont pas compatibles avec `memcpy_s`, vous devez créer un nouveau `CArray` de la taille appropriée. Vous devez ensuite utiliser [CArray::Copy](#copy) et [CArray::SetAt](#setat) pour remplir le nouveau tableau, car ces méthodes utilisent un opérateur d’assignation à la place de `memcpy_s`.

Comme avec un tableau de C, le temps d’accès pour un `CArray` élément indexé est constante et est indépendant de la taille du tableau.

> [!TIP]
>  Avant d’utiliser un tableau, utilisez [SetSize](#setsize) pour établir sa taille et l’allocation de mémoire pour elle. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin de vider des éléments individuels dans un tableau, vous devez définir la profondeur de la [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objet à 1 ou supérieure.

Certaines fonctions de membre de cet appel de la classe d’assistance globales des fonctions qui doivent être personnalisées pour la plupart des utilisations de la `CArray` classe. Consultez la rubrique [Assistants de classe de Collection](../../mfc/reference/collection-class-helpers.md) dans la section MFC Macros and Globals.

Dérivation de classe de tableau est semblable à dérivation de la liste.

Pour plus d’informations sur l’utilisation `CArray`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

##  <a name="add"></a>  CArray::Add

Ajoute un nouvel élément à la fin d’un tableau ne soit le tableau 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type des arguments faisant référence à des éléments dans ce tableau.

*newElement*<br/>
L’élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Si [SetSize](#setsize) a été utilisé avec un `nGrowBy` valeur supérieure à 1, puis de mémoire supplémentaire peut être allouée. Toutefois, la limite supérieure augmente de 1 uniquement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>  CArray::Append

Appelez cette fonction membre pour ajouter le contenu d’un tableau à la fin d’un autre.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à ajouter à un tableau.

### <a name="return-value"></a>Valeur de retour

L’index du premier élément ajouté.

### <a name="remarks"></a>Notes

Les tableaux doivent être du même type.

Si nécessaire, `Append` peut allouer de mémoire supplémentaire pour prendre en compte les éléments ajoutés au tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>  CArray::CArray

Construit un tableau vide.

```
CArray();
```

### <a name="remarks"></a>Notes

Le tableau développe un élément à la fois.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>  CArray::Copy

Utilisez cette fonction membre copie les éléments d’un tableau à un autre.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à copier vers un tableau.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour remplacer les éléments d’un tableau avec les éléments d’un autre tableau.

`Copy` ne pas libérer de la mémoire ; Toutefois, si nécessaire, `Copy` peut allouer de mémoire supplémentaire pour prendre en compte les éléments copiés dans le tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>  CArray::ElementAt

Retourne une référence temporaire à l’élément spécifié dans le tableau.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur de retour

Une référence à un élément de tableau.

### <a name="remarks"></a>Notes

Il est utilisé pour implémenter l’opérateur d’assignation de gauche pour les tableaux.

### <a name="example"></a>Exemple

  Consultez l’exemple de [GetSize](#getsize).

##  <a name="freeextra"></a>  CArray::FreeExtra

Libère la mémoire supplémentaire qui a été alloué tandis que le tableau a été augmenté.

```
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.

### <a name="example"></a>Exemple

  Consultez l’exemple de [GetData](#getdata).

##  <a name="getat"></a>  CArray::GetAt

Retourne l’élément de tableau à l’index spécifié.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments du tableau.

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur de retour

L’élément de tableau actuellement à cet index.

### <a name="remarks"></a>Notes

En passant une valeur négative ou une valeur supérieure à la valeur retournée par `GetUpperBound` entraîne un échec d’assertion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>  CArray::GetCount

Retourne le nombre d’éléments de tableau.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les index sont de base zéro, la taille est 1 supérieur le plus grand index. L’appel de cette méthode génère le même résultat que la [CArray::GetSize](#getsize) (méthode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>  CArray::GetData

Utilisez cette fonction membre pour obtenir un accès direct aux éléments dans un tableau.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments du tableau.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un élément de tableau.

### <a name="remarks"></a>Notes

Si aucun élément n’est disponibles, `GetData` retourne une valeur null.

Bien que l’accès direct aux éléments d’un tableau peut vous aider à travailler plus rapidement, soyez prudent lors de l’appel `GetData`; les erreurs que vous apportez directement affectent les éléments de votre tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>  CArray::GetSize

Retourne la taille du tableau.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Notes

Étant donné que les index sont de base zéro, la taille est 1 supérieur le plus grand index. L’appel de cette méthode génère le même résultat que la [CArray::GetCount](#getcount) (méthode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>  CArray::GetUpperBound

Retourne la limite supérieure en cours de ce tableau.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Notes

Étant donné que les index de tableau sont de base zéro, cette fonction retourne une valeur de 1 inférieur à `GetSize`.

La condition `GetUpperBound( )` = -1 indique que le tableau ne contient aucun élément.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CArray::GetAt](#getat).

##  <a name="insertat"></a>  CArray::InsertAt

La première version de `InsertAt` insère un élément (ou plusieurs copies d’un élément) à l’index spécifié dans un tableau.

```
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entiers qui peut être supérieur à la valeur retournée par `GetUpperBound`.

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments dans ce tableau.

*newElement*<br/>
L’élément à être placé dans ce tableau.

*nCount*<br/>
Le nombre de fois où que cet élément doit être inséré (1 par défaut).

*nStartIndex*<br/>
Un index d’entiers qui peut être supérieur à la valeur retournée par [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Un autre tableau qui contient les éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Dans le processus, il se déplace (en augmentant l’index) l’élément existant à cet index et il se déplace tous les éléments au-dessus de lui.

La deuxième version insère tous les éléments d’un autre `CArray` collection, en commençant à la *nStartIndex* position.

Le `SetAt` (fonction), en revanche, remplace un élément de tableau spécifié et tous les éléments n’est pas transférée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>  CArray::IsEmpty

Détermine si le tableau est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le tableau ne contient aucun élément ; sinon 0.

##  <a name="operator_at"></a>  CArray::operator \[\]

Ces opérateurs d’indice sont une alternative pratique à la [SetAt](#setat) et [GetAt](#getat) fonctions.

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments dans ce tableau.

*nIndex*<br/>
Index de l’élément accessible.

### <a name="remarks"></a>Notes

Le premier opérateur, appelée pour les tableaux qui ne sont pas **const**, peut être utilisée sur la droite (r-value) ou la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour **const** tableaux, peut être utilisé uniquement sur la droite.

La version Debug de la bibliothèque déclare si l’indice (soit sur le côté gauche ou droit d’une instruction d’assignation) est hors limites.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>  CArray::RelocateElements

Déplace les données vers une nouvelle mémoire tampon lorsque le tableau doit augmenter ou réduire.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*pNewData*<br/>
Une nouvelle mémoire tampon pour le tableau d’éléments.

*pData*<br/>
L’ancien tableau d’éléments.

*nCount*<br/>
Nombre d’éléments dans le tableau ancien.

### <a name="remarks"></a>Notes

*pNewData* est toujours suffisamment grande pour contenir tous les *pData* éléments.

Le [CArray](../../mfc/reference/carray-class.md) implémentation utilise cette méthode pour copier les anciennes données vers une nouvelle mémoire tampon lorsque le tableau doit augmenter ou réduire (lorsque [SetSize](#setsize) ou [FreeExtra](#freeextra) sont appelées). L’implémentation par défaut copie simplement les données.

Pour les tableaux dans lequel un élément contient un pointeur vers un de ses propres membres, ou une autre structure contient un pointeur vers un des éléments du tableau, les pointeurs ne sont pas mises à jour dans copie ordinaire. Dans ce cas, vous pouvez corriger les pointeurs en implémentant une spécialisation de `RelocateElements` avec les types pertinents. Vous êtes également chargé de la copie de données.

##  <a name="removeall"></a>  CArray::RemoveAll

Supprime tous les éléments de ce tableau.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Si le tableau est déjà vide, la fonction fonctionne toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>  CArray::RemoveAt

Supprime un ou plusieurs éléments, en commençant à un index spécifié dans un tableau.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par [GetUpperBound](#getupperbound).

*nCount*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Dans le processus, il se déplace vers le bas tous les éléments situés au-dessus de l’élément supprimé (s). Il décrémente le coin supérieur limite du tableau, mais ne libère pas de mémoire.

Si vous essayez de supprimer plus d’éléments contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque assertions.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>  CArray::SetAt

Définit l’élément de tableau à l’index spécifié.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’arguments utilisés pour faire référence à des éléments de tableau.

*newElement*<br/>
La nouvelle valeur d’élément à stocker à la position spécifiée.

### <a name="remarks"></a>Notes

`SetAt` n’entraîne pas le tableau de croître. Utilisez [SetAtGrow](#setatgrow) si vous souhaitez que le tableau à croître automatiquement.

Vous devez vous assurer que votre valeur d’index représente une position valide dans le tableau. Si elle est hors limites, la version Debug de la bibliothèque assertions.

### <a name="example"></a>Exemple

  Consultez l’exemple de [GetAt](#getat).

##  <a name="setatgrow"></a>  CArray::SetAtGrow

Définit l’élément de tableau à l’index spécifié.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un index d’entier qui est supérieur ou égal à 0.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments dans le tableau.

*newElement*<br/>
L’élément à ajouter à ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Le tableau s’étend automatiquement si nécessaire (autrement dit, la limite supérieure est ajustée pour prendre en compte le nouvel élément).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>  CArray::SetSize

Établit la taille d’un tableau vide ou existant ; alloue de la mémoire si nécessaire.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Paramètres

*nNewSize*<br/>
La nouvelle taille du tableau (nombre d’éléments). Doit être supérieur ou égal à 0.

*nGrowBy*<br/>
Le nombre minimal d’emplacements d’élément pour allouer si une augmentation de la taille est nécessaire.

### <a name="remarks"></a>Notes

Si la nouvelle taille est inférieure à l’ancienne taille, puis du tableau est tronqué et de toute la mémoire inutilisée est libérée.

Utilisez cette fonction pour définir la taille de votre tableau avant de commencer à l’aide du tableau. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Le *nGrowBy* paramètre affecte l’allocation de mémoire interne pendant que le tableau se développe. Son utilisation n’affecte jamais la taille du tableau comme indiqué par [GetSize](#getsize) et [GetUpperBound](#getupperbound). Si la valeur par défaut est utilisée, MFC alloue la mémoire dans un mode de calcul pour éviter la fragmentation de mémoire et optimiser l’efficacité pour la plupart des cas.

### <a name="example"></a>Exemple

  Consultez l’exemple de [GetData](#getdata).

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)<br/>
[Programmes d’assistance pour les classes de collection](../../mfc/reference/collection-class-helpers.md)
