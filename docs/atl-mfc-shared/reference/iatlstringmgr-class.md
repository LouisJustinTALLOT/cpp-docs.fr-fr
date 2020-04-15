---
title: Classe IAtlStringMgr
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
ms.openlocfilehash: 49ef7850edb18cd51092f282644973376abd4c7c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317495"
---
# <a name="iatlstringmgr-class"></a>Classe IAtlStringMgr

Cette classe représente l’interface d’un `CStringT` gestionnaire de mémoire.

## <a name="syntax"></a>Syntaxe

```
__interface IAtlStringMgr
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Allouer](#allocate)|Appelez cette méthode pour allouer une nouvelle structure de données de chaîne.|
|[Clone](#clone)|Appelez cette méthode pour retourner un pointeur à un `CSimpleStringT`nouveau gestionnaire de chaîne pour une utilisation avec une autre instance de .|
|[Gratuit](#free)|Appelez cette méthode pour libérer une structure de données de chaîne.|
|[GetNilString GetNilString](#getnilstring)|Retourne un pointeur sur l’objet utilisé par les `CStringData` objets à chaîne vides.|
|[Réaffecter](#reallocate)|Appelez cette méthode pour réaffecter une structure de données de chaîne.|

## <a name="remarks"></a>Notes

Cette interface gère la mémoire utilisée par les classes de cordes indépendantes MFC ; tels que [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), et [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Vous pouvez également utiliser cette classe pour implémenter un gestionnaire de mémoire personnalisé pour votre classe de chaînes personnalisée. Pour plus d’informations, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Allocate

Alloue une nouvelle structure de données de chaîne.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Paramètres

*nAllocLength*<br/>
Le nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize (en)*<br/>
La taille (dans les octets) du type de personnage utilisé par le gestionnaire de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

> [!NOTE]
> Ne signalez pas une allocation ratée en lançant une exception. Au lieu de cela, une allocation a échoué devrait être signalée en retournant NULL.

### <a name="remarks"></a>Notes

Appelez [IAtlStringMgr::Free](#free) ou [IAtlStringMgr::ReAllocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

> [!NOTE]
> Pour des exemples d’utilisation, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Clone

Retourne un pointeur à un nouveau gestionnaire `CSimpleStringT`de chaîne pour une utilisation avec une autre instance de .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie de l'objet `IAtlStringMgr`.

### <a name="remarks"></a>Notes

Communément appelé par le cadre quand un gestionnaire de chaîne est nécessaire pour une nouvelle chaîne. Dans la plupart des cas, le **pointeur** est retourné.

Toutefois, si le gestionnaire de mémoire ne `CSimpleStringT`prend pas en charge d’être utilisé par plusieurs cas de , un pointeur à un gestionnaire de chaîne sharable doit être retourné.

> [!NOTE]
> Pour des exemples d’utilisation, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Gratuit

Libère une structure de données de chaîne.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Paramètres

*Pdata*<br/>
Un pointeur vers le bloc de mémoire à libérer.

### <a name="remarks"></a>Notes

Libère le bloc mémoire spécifié précédemment attribué par [Allocate](#allocate) ou [Réaffectation](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Pour des exemples d’utilisation, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

Retourne un pointeur à une structure de données de chaîne pour une chaîne vide.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CStringData` sur l’objet utilisé pour représenter une chaîne vide.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner une représentation d’une chaîne vide.

> [!NOTE]
> Lors de la mise en œuvre d’un gestionnaire de chaîne personnalisé, cette fonction ne doit jamais échouer. Vous pouvez vous assurer cela en `CNilStringData` intégrant un exemple de dans la classe de gestionnaire de chaîne, et retourner un pointeur à cette instance.

> [!NOTE]
> Pour des exemples d’utilisation, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Réallocate

Réaffecte une structure de données de chaîne.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Paramètres

*Pdata*<br/>
Pointeur sur la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nAllocLength*<br/>
Le nombre de caractères dans le nouveau bloc de mémoire.

*nCharSize (en)*<br/>
La taille (dans les octets) du type de personnage utilisé par le gestionnaire de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez cette fonction pour resize le bloc de mémoire existant spécifié par *pData*.

Appelez [IAtlStringMgr::Libre](#free) de libérer la mémoire allouée par cette méthode.

> [!NOTE]
> Pour des exemples d’utilisation, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
