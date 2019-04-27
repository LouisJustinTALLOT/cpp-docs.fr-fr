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
ms.openlocfilehash: 978d33c719b9cb8c2708dc97fa78874534dfd748
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62199825"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr, classe

Cette classe représente l’interface pour un `CStringT` Gestionnaire de mémoire.

## <a name="syntax"></a>Syntaxe

```
__interface IAtlStringMgr
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[allouer](#allocate)|Appelez cette méthode pour allouer une nouvelle structure de données de chaîne.|
|[Clone](#clone)|Appelez cette méthode pour retourner un pointeur vers un nouveau gestionnaire de chaînes pour une utilisation avec une autre instance de `CSimpleStringT`.|
|[Gratuit](#free)|Appelez cette méthode pour libérer une structure de données de chaîne.|
|[GetNilString](#getnilstring)|Retourne un pointeur vers le `CStringData` objet utilisé par les objets de la chaîne vide.|
|[Reallocate](#reallocate)|Appelez cette méthode pour réallouer une structure de données de chaîne.|

## <a name="remarks"></a>Notes

Cette interface gère la mémoire utilisée par les classes de chaîne indépendant des MFC ; comme [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), et [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Vous pouvez également utiliser cette classe pour implémenter un gestionnaire de mémoire personnalisé pour votre classe de chaîne personnalisée. Pour plus d’informations, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpstr.h

##  <a name="allocate"></a>  IAtlStringMgr::Allocate

Alloue une nouvelle structure de données de chaîne.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Paramètres

*nAllocLength*<br/>
Le nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize*<br/>
La taille (en octets) du type de caractères utilisé par le Gestionnaire de chaînes.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

> [!NOTE]
>  Pas signaler un échec d’allocation en levant une exception. Au lieu de cela, un échec d’allocation doit être signalé en retournant NULL.

### <a name="remarks"></a>Notes

Appelez [IAtlStringMgr::Free](#free) ou [IAtlStringMgr::ReAllocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="clone"></a>  IAtlStringMgr::Clone

Retourne un pointeur vers un nouveau gestionnaire de chaînes pour une utilisation avec une autre instance de `CSimpleStringT`.

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie de la `IAtlStringMgr` objet.

### <a name="remarks"></a>Notes

Généralement appelé par le framework lorsqu’un gestionnaire de chaînes est nécessaire pour une nouvelle chaîne. Dans la plupart des cas, le **cela** pointeur est retourné.

Toutefois, si le Gestionnaire de mémoire ne prend pas en charge utilisé par plusieurs instances de `CSimpleStringT`, un pointeur vers un gestionnaire de chaînes partageable doit être retourné.

> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="free"></a>  IAtlStringMgr::Free

Libère une structure de données de chaîne.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Pointeur vers le bloc de mémoire à libérer.

### <a name="remarks"></a>Notes

Le bloc de mémoire spécifié précédemment alloué par [Allocate](#allocate) ou [réallouer](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString

Retourne un pointeur vers une structure de données de chaîne pour une chaîne vide.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `CStringData` objet utilisé pour représenter une chaîne vide.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner une représentation d’une chaîne vide.

> [!NOTE]
> Lorsque vous implémentez un gestionnaire de chaînes personnalisé, cette fonction ne doit jamais échouer. Vous pouvez le vérifier en incorporant une instance de `CNilStringData` dans la classe de gestionnaire de chaîne et retourner un pointeur vers cette instance.

> [!NOTE]
> Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="reallocate"></a>  IAtlStringMgr::Reallocate

Réalloue une structure de données de chaîne.

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
Le nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize*<br/>
La taille (en octets) du type de caractères utilisé par le Gestionnaire de chaînes.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez cette fonction pour redimensionner le bloc de mémoire existant spécifié par *pData*.

Appelez [IAtlStringMgr::Free](#free) pour libérer la mémoire allouée par cette méthode.

> [!NOTE]
> Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
