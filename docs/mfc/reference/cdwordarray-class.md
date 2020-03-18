---
title: CDWordArray, classe
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: f17caafd01bb5ddfa49afe378bfd79652149ebd8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447353"
---
# <a name="cdwordarray-class"></a>CDWordArray, classe

Prend en charge les tableaux de mots doubles de 32 bits.

## <a name="syntax"></a>Syntaxe

```
class CDWordArray : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CDWordArray` sont similaires aux fonctions membres de la classe [CObArray](../../mfc/reference/cobarray-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObArray` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un pointeur de `CObject` sous la forme d’un paramètre de fonction ou d’une valeur de retour, substituez une `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

par exemple, se traduit par

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDWordArray::CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDWordArray :: Add](../../mfc/reference/cobarray-class.md#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CDWordArray :: Append](../../mfc/reference/cobarray-class.md#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CDWordArray :: Copy](../../mfc/reference/cobarray-class.md#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CDWordArray :: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Retourne une référence temporaire à l’octet dans le tableau.|
|[CDWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CDWordArray :: GetAt](../../mfc/reference/cobarray-class.md#getat)|Retourne la valeur à un index donné.|
|[CDWordArray :: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CDWordArray :: GetData](../../mfc/reference/cobarray-class.md#getdata)|Autorise l'accès aux éléments du tableau. Sa valeur peut être NULL.|
|[CDWordArray :: est à obtenir](../../mfc/reference/cobarray-class.md#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CDWordArray :: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Retourne le plus grand index valide.|
|[CDWordArray :: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CDWordArray :: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Détermine si le tableau est vide.|
|[CDWordArray :: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Supprime tous les éléments de ce tableau.|
|[CDWordArray :: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Supprime un élément à un index spécifique.|
|[CDWordArray :: SetAt](../../mfc/reference/cobarray-class.md#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CDWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CDWordArray :: configure](../../mfc/reference/cobarray-class.md#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[CDWordArray :: Operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

`CDWordArray` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de mots doubles est stocké dans une archive, avec l’opérateur d’insertion surchargé ( **<<** ) ou avec la fonction membre `Serialize`, chaque élément est, à son tour, sérialisé.

> [!NOTE]
>  Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin de la sortie de débogage d’éléments individuels dans le tableau, vous devez définir la profondeur de l’objet `CDumpContext` à une valeur supérieure ou égale à 1.

Pour plus d’informations sur l’utilisation de `CDWordArray`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObArray, classe](../../mfc/reference/cobarray-class.md)
