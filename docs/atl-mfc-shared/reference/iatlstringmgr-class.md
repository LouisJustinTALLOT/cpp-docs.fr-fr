---
title: IAtlStringMgr, classe
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: a617ba829999e9e5778bd7f0091cfb0d624dce71
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832007"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr, classe

Cette classe représente l’interface pour un `CStringT` Gestionnaire de mémoire.

## <a name="syntax"></a>Syntaxe

```
__interface IAtlStringMgr
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[Lui](#allocate)|Appelez cette méthode pour allouer une nouvelle structure de données de type chaîne.|
|[Clone](#clone)|Appelez cette méthode pour retourner un pointeur vers un nouveau gestionnaire de chaînes à utiliser avec une autre instance de `CSimpleStringT` .|
|[Gratuit](#free)|Appelez cette méthode pour libérer une structure de données de chaîne.|
|[GetNilString](#getnilstring)|Retourne un pointeur vers l' `CStringData` objet utilisé par les objets de chaîne vides.|
|[Réallouer](#reallocate)|Appelez cette méthode pour réallouer une structure de données de chaîne.|

## <a name="remarks"></a>Notes

Cette interface gère la mémoire utilisée par les classes de chaînes indépendantes des MFC. tels que [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)et [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Vous pouvez également utiliser cette classe pour implémenter un gestionnaire de mémoire personnalisé pour votre classe de chaîne personnalisée. Pour plus d’informations, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpstr. h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a> IAtlStringMgr :: Allocate

Alloue une nouvelle structure de données de type chaîne.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Paramètres

*nAllocLength*<br/>
Nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize*<br/>
Taille (en octets) du type de caractère utilisé par le gestionnaire de chaînes.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

> [!NOTE]
> Ne signalez pas d’échec d’allocation en levant une exception. Au lieu de cela, une allocation ayant échoué doit être signalée en retournant la valeur NULL.

### <a name="remarks"></a>Notes

Appelez [IAtlStringMgr :: Free](#free) ou [IAtlStringMgr :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

> [!NOTE]
> Pour obtenir des exemples d’utilisation, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a> IAtlStringMgr :: Clone

Retourne un pointeur vers un nouveau gestionnaire de chaînes à utiliser avec une autre instance de `CSimpleStringT` .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une copie de l'objet `IAtlStringMgr`.

### <a name="remarks"></a>Notes

Communément appelé par le Framework lorsqu’un gestionnaire de chaînes est nécessaire pour une nouvelle chaîne. Dans la plupart des cas, le **`this`** pointeur est retourné.

Toutefois, si le gestionnaire de mémoire ne prend pas en charge l’utilisation de plusieurs instances de `CSimpleStringT` , un pointeur vers un gestionnaire de chaînes partageable doit être retourné.

> [!NOTE]
> Pour obtenir des exemples d’utilisation, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a> IAtlStringMgr :: Free

Libère une structure de données de type chaîne.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Pointeur vers le bloc de mémoire à libérer.

### <a name="remarks"></a>Notes

Libère le bloc de mémoire spécifié précédemment alloué par [allocate](#allocate) ou [Reallocation](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Pour obtenir des exemples d’utilisation, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a> IAtlStringMgr::GetNilString

Retourne un pointeur vers une structure de données de chaîne pour une chaîne vide.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `CStringData` objet utilisé pour représenter une chaîne vide.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner une représentation d’une chaîne vide.

> [!NOTE]
> Lors de l’implémentation d’un gestionnaire de chaînes personnalisé, cette fonction ne doit jamais échouer. Vous pouvez vous en assurer en incorporant une instance de `CNilStringData` dans la classe de gestionnaire de chaînes et en retournant un pointeur vers cette instance.

> [!NOTE]
> Pour obtenir des exemples d’utilisation, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a> IAtlStringMgr :: Reallocation

Réalloue une structure de données de type chaîne.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nAllocLength*<br/>
Nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize*<br/>
Taille (en octets) du type de caractère utilisé par le gestionnaire de chaînes.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez cette fonction pour redimensionner le bloc de mémoire existant spécifié par *pData*.

Appelez [IAtlStringMgr :: Free](#free) pour libérer la mémoire allouée par cette méthode.

> [!NOTE]
> Pour obtenir des exemples d’utilisation, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
