---
title: CPtrArray, classe
ms.date: 11/04/2016
f1_keywords:
- CPtrArray
- AFXCOLL/CPtrArray
- AFXCOLL/CPtrArray::CPtrArray
- AFXCOLL/CPtrArray::Add
- AFXCOLL/CPtrArray::Append
- AFXCOLL/CPtrArray::Copy
- AFXCOLL/CPtrArray::ElementAt
- AFXCOLL/CPtrArray::FreeExtra
- AFXCOLL/CPtrArray::GetAt
- AFXCOLL/CPtrArray::GetCount
- AFXCOLL/CPtrArray::GetData
- AFXCOLL/CPtrArray::GetSize
- AFXCOLL/CPtrArray::GetUpperBound
- AFXCOLL/CPtrArray::InsertAt
- AFXCOLL/CPtrArray::IsEmpty
- AFXCOLL/CPtrArray::RemoveAll
- AFXCOLL/CPtrArray::RemoveAt
- AFXCOLL/CPtrArray::SetAt
- AFXCOLL/CPtrArray::SetAtGrow
- AFXCOLL/CPtrArray::SetSize
helpviewer_keywords:
- CPtrArray [MFC], CPtrArray
- CPtrArray [MFC], Add
- CPtrArray [MFC], Append
- CPtrArray [MFC], Copy
- CPtrArray [MFC], ElementAt
- CPtrArray [MFC], FreeExtra
- CPtrArray [MFC], GetAt
- CPtrArray [MFC], GetCount
- CPtrArray [MFC], GetData
- CPtrArray [MFC], GetSize
- CPtrArray [MFC], GetUpperBound
- CPtrArray [MFC], InsertAt
- CPtrArray [MFC], IsEmpty
- CPtrArray [MFC], RemoveAll
- CPtrArray [MFC], RemoveAt
- CPtrArray [MFC], SetAt
- CPtrArray [MFC], SetAtGrow
- CPtrArray [MFC], SetSize
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
ms.openlocfilehash: 5db9f69348e96fffc1aa6fdc88134d777eb5406d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226852"
---
# <a name="cptrarray-class"></a>CPtrArray, classe

Prend en charge des tableaux de pointeurs void.

## <a name="syntax"></a>Syntaxe

```
class CPtrArray : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CPtrArray` sont similaires aux fonctions membres de la classe [CObArray](../../mfc/reference/cobarray-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObArray` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur sous la forme d’un paramètre de fonction ou d’une valeur de retour, remplacez un pointeur par **`void`** .

`CObject* CObArray::GetAt( int <nIndex> ) const;`

par exemple, se traduit par

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPtrArray::CPtrArray](../../mfc/reference/cobarray-class.md#cobarray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPtrArray :: Add](../../mfc/reference/cobarray-class.md#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CPtrArray :: Append](../../mfc/reference/cobarray-class.md#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CPtrArray :: Copy](../../mfc/reference/cobarray-class.md#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CPtrArray :: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CPtrArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CPtrArray :: GetAt](../../mfc/reference/cobarray-class.md#getat)|Retourne la valeur à un index donné.|
|[CPtrArray :: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CPtrArray :: GetData](../../mfc/reference/cobarray-class.md#getdata)|Autorise l'accès aux éléments du tableau. Peut être `NULL`.|
|[CPtrArray :: est à obtenir](../../mfc/reference/cobarray-class.md#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CPtrArray :: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Retourne le plus grand index valide.|
|[CPtrArray :: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CPtrArray :: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Détermine si le tableau est vide.|
|[CPtrArray :: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Supprime tous les éléments de ce tableau.|
|[CPtrArray :: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Supprime un élément à un index spécifique.|
|[CPtrArray :: SetAt](../../mfc/reference/cobarray-class.md#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CPtrArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CPtrArray :: configure](../../mfc/reference/cobarray-class.md#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPtrArray ::, opérateur \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

`CPtrArray`incorpore la macro IMPLEMENT_DYNAMIC pour prendre en charge l’accès aux types au moment de l’exécution et le vidage sur un `CDumpContext` objet. Si vous avez besoin d’un vidage d’éléments individuels de tableau de pointeurs, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

> [!NOTE]
> Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Les tableaux de pointeurs ne peuvent pas être sérialisés.

Lorsqu’un tableau de pointeurs est supprimé ou que ses éléments sont supprimés, seuls les pointeurs sont supprimés, et non les entités auxquelles ils font référence.

Pour plus d’informations sur l’utilisation de `CPtrArray` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
