---
title: CAtlArray, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775697"
---
# <a name="catlarray-class"></a>CAtlArray, classe

Cette classe implémente un objet tableau.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Type de données à stocker dans le tableau.

*ETraits*<br/>
Le code utilisé pour copier ou déplacer des éléments.

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Ajouter](#add)|Appelez cette méthode pour ajouter un élément à l’objet de tableau.|
|[Ajouter](#append)|Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.|
|[AssertValid](#assertvalid)|Appelez cette méthode pour vérifier que l’objet de tableau est valide.|
|[CAtlArray](#catlarray)|Constructeur.|
|[~CAtlArray](#dtor)|Destructeur.|
|[Copier](#copy)|Appelez cette méthode pour copier les éléments d’un tableau à un autre.|
|[FreeExtra](#freeextra)|Appelez cette méthode pour supprimer tous les éléments vides du tableau.|
|[GetAt](#getat)|Appelez cette méthode pour récupérer un seul élément à partir de l’objet de tableau.|
|[GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.|
|[GetData](#getdata)|Appelez cette méthode pour retourner un pointeur vers le premier élément du tableau.|
|[InsertArrayAt](#insertarrayat)|Appelez cette méthode pour insérer un tableau dans un autre.|
|[InsertAt](#insertat)|Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet de tableau.|
|[IsEmpty](#isempty)|Appelez cette méthode pour tester si le tableau est vide.|
|[RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de l’objet de tableau.|
|[RemoveAt](#removeat)|Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.|
|[SetAt](#setat)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet tableau.|
|[SetAtGrow](#setatgrow)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en développant le tableau en fonction des besoins.|
|[SetCount](#setcount)|Appelez cette méthode pour définir la taille de l’objet de tableau.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator &#91;&#93;](#operator_at)|Appeler cet opérateur pour retourner une référence à un élément dans le tableau.|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments dans le tableau.|
|[OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments à partir du tableau.|

## <a name="remarks"></a>Notes

`CAtlArray` Fournit des méthodes pour créer et gérer un tableau d’éléments d’un type défini par l’utilisateur. Bien que semblable à des tableaux C standard, le `CAtlArray` objet peut dynamiquement réduire et évoluer si nécessaire. L’index de tableau commence toujours à la position 0, et la limite supérieure peut être fixe ou autorisée développe à mesure que les nouveaux éléments sont ajoutés.

Pour les tableaux avec un petit nombre d’éléments, la classe ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) peut être utilisé.

`CAtlArray` est étroitement liée à MFC `CArray` classe et fonctionnera dans un projet MFC, sans toutefois de prise en charge de la sérialisation.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

Appelez cette méthode pour ajouter un élément à l’objet de tableau.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Paramètres

*element*<br/>
L’élément à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Le nouvel élément est ajouté à la fin du tableau. Si aucun élément n’est fourni, un élément vide est ajouté ; Autrement dit, le tableau est augmenter la taille comme si un élément réel a été ajouté. Si l’opération échoue, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) est appelé avec l’argument E_OUTOFMEMORY.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*aSrc*<br/>
Le tableau à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne l’index du premier élément ajouté.

### <a name="remarks"></a>Notes

Les éléments du tableau fourni sont ajoutés à la fin du tableau existant. Si nécessaire, mémoire sera allouée pour prendre en compte les nouveaux éléments.

Les tableaux doivent être du même type, et il n’est pas possible d’ajouter un tableau à lui-même.

Dans les versions debug, un ATLASSERT ; sera déclenchée si le `CAtlArray` argument n’est pas un tableau valide ou si *aSrc* fait référence au même objet. Arguments non valides dans les versions release, peuvent entraîner un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

Appelez cette méthode pour vérifier que l’objet de tableau est valide.

```
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Si l’objet de tableau n’est pas valide, ATLASSERT ; lèvera une assertion. Cette méthode est disponible uniquement si _DEBUG est défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

Constructeur.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Initialise l’objet de tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  CAtlArray::~CAtlArray

Destructeur.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources utilisées par l’objet de tableau.

##  <a name="copy"></a>  CAtlArray::Copy

Appelez cette méthode pour copier les éléments d’un tableau à un autre.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*aSrc*<br/>
La source des éléments à copier dans un tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour remplacer les éléments d’un tableau avec les éléments d’un autre tableau. Si nécessaire, mémoire sera allouée pour prendre en compte les nouveaux éléments. Il n’est pas possible de copier des éléments d’un tableau à lui-même.

Si le contenu existant du tableau doivent être conservées, utilisez [CAtlArray::Append](#append) à la place.

Dans les versions debug, un ATLASSERT ; sera déclenchée si existant `CAtlArray` objet n’est pas valide, ou si *aSrc* fait référence au même objet. Arguments non valides dans les versions release, peuvent entraîner un comportement imprévisible.

> [!NOTE]
> `CAtlArray::Copy` ne prend pas en charge les tableaux comprenant des éléments créés avec le [CAutoPtr](../../atl/reference/cautoptr-class.md) classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

Appelez cette méthode pour supprimer tous les éléments vides du tableau.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Notes

Tous les éléments vides sont supprimés, mais la taille et la limite supérieure du tableau restent inchangés.

Dans les versions debug, un ATLASSERT ; sera déclenchée si l’objet CAtlArray n’est pas valide, ou si le tableau dépasse sa taille maximale.

##  <a name="getat"></a>  CAtlArray::GetAt

Appel de que cette méthode récupère un élément unique à partir de l’objet de tableau.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
La valeur d’index de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Dans les versions debug, un ATLASSERT ; sera déclenchée si *iElement* dépasse le nombre d’éléments dans le tableau. Un argument non valide dans les versions release, peut entraîner un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments stockés dans le tableau.

### <a name="remarks"></a>Notes

Comme le premier élément du tableau est à la position 0, la valeur retournée par `GetCount` est toujours 1 supérieur le plus grand index.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlArray::GetAt](#getat).

##  <a name="getdata"></a>  CAtlArray::GetData

Appelez cette méthode pour retourner un pointeur vers le premier élément du tableau.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers l’emplacement de mémoire stockant le premier élément du tableau. Si aucun élément n’est disponible, la valeur NULL est retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

Le type de données à utiliser pour l’ajout d’éléments dans le tableau.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

Appelez cette méthode pour insérer un tableau dans un autre.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Paramètres

*iStart*<br/>
Index auquel le tableau doit être inséré.

*paNew*<br/>
Le tableau doit être inséré.

### <a name="remarks"></a>Notes

Éléments à partir du tableau *paNew* sont copiés dans l’objet de tableau, en commençant à l’élément *iStart*. Les éléments du tableau sont déplacés pour éviter l’écrasement.

Dans les versions debug, un ATLASSERT ; sera déclenchée si le `CAtlArray` objet n’est pas valide, ou si le *paNew* pointeur est NULL ou non valide.

> [!NOTE]
> `CAtlArray::InsertArrayAt` ne prend pas en charge les tableaux comprenant des éléments créés avec le [CAutoPtr](../../atl/reference/cautoptr-class.md) classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet de tableau.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index où l’ou les éléments doivent être insérés.

*element*<br/>
La valeur de l’élément ou les éléments à insérer.

*nCount*<br/>
Le nombre d’éléments à ajouter.

### <a name="remarks"></a>Notes

Insère un ou plusieurs éléments dans le tableau, en commençant à l’index *iElement*. Éléments existants sont déplacés pour éviter l’écrasement.

Dans les versions debug, un ATLASSERT ; sera déclenchée si le `CAtlArray` objet n’est pas valide, le nombre d’éléments à ajouter est égal à zéro, ou le nombre d’éléments est trop grand pour le tableau destiné à contenir. Dans les versions commerciales, le passage de paramètres non valides peut provoquer des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

Appelez cette méthode pour tester si le tableau est vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le tableau est vide, sinon false.

### <a name="remarks"></a>Notes

Le tableau est dite vide s’il ne contienne aucun élément. Par conséquent, même si le tableau contient des éléments vides, il n’est pas vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  CAtlArray::operator []

Appeler cet opérateur pour retourner une référence à un élément dans le tableau.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
La valeur d’index de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Exécute une fonction similaire à [CAtlArray::GetAt](#getat). Contrairement à la classe MFC [CArray](../../mfc/reference/carray-class.md), cet opérateur ne peut pas être utilisé pour remplacer [CAtlArray::SetAt](#setat).

Dans les versions debug, un ATLASSERT ; sera déclenchée si *iElement* dépasse le nombre total d’éléments dans le tableau. Dans les versions commerciales, un paramètre non valide peut provoquer des résultats imprévisibles.

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments à partir du tableau.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

Appelez cette méthode pour supprimer tous les éléments de l’objet de tableau.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de l’objet de tableau.

Cette méthode appelle [CAtlArray::SetCount](#setcount) pour redimensionner le tableau et par la suite libère la mémoire allouée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlArray::IsEmpty](#isempty).

##  <a name="removeat"></a>  CAtlArray::RemoveAt

Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
L’index du premier élément à supprimer.

*nCount*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Supprime un ou plusieurs éléments du tableau. Les éléments restants sont décalés vers le bas. La limite supérieure est décrémentée, mais la mémoire n’est pas libérée tant qu’un appel à [CAtlArray::FreeExtra](#freeextra) est effectuée.

Dans les versions debug, un ATLASSERT ; sera déclenchée si le `CAtlArray` objet n’est pas valide, ou si le total combiné de *iElement* et *nCount* dépasse le nombre total d’éléments dans le tableau. Dans les versions commerciales, les paramètres non valides peuvent provoquer des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

Appelez cette méthode pour définir la valeur d’un élément dans l’objet tableau.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
L’index qui pointe vers l’élément de tableau à définir.

*element*<br/>
La nouvelle valeur de l’élément spécifié.

### <a name="remarks"></a>Notes

Dans les versions debug, un ATLASSERT ; sera déclenchée si *iElement* dépasse le nombre d’éléments dans le tableau. Dans les versions commerciales, un paramètre non valide peut entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlArray::GetAt](#getat).

##  <a name="setcount"></a>  CAtlArray::SetCount

Appelez cette méthode pour définir la taille de l’objet de tableau.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Paramètres

*nNewSize*<br/>
La taille requise du tableau.

*nGrowBy*<br/>
Une valeur utilisée pour déterminer la taille de la mémoire tampon. La valeur -1 entraîne une valeur calculée en interne à utiliser.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le tableau est redimensionné avec succès, false sinon.

### <a name="remarks"></a>Notes

Le tableau vous pouvez augmenter ou réduire la taille. Si augmentée, éléments vides supplémentaires sont ajoutés au tableau. Si diminue, les éléments à l’aide plus grands index seront supprimés et la mémoire libérée.

Utilisez cette méthode pour définir la taille du tableau avant de l’utiliser. Si `SetCount` n’est pas utilisé, le processus d’ajout d’éléments, et l’allocation de mémoire suivantes effectuées, réduira les performances et fragmenter la mémoire.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlArray::GetData](#getdata).

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en développant le tableau en fonction des besoins.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
L’index qui pointe vers l’élément de tableau à définir.

*element*<br/>
La nouvelle valeur de l’élément spécifié.

### <a name="remarks"></a>Notes

Remplace la valeur de l’élément vers lequel pointé l’index. Si *iElement* est supérieure à la taille actuelle du tableau, le tableau est automatiquement augmenté à l’aide d’un appel à [CAtlArray::SetCount](#setcount). Dans les versions debug, un ATLASSERT ; sera déclenchée si le `CAtlArray` objet n’est pas valide. Dans les versions commerciales, les paramètres non valides peuvent provoquer des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[MMXSwarm, exemple](../../overview/visual-cpp-samples.md)<br/>
[Exemple DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[CArray, classe](../../mfc/reference/carray-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
