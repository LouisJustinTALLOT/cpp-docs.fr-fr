---
title: Classe CArray
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
ms.openlocfilehash: 3355e72c58365e97f8f3f8ce09754285f671915a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753979"
---
# <a name="carray-class"></a>Classe CArray

Soutient les tableaux qui sont comme les tableaux C, mais qui peuvent réduire et croître dynamiquement au besoin.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle qui spécifie le type d’objets stockés dans le tableau. *TYPE* est un paramètre `CArray`qui est retourné par .

*ARG_TYPE*<br/>
Paramètre de modèle qui spécifie le type d’argument qui est utilisé pour accéder aux objets stockés dans le tableau. Souvent une référence à *TYPE*. *ARG_TYPE* est un paramètre qui `CArray`est transmis à .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArray::CArray](#carray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CArray::Ajouter](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CArray::Append](#append)|Annexe un autre tableau à la gamme; développe le tableau si nécessaire|
|[CArray::Copier](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CArray::FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CArray::GetAt](#getat)|Retourne la valeur à un index donné.|
|[CArray::GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CArray::GetData](#getdata)|Autorise l'accès aux éléments du tableau. Sa valeur peut être NULL.|
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

Les index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut fixer la limite supérieure ou permettre au réseau de se développer lorsque vous ajoutez des éléments au-delà de la limite actuelle. La mémoire est attribuée de façon contigu à la limite supérieure, même si certains éléments sont nuls.

> [!NOTE]
> La plupart des méthodes `CArray` qui resize un objet ou y ajouter des éléments utilisent [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) pour déplacer les éléments. Il s’agit `memcpy_s` d’un problème parce qu’il n’est pas compatible avec les objets qui nécessitent l’appel du constructeur. Si les éléments `CArray` de la `memcpy_s`n’est pas `CArray` compatible avec, vous devez créer un nouveau de la taille appropriée. Vous devez ensuite utiliser [CArray::Copy](#copy) et [CArray::SetAt](#setat) pour remplir le nouveau `memcpy_s`tableau parce que ces méthodes utilisent un opérateur d’affectation au lieu de .

Comme avec un tableau C, `CArray` le temps d’accès pour un élément indexé est constant et indépendant de la taille du tableau.

> [!TIP]
> Avant d’utiliser un tableau, utilisez [SetSize](#setsize) pour établir sa taille et allouer la mémoire pour elle. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin d’un dépotoir d’éléments individuels dans un tableau, vous devez définir la profondeur de l’objet [CDumpContext](../../mfc/reference/cdumpcontext-class.md) à 1 ou plus.

Certaines fonctions membres de cette classe appellent fonctions d’aide globale `CArray` qui doivent être personnalisées pour la plupart des utilisations de la classe. Voir le sujet [Collection Class Helpers](../../mfc/reference/collection-class-helpers.md) dans la section Macros et Globals MFC.

La dérivation de classe de tableau est comme la dérivation de liste.

Pour plus d’informations `CArray`sur la façon d’utiliser , voir l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::Ajouter

Ajoute un nouvel élément à la fin d’un tableau, augmentant le tableau de 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’arguments faisant référence aux éléments de ce tableau.

*nouvel Element*<br/>
L’élément à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Si [SetSize](#setsize) a été `nGrowBy` utilisé avec une valeur supérieure à 1, alors la mémoire supplémentaire peut être allouée. Cependant, la limite supérieure n’augmentera que de 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::Append

Appelez cette fonction de membre pour ajouter le contenu d’un tableau à la fin d’un autre.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à annexer à un tableau.

### <a name="return-value"></a>Valeur de retour

L’index du premier élément joint.

### <a name="remarks"></a>Notes

Les tableaux doivent être du même type.

Si nécessaire, `Append` peut allouer une mémoire supplémentaire pour accueillir les éléments annexés au tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray::CArray

Construit un tableau vide.

```
CArray();
```

### <a name="remarks"></a>Notes

Le tableau pousse un élément à la fois.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::Copier

Utilisez cette fonction de membre pour copier les éléments d’un tableau à un autre.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à copier à un tableau.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour remplacer les éléments d’un tableau avec les éléments d’un autre tableau.

`Copy`ne libère pas la mémoire; toutefois, si `Copy` nécessaire, peut allouer une mémoire supplémentaire pour tenir compte des éléments copiés sur le tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray::ElementAt

Renvoie une référence temporaire à l’élément spécifié dans le tableau.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur de retour

Une référence à un élément de tableau.

### <a name="remarks"></a>Notes

Il est utilisé pour implémenter l’opérateur d’affectation côté gauche pour les tableaux.

### <a name="example"></a>Exemple

  Voir l’exemple pour [GetSize](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra

Libère toute mémoire supplémentaire qui a été allouée pendant que le tableau a été cultivé.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.

### <a name="example"></a>Exemple

  Voir l’exemple pour [GetData](#getdata).

## <a name="carraygetat"></a><a name="getat"></a>CArray::GetAt

Retourne l’élément de tableau à l’index spécifié.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type des éléments de tableau.

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valeur de retour

L’élément de tableau actuellement à cet index.

### <a name="remarks"></a>Notes

L’adoption d’une valeur négative ou `GetUpperBound` d’une valeur supérieure à la valeur retournée entraînera un échec de l’affirmation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray::GetCount

Retourne le nombre d’éléments de tableau.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les indices sont basés à zéro, la taille est 1 supérieure à l’indice le plus important. L’appel de cette méthode générera le même résultat que la méthode [CArray::GetSize.](#getsize)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray::GetData

Utilisez cette fonction de membre pour accéder directement aux éléments d’un tableau.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type des éléments de tableau.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un élément de tableau.

### <a name="remarks"></a>Notes

Si aucun élément `GetData` n’est disponible, renvoie une valeur nulle.

Bien que l’accès direct aux éléments d’un tableau `GetData`peut vous aider à travailler plus rapidement, faites preuve de prudence lorsque vous appelez; toutes les erreurs que vous faites affectent directement les éléments de votre tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray::GetSize

Retourne la taille du tableau.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Notes

Étant donné que les indices sont basés à zéro, la taille est 1 supérieure à l’indice le plus important. L’appel de cette méthode générera le même résultat que la méthode [CArray::GetCount.](#getcount)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound

Retourne la limite supérieure actuelle de ce tableau.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Notes

Étant donné que les indices de tableau sont basés à `GetSize`zéro, cette fonction retourne une valeur 1 de moins que .

La `GetUpperBound( )` condition de -1 indique que le tableau ne contient aucun élément.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArray:GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray::InsertAt

La première `InsertAt` version des inserts d’un élément (ou de multiples copies d’un élément) à un index spécifié dans un tableau.

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
Un indice d’intégration qui peut `GetUpperBound`être supérieur à la valeur retournée par .

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de ce tableau.

*nouvel Element*<br/>
L’élément à placer dans ce tableau.

*nCompte*<br/>
Le nombre de fois cet élément doit être inséré (par défaut à 1).

*nStartIndex*<br/>
Un indice d’intégration qui peut être supérieur à la valeur retournée par [GetUpperBound](#getupperbound).

*pNewArray (en)*<br/>
Un autre tableau qui contient des éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

Dans le processus, il déplace vers le haut (en incrémentant l’indice) l’élément existant à cet indice, et il déplace vers le haut tous les éléments au-dessus.

La deuxième version insère `CArray` tous les éléments d’une autre collection, à partir de la position *nStartIndex.*

La `SetAt` fonction, en revanche, remplace un élément de tableau spécifié et ne déplace aucun élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray::IsEmpty

Détermine si le tableau est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le tableau ne contient pas d’éléments; sinon 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::opérateur\[\]

Ces opérateurs de sous-scripte remplacent les fonctions [SetAt](#setat) et [GetAt.](#getat)

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments de ce tableau.

*nIndex*<br/>
Index de l’élément à accéder.

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour des tableaux qui ne sont pas **const**, peut être utilisé soit sur la droite (r-valeur) ou la gauche (l-valeur) d’une déclaration d’affectation. Le second, appelé pour les tableaux **de cônes,** ne peut être utilisé que sur la droite.

La version Debug de la bibliothèque affirme si le sous-scriptum (soit sur le côté gauche ou à droite d’une déclaration d’affectation) est hors limites.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::RelocateElements

Déplace les données dans un nouveau tampon lorsque le tableau devrait croître ou rétrécir.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Paramètres

*pNewData (en)*<br/>
Un nouveau tampon pour la gamme d’éléments.

*Pdata*<br/>
L’ancien tableau d’éléments.

*nCompte*<br/>
Nombre d’éléments dans l’ancien tableau.

### <a name="remarks"></a>Notes

*pNewData* est toujours assez grand pour contenir tous les éléments *de pData.*

La mise en œuvre [de CArray](../../mfc/reference/carray-class.md) utilise cette méthode pour copier les anciennes données à un nouveau tampon lorsque le tableau doit croître ou rétrécir (lorsque [SetSize](#setsize) ou [FreeExtra](#freeextra) sont appelés). La implémentation par défaut ne fait que copier les données.

Pour les tableaux dans lesquels un élément contient un pointeur à l’un de ses propres membres, ou une autre structure contient un pointeur à l’un des éléments de tableau, les pointeurs ne sont pas mis à jour en copie simple. Dans ce cas, vous pouvez corriger les points `RelocateElements` en mettant en œuvre une spécialisation avec les types pertinents. Vous êtes également responsable de la copie de données.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray::RemoveAll

Supprime tous les éléments de ce tableau.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Si le tableau est déjà vide, la fonction fonctionne toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray::RemoveAt

Supprime un ou plusieurs éléments à partir d’un index spécifié dans un tableau.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

*nCompte*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Dans le processus, il déplace vers le bas tous les éléments au-dessus de l’élément supprimé.s). Il décrément la limite supérieure du tableau mais ne libère pas la mémoire.

Si vous essayez d’enlever plus d’éléments que ceux contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque affirme.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray::SetAt

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’arguments utilisés pour le référencement des éléments de tableau.

*nouvel Element*<br/>
La nouvelle valeur d’élément à stocker à la position spécifiée.

### <a name="remarks"></a>Notes

`SetAt`ne fera pas croître le tableau. Utilisez [SetAtGrow](#setatgrow) si vous voulez que le tableau se développe automatiquement.

Vous devez vous assurer que votre valeur indicative représente une position valide dans le tableau. S’il est hors limites, alors la version Debug de la bibliothèque affirme.

### <a name="example"></a>Exemple

  Voir l’exemple pour [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray::SetAtGrow

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0.

*ARG_TYPE*<br/>
Paramètre de modèle spécifiant le type d’éléments dans le tableau.

*nouvel Element*<br/>
L’élément à ajouter à ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Le tableau se développe automatiquement si nécessaire (c’est-à-dire que la limite supérieure est ajustée pour accueillir le nouvel élément).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::SetSize

Établit la taille d’un tableau vide ou existant; alloue la mémoire si nécessaire.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Paramètres

*nNewSize (en)*<br/>
La nouvelle taille du tableau (nombre d’éléments). Doit être supérieur ou égal à 0.

*nGrowBy (en)*<br/>
Le nombre minimum de fentes d’élément à allouer si une augmentation de taille est nécessaire.

### <a name="remarks"></a>Notes

Si la nouvelle taille est plus petite que l’ancienne taille, alors le tableau est tronqué et toute mémoire inutilisée est libérée.

Utilisez cette fonction pour définir la taille de votre tableau avant de commencer à utiliser le tableau. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Le *paramètre nGrowBy* affecte l’allocation de mémoire interne pendant que le tableau est en croissance. Son utilisation n’affecte jamais la taille du tableau tel que rapporté par [GetSize](#getsize) et [GetUpperBound](#getupperbound). Si la valeur par défaut est utilisée, MFC alloue la mémoire d’une manière calculée pour éviter la fragmentation de la mémoire et optimiser l’efficacité pour la plupart des cas.

### <a name="example"></a>Exemple

  Voir l’exemple pour [GetData](#getdata).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)<br/>
[Programmes d’assistance pour les classes de collection](../../mfc/reference/collection-class-helpers.md)
