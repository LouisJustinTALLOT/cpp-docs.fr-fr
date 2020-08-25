---
title: CStringData (classe)
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 140836f45ed2f4088bc0baed67676f93cb268d01
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832111"
---
# <a name="cstringdata-class"></a>CStringData (classe)

Cette classe représente les données d’un objet String.

## <a name="syntax"></a>Syntaxe

```
struct CStringData
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[AddRef](#addref)|Incrémente le décompte de références de l’objet de données de chaîne.|
|[data](#data)|Récupère les données caractères d’un objet String.|
|[IsLocked](#islocked)|Détermine si la mémoire tampon de l’objet String associé est verrouillée.|
|[IsShared](#isshared)|Détermine si la mémoire tampon de l’objet String associé est actuellement partagée.|
|[Verrouiller](#lock)|Verrouille la mémoire tampon de l’objet String associé.|
|[Version release](#release)|Libère l’objet String spécifié.|
|[Bloquer](#unlock)|Déverrouille la mémoire tampon de l’objet String associé.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|[nAllocLength](#nalloclength)|Longueur des données allouées dans s (à l’exclusion de la `XCHAR` valeur null de fin)|
|[nDataLength](#ndatalength)|Longueur des données actuellement utilisées dans `XCHAR` s (à l’exclusion de la valeur null de fin)|
|[nRefs](#nrefs)|Le décompte de références actuel de l’objet.|
|[pStringMgr](#pstringmgr)|Pointeur vers le gestionnaire de chaînes de cet objet String.|

## <a name="remarks"></a>Notes

Cette classe doit être utilisée uniquement par les développeurs qui implémentent des gestionnaires de chaînes personnalisés. Pour plus d’informations sur les gestionnaires de chaînes personnalisés, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md) .

Cette classe encapsule divers types d’informations et de données associés à un objet String plus élevé, tel que [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)ou [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) . Chaque objet String plus élevé contient un pointeur vers l’objet qui lui est associé `CStringData` , ce qui permet à plusieurs objets String de pointer vers le même objet de données String. Cette relation est représentée par le décompte de références ( `nRefs` ) de l' `CStringData` objet.

> [!NOTE]
> Dans certains cas, un type chaîne (tel que `CFixedString` ) ne partage pas un objet de données de type chaîne avec plusieurs objets de chaîne plus élevés. Pour plus d’informations, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Ces données sont composées des éléments suivants :

- Gestionnaire de mémoire (de type [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la chaîne.

- Longueur actuelle ( [nDataLength](#ndatalength)) de la chaîne.

- Longueur allouée ( [nAllocLength](#nalloclength)) de la chaîne. Pour des raisons de performances, il peut être différent de la longueur de chaîne actuelle

- Le décompte de références actuel ( [nRefs](#nrefs)) de l' `CStringData` objet. Cette valeur est utilisée pour déterminer le nombre d’objets de chaîne qui partagent le même `CStringData` objet.

- Mémoire tampon de caractères réelle ( [données](#data)) de la chaîne.

   > [!NOTE]
   > La mémoire tampon de caractères réelle de l’objet String est allouée par le gestionnaire de chaînes et ajoutée à l' `CStringData` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpstr. h

## <a name="cstringdataaddref"></a><a name="addref"></a> CStringData :: AddRef

Incrémente le décompte de références de l’objet String.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Notes

Incrémente le décompte de références de l’objet String.

> [!NOTE]
> N’appelez pas cette méthode sur une chaîne avec un nombre de références négatif, car un nombre négatif indique que la mémoire tampon de la chaîne est verrouillée.

## <a name="cstringdatadata"></a><a name="data"></a> CStringData ::d ATA

Retourne un pointeur vers la mémoire tampon de caractères d’un objet String.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la mémoire tampon de caractères de l’objet String.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner la mémoire tampon de caractères actuelle de l’objet String associé.

> [!NOTE]
> Cette mémoire tampon n’est pas allouée par l' `CStringData` objet, mais par le gestionnaire de chaînes si nécessaire. Lorsqu’elle est allouée, la mémoire tampon est ajoutée à l’objet de données de chaîne.

## <a name="cstringdataislocked"></a><a name="islocked"></a> CStringData :: IsLocked

Détermine si la mémoire tampon de caractères est verrouillée.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la mémoire tampon est verrouillée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour déterminer si la mémoire tampon de caractères d’un objet String est actuellement verrouillée.

## <a name="cstringdataisshared"></a><a name="isshared"></a> CStringData :: IsShared

Détermine si la mémoire tampon de caractères est partagée.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la mémoire tampon est partagée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour déterminer si la mémoire tampon de caractères d’un objet de données de type chaîne est actuellement partagée entre plusieurs objets String.

## <a name="cstringdatalock"></a><a name="lock"></a> CStringData :: Lock

Verrouille la mémoire tampon de caractères de l’objet String associé.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour verrouiller la mémoire tampon de caractères de l’objet de données de chaîne. Le verrouillage et le déverrouillage sont utilisés lorsque l’accès direct à la mémoire tampon de caractères est requis par le développeur. Un bon exemple de verrouillage est démontré par les méthodes [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) de `CSimpleStringT` .

> [!NOTE]
> Une mémoire tampon de caractères ne peut être verrouillée que si la mémoire tampon n’est pas partagée entre des objets de chaîne plus élevés.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a> CStringData :: nAllocLength

Longueur de la mémoire tampon de caractères allouée.

```
int nAllocLength;
```

### <a name="remarks"></a>Notes

Stocke la longueur de la mémoire tampon de données allouée dans s (à l’exclusion de la `XCHAR` valeur null de fin).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a> CStringData :: nDataLength

Longueur actuelle de l’objet String.

```
int nDataLength;
```

### <a name="remarks"></a>Notes

Stocke la longueur des données actuellement utilisées dans s (à l’exclusion de la `XCHAR` valeur null de fin).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a> CStringData :: nRefs

Nombre de références de l’objet de données de chaîne.

```
long nRefs;
```

### <a name="remarks"></a>Notes

Stocke le décompte de références de l’objet de données de chaîne. Ce nombre indique le nombre d’objets de chaîne plus élevés associés à l’objet de données de chaîne. Une valeur négative indique que l’objet de données de type chaîne est actuellement verrouillé.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a> CStringData ::p StringMgr

Gestionnaire de mémoire de l’objet String associé.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Notes

Stocke le gestionnaire de mémoire pour l’objet String associé. Pour plus d’informations sur les gestionnaires de mémoire et les chaînes, consultez Gestion de la [mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a> CStringData :: Release

Décrémente le décompte de références de l’objet de données de chaîne.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour décrémenter le nombre de références, en libérant la `CStringData` structure si le nombre de références atteint zéro. C’est généralement le cas lorsqu’un objet String est supprimé et qu’il n’a plus besoin de référencer l’objet de données String.

Par exemple, le code suivant appelle `CStringData::Release` pour l’objet de données de chaîne associé à `str1` :

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a> CStringData :: Unlock

Déverrouille la mémoire tampon de caractères de l’objet String associé.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour déverrouiller la mémoire tampon de caractères de l’objet de données de chaîne. Une fois qu’une mémoire tampon est déverrouillée, elle est partageable et peut être décomptée.

> [!NOTE]
> Chaque appel à `Lock` doit être mis en correspondance par un appel correspondant à `Unlock` .

Le verrouillage et le déverrouillage sont utilisés lorsque le développeur doit s’assurer que les données de chaîne ne sont pas partagées. Un bon exemple de verrouillage est démontré par les méthodes [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) de `CSimpleStringT` .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
