---
description: 'En savoir plus sur : CArray (classe)'
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
ms.openlocfilehash: 2aea88178347fd146720a8205974049e4baf039f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259641"
---
# <a name="carray-class"></a>CArray (classe)

Prend en charge des tableaux similaires aux tableaux C, mais peut réduire et augmenter dynamiquement en fonction des besoins.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des objets stockés dans le tableau. Le *type* est un paramètre qui est retourné par `CArray` .

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’argument utilisé pour accéder aux objets stockés dans le tableau. Souvent une référence au *type*. *Arg_type* est un paramètre qui est passé à `CArray` .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArray :: CArray](#carray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CArray :: Add](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CArray :: Append](#append)|Ajoute un autre tableau au tableau ; augmente le tableau si nécessaire|
|[CArray :: Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CArray :: ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CArray :: FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CArray :: GetAt](#getat)|Retourne la valeur à un index donné.|
|[CArray :: GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CArray :: GetData](#getdata)|Autorise l'accès aux éléments du tableau. Sa valeur peut être NULL.|
|[CArray :: Deis](#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CArray :: GetUpperBound](#getupperbound)|Retourne le plus grand index valide.|
|[CArray :: InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CArray :: IsEmpty](#isempty)|Détermine si le tableau est vide.|
|[CArray :: RemoveAll](#removeall)|Supprime tous les éléments de ce tableau.|
|[CArray :: RemoveAt](#removeat)|Supprime un élément à un index spécifique.|
|[CArray :: SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CArray :: SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CArray :: assets](#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Les index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut corriger la limite supérieure ou activer le tableau pour développer lorsque vous ajoutez des éléments au-delà de la limite actuelle. La mémoire est allouée de façon contiguë à la limite supérieure, même si certains éléments ont la valeur null.

> [!NOTE]
> La plupart des méthodes qui redimensionnent un `CArray` objet ou y ajoutent des éléments qui utilisent [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) pour déplacer des éléments. Il s’agit d’un problème, car `memcpy_s` n’est pas compatible avec les objets qui nécessitent l’appel du constructeur. Si les éléments de `CArray` ne sont pas compatibles avec `memcpy_s` , vous devez créer un nouveau `CArray` de la taille appropriée. Vous devez ensuite utiliser [CArray :: Copy](#copy) et [CArray :: setat](#setat) pour remplir le nouveau tableau, car ces méthodes utilisent un opérateur d’assignation au lieu de `memcpy_s` .

Comme avec un tableau C, le temps d’accès d’un `CArray` élément indexé est constant et indépendant de la taille du tableau.

> [!TIP]
> Avant d’utiliser un tableau, utilisez l’opération de [configuration](#setsize) pour définir sa taille et lui allouer de la mémoire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin d’un vidage d’éléments individuels dans un tableau, vous devez définir la profondeur de l’objet [CDumpContext](../../mfc/reference/cdumpcontext-class.md) à une valeur supérieure ou égale à 1.

Certaines fonctions membres de cette classe appellent des fonctions d’assistance globales qui doivent être personnalisées pour la plupart des utilisations de la `CArray` classe. Consultez les rubriques [d’aide](../../mfc/reference/collection-class-helpers.md) sur les classes de collection de la rubrique dans la section macros et globales MFC.

La dérivation de classe de tableau est semblable à la dérivation de liste.

Pour plus d’informations sur l’utilisation de `CArray` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a> CArray :: Add

Ajoute un nouvel élément à la fin d’un tableau, en augmentant le tableau de 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’arguments référençant des éléments dans ce tableau.

*newElement*<br/>
Élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur renvoyée

Index de l’élément ajouté.

### <a name="remarks"></a>Notes

Si l’opération de [configuration](#setsize) a été utilisée avec une `nGrowBy` valeur supérieure à 1, une mémoire supplémentaire peut être allouée. Toutefois, la limite supérieure n’augmente que de 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a> CArray :: Append

Appelez cette fonction membre pour ajouter le contenu d’un tableau à la fin d’un autre.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à ajouter à un tableau.

### <a name="return-value"></a>Valeur renvoyée

Index du premier élément ajouté.

### <a name="remarks"></a>Notes

Les tableaux doivent être du même type.

Si nécessaire, `Append` peut allouer de la mémoire supplémentaire pour prendre en charge les éléments ajoutés au tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a> CArray :: CArray

Construit un tableau vide.

```
CArray();
```

### <a name="remarks"></a>Notes

Le tableau augmente un élément à la fois.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a> CArray :: Copy

Utilisez cette fonction membre pour copier les éléments d’un tableau dans un autre.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à copier dans un tableau.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour remplacer les éléments d’un tableau par les éléments d’un autre tableau.

`Copy` ne libère pas la mémoire ; Toutefois, si nécessaire, `Copy` peut allouer de la mémoire supplémentaire pour prendre en charge les éléments copiés dans le tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a> CArray :: ElementAt

Retourne une référence temporaire à l’élément spécifié dans le tableau.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur renvoyée

Référence à un élément de tableau.

### <a name="remarks"></a>Notes

Il est utilisé pour implémenter l’opérateur d’assignation côté gauche pour les tableaux.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à la [propriété](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a> CArray :: FreeExtra

Libère toute mémoire supplémentaire allouée lors de la croissance du tableau.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [GetData](#getdata).

## <a name="carraygetat"></a><a name="getat"></a> CArray :: GetAt

Retourne l’élément de tableau à l’index spécifié.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments du tableau.

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur renvoyée

Élément de tableau actuellement à cet index.

### <a name="remarks"></a>Notes

Le passage d’une valeur négative ou d’une valeur supérieure à la valeur retournée par `GetUpperBound` entraîne une assertion ayant échoué.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a> CArray :: GetCount

Retourne le nombre d’éléments du tableau.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans le tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les index sont de base zéro, la taille est égale à 1 par rapport à l’index le plus grand. L’appel de cette méthode génère le même résultat que la méthode [CArray ::](#getsize) DETENTE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a> CArray :: GetData

Utilisez cette fonction membre pour obtenir un accès direct aux éléments d’un tableau.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments du tableau.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un élément de tableau.

### <a name="remarks"></a>Notes

Si aucun élément n’est disponible, `GetData` retourne une valeur null.

Bien que l’accès direct aux éléments d’un tableau puisse vous aider à travailler plus rapidement, soyez prudent lors de l’appel de `GetData` ; toutes les erreurs que vous apportez affectent directement les éléments de votre tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a> CArray :: Deis

Retourne la taille du tableau.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Notes

Étant donné que les index sont de base zéro, la taille est égale à 1 par rapport à l’index le plus grand. L’appel de cette méthode génère le même résultat que la méthode [CArray :: GetCount](#getcount) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a> CArray :: GetUpperBound

Retourne la limite supérieure actuelle de ce tableau.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Notes

Étant donné que les index de tableau sont de base zéro, cette fonction retourne une valeur 1 inférieure à `GetSize` .

La condition `GetUpperBound( )` =-1 indique que le tableau ne contient pas d’éléments.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CArray :: GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a> CArray :: InsertAt

La première version de `InsertAt` insère un élément (ou plusieurs copies d’un élément) à un index spécifié dans un tableau.

```cpp
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
Index entier qui peut être supérieur à la valeur retournée par `GetUpperBound` .

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de ce tableau.

*newElement*<br/>
Élément à placer dans ce tableau.

*nCount*<br/>
Nombre de fois où cet élément doit être inséré (1 par défaut).

*nStartIndex*<br/>
Index entier qui peut être supérieur à la valeur retournée par [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Autre tableau qui contient les éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Dans le processus, il est déplacé vers le haut (en incrémentant l’index) de l’élément existant à cet index, et il décale tous les éléments situés au-dessus de celui-ci.

La deuxième version insère tous les éléments d’une autre `CArray` collection, en commençant à la position *nStartIndex* .

`SetAt`En revanche, la fonction remplace un élément de tableau spécifié et ne décale aucun élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a> CArray :: IsEmpty

Détermine si le tableau est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le tableau ne contient pas d’éléments ; Sinon, 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a> CArray :: Operator \[\]

Ces opérateurs d’indice sont un substitut pratique pour les fonctions [setat](#setat) et [GetAt](#getat) .

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type des éléments de ce tableau.

*nIndex*<br/>
Index de l’élément auquel accéder.

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour les tableaux qui ne sont pas **`const`** , peut être utilisé soit sur le droit (r-value), soit sur la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour les **`const`** tableaux, peut être utilisée uniquement à droite.

La version de débogage de la bibliothèque déclare si l’indice (à gauche ou à droite d’une instruction d’assignation) est hors limites.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a> CArray :: RelocateElements

Déplace les données vers une nouvelle mémoire tampon lorsque le tableau doit croître ou diminuer.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*pNewData*<br/>
Nouvelle mémoire tampon pour le tableau d’éléments.

*pData*<br/>
Ancien tableau d’éléments.

*nCount*<br/>
Nombre d’éléments dans l’ancien tableau.

### <a name="remarks"></a>Notes

*pNewData* est toujours assez grand pour contenir tous les éléments *pData* .

L’implémentation de [CArray](../../mfc/reference/carray-class.md) utilise cette méthode pour copier les anciennes données dans une nouvelle mémoire tampon lorsque le tableau doit augmenter ou diminuer (lorsque la méthode [deinstalle](#setsize) ou [FreeExtra](#freeextra) est appelée). L’implémentation par défaut copie simplement les données.

Pour les tableaux dans lesquels un élément contient un pointeur vers l’un de ses propres membres, ou une autre structure contient un pointeur vers l’un des éléments du tableau, les pointeurs ne sont pas mis à jour en copie simple. Dans ce cas, vous pouvez corriger les pointeurs en implémentant une spécialisation de `RelocateElements` avec les types appropriés. Vous êtes également responsable de la copie des données.

## <a name="carrayremoveall"></a><a name="removeall"></a> CArray :: RemoveAll

Supprime tous les éléments de ce tableau.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Si le tableau est déjà vide, la fonction fonctionne toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a> CArray :: RemoveAt

Supprime un ou plusieurs éléments commençant à un index spécifié dans un tableau.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

*nCount*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Dans le processus, il décale tous les éléments au-dessus du ou des éléments supprimés. Elle décrémente la limite supérieure du tableau, mais ne libère pas la mémoire.

Si vous essayez de supprimer plus d’éléments que ceux contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque Assert.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a> CArray :: SetAt

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’arguments utilisé pour référencer des éléments de tableau.

*newElement*<br/>
Nouvelle valeur de l’élément à stocker à la position spécifiée.

### <a name="remarks"></a>Notes

`SetAt` n’entraîne pas la croissance du tableau. Utilisez [SetAtGrow](#setatgrow) si vous souhaitez que le tableau augmente automatiquement.

Vous devez vous assurer que votre valeur d’index représente une position valide dans le tableau. S’il est hors limites, la version de débogage de la bibliothèque Assert.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a> CArray :: SetAtGrow

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier supérieur ou égal à 0.

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’éléments dans le tableau.

*newElement*<br/>
Élément à ajouter à ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Le tableau s’agrandit automatiquement si nécessaire (autrement dit, la limite supérieure est ajustée pour s’adapter au nouvel élément).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a> CArray :: assets

Établit la taille d’un tableau vide ou existant ; alloue de la mémoire si nécessaire.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Paramètres

*nNewSize*<br/>
Nouvelle taille de tableau (nombre d’éléments). Doit être supérieur ou égal à 0.

*nGrowBy*<br/>
Nombre minimal d’emplacements d’éléments à allouer si une augmentation de la taille est nécessaire.

### <a name="remarks"></a>Notes

Si la nouvelle taille est inférieure à l’ancienne taille, le tableau est tronqué et toute la mémoire inutilisée est libérée.

Utilisez cette fonction pour définir la taille de votre tableau avant de commencer à utiliser le tableau. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Le paramètre *nGrowBy* affecte l’allocation de mémoire interne pendant la croissance du tableau. Son utilisation n’affecte jamais la taille du tableau comme [indiqué par](#getsize) Desize et [GetUpperBound](#getupperbound). Si la valeur par défaut est utilisée, les MFC allouent de la mémoire de façon à éviter la fragmentation de la mémoire et optimisent l’efficacité dans la plupart des cas.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [GetData](#getdata).

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)<br/>
[Classe d’assistance des classes de collection](../../mfc/reference/collection-class-helpers.md)
