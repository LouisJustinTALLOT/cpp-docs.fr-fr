---
title: Cdwordarray, classe
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: 8cc67e62d905710ba5d63bf93c7b8aa1bf50f69c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206123"
---
# <a name="cdwordarray-class"></a>Cdwordarray, classe

Prend en charge les tableaux de mots doubles de 32 bits.

## <a name="syntax"></a>Syntaxe

```
class CDWordArray : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CDWordArray` sont similaires aux fonctions membres de classe [CObArray](../../mfc/reference/cobarray-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObArray` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur en tant que paramètre de fonction ou valeur de retour, remplacez un `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

par exemple, se traduit par

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Retourne une référence temporaire à l’octet dans le tableau.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Retourne la valeur à un index donné.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Autorise l'accès aux éléments du tableau. Peut être NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Retourne le plus grand index valide.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Détermine si le tableau est vide.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Supprime tous les éléments de ce tableau.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Supprime un élément à un index spécifique.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

`CDWordArray` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de mots doubles est stocké dans une archive, soit avec l’insertion surchargée ( **<<**) opérateur ou avec le `Serialize` fonction membre, chaque élément est, à son tour, sérialisé.

> [!NOTE]
>  Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin de la sortie à partir des éléments individuels dans le tableau de débogage, vous devez définir la profondeur de la `CDumpContext` objet à 1 ou supérieur.

Pour plus d’informations sur l’utilisation de `CDWordArray`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll.h

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
