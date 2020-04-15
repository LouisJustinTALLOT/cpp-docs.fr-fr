---
title: Classe CStringData
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
ms.openlocfilehash: 5915d9e25588e4e35538619662281ceaf1b35ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317612"
---
# <a name="cstringdata-class"></a>Classe CStringData

Cette classe représente les données d’un objet à cordes.

## <a name="syntax"></a>Syntaxe

```
struct CStringData
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddRef](#addref)|Incréments le nombre de références de l’objet de données de chaîne.|
|[data](#data)|Récupère les données de caractère d’un objet à chaîne.|
|[IsLocked](#islocked)|Détermine si le tampon de l’objet de chaîne associé est verrouillé.|
|[IsShared](#isshared)|Détermine si le tampon de l’objet à chaîne associé est actuellement partagé.|
|[Verrouiller](#lock)|Verrouille le tampon de l’objet de chaîne associé.|
|[Libérer](#release)|Libère l’objet de chaîne spécifié.|
|[Déverrouiller](#unlock)|Déverrouille le tampon de l’objet à chaîne associé.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[nAllocLength](#nalloclength)|Longueur des données `XCHAR`allouées dans s (sans compter la fin nulle)|
|[nDataLength (en)](#ndatalength)|Longueur des données `XCHAR`actuellement utilisées dans s (sans compter la fin nulle)|
|[nRefs](#nrefs)|Le nombre de références actuel de l’objet.|
|[pStringMgr](#pstringmgr)|Un pointeur pour le gestionnaire de cordes de cet objet à cordes.|

## <a name="remarks"></a>Notes

Cette classe ne doit être utilisée que par les développeurs qui mettent en œuvre des gestionnaires de chaînes personnalisés. Pour plus d’informations sur les gestionnaires de chaînes personnalisées, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Cette classe résume différents types d’informations et de données associées à un objet à chaîne plus élevée, tels que [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), ou [CFixedStringT.](../../atl-mfc-shared/reference/cfixedstringt-class.md) Chaque objet à chaîne supérieure `CStringData` contient un pointeur sur son objet associé, permettant à plusieurs objets de chaîne de pointer vers le même objet de données de chaîne. Cette relation est représentée par`nRefs`le nombre `CStringData` de références ( ) de l’objet.

> [!NOTE]
> Dans certains cas, un type `CFixedString`de chaîne (tel que ) ne partagera pas un objet de données de chaîne avec plus d’un objet à chaîne plus élevé. Pour plus d’informations à ce sujet, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Ces données sont composées de :

- Le gestionnaire de mémoire (de type [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la chaîne.

- La longueur actuelle ( [nDataLength](#ndatalength)) de la corde.

- La longueur allouée ( [nAllocLength](#nalloclength)) de la chaîne. Pour des raisons de performance, cela peut différer de la longueur actuelle de la chaîne

- Le nombre de référence actuel ( `CStringData` [nRefs](#nrefs)) de l’objet. Cette valeur est utilisée pour déterminer le `CStringData` nombre d’objets à chaîne partageant le même objet.

- Le tampon de caractère réel ( [données](#data)) de la chaîne.

   > [!NOTE]
   > Le tampon de caractère réel de l’objet de chaîne est `CStringData` attribué par le gestionnaire de chaîne et est annexé à l’objet.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>CStringData::AddRef

Incréments le nombre de références de l’objet de chaîne.

```
void AddRef() throw();
```

### <a name="remarks"></a>Notes

Incréments le nombre de références de l’objet de chaîne.

> [!NOTE]
> N’appelez pas cette méthode sur une chaîne avec un nombre de références négatif, car un nombre négatif indique que le tampon de chaîne est verrouillé.

## <a name="cstringdatadata"></a><a name="data"></a>CStringData::data

Retourne un pointeur au tampon de caractère d’un objet de chaîne.

```
void* data() throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le tampon de caractère de l’objet de chaîne.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner le tampon de caractère actuel de l’objet de chaîne associé.

> [!NOTE]
> Ce tampon n’est `CStringData` pas attribué par l’objet, mais par le gestionnaire de chaîne en cas de besoin. Lorsqu’il est alloué, le tampon est annexé à l’objet de données de chaîne.

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::IsLocked

Détermine si le tampon de caractère est verrouillé.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le tampon est verrouillé; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour déterminer si le tampon de caractère d’un objet de chaîne est actuellement verrouillé.

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared

Détermine si le tampon de caractère est partagé.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le tampon est partagé; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour déterminer si le tampon de caractère d’un objet de données de chaîne est actuellement partagé entre plusieurs objets à cordes.

## <a name="cstringdatalock"></a><a name="lock"></a>CStringData::Lock

Verrouille le tampon de caractère de l’objet de chaîne associé.

```
void Lock() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour verrouiller le tampon de caractère de l’objet de données de chaîne. Le verrouillage et le déverrouillage sont utilisés lorsque le développeur exige un accès direct au tampon de caractère. Un bon exemple de verrouillage est démontré par les méthodes `CSimpleStringT` [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) de .

> [!NOTE]
> Un tampon de caractère ne peut être verrouillé que si le tampon n’est pas partagé entre des objets à chaîne plus élevée.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAllocLength

Longueur du tampon de caractère alloué.

```
int nAllocLength;
```

### <a name="remarks"></a>Notes

Stocke la longueur du tampon `XCHAR`de données alloué dans s (sans compter la fin nulle).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength

Longueur actuelle de l’objet de chaîne.

```
int nDataLength;
```

### <a name="remarks"></a>Notes

Stocke la longueur des `XCHAR`données actuellement utilisées dans s (sans compter la fin nulle).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

Nombre de références de l’objet de données de chaîne.

```
long nRefs;
```

### <a name="remarks"></a>Notes

Stocke le nombre de références de l’objet de données de chaîne. Ce compte indique le nombre d’objets à chaîne plus élevés qui sont associés à l’objet de données de chaîne. Une valeur négative indique que l’objet de données de chaîne est actuellement verrouillé.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr

Le gestionnaire de mémoire de l’objet de chaîne associé.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Notes

Stocke le gestionnaire de mémoire pour l’objet de chaîne associé. Pour plus d’informations sur les gestionnaires de mémoire et les chaînes, voir [Memory Management et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::Libération

Décrément le nombre de références de l’objet de données de chaîne.

```
void Release() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour décroisser le `CStringData` nombre de références, libérant la structure si le nombre de références atteint zéro. Ceci est généralement fait quand un objet de chaîne est supprimé, et donc n’a plus besoin de référencer l’objet de données de chaîne.

Par exemple, le code `CStringData::Release` suivant appellerait l’objet de données de chaîne associé `str1`à :

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::Unlock

Débloque le tampon de caractère de l’objet de chaîne associé.

```
void Unlock() throw();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour débloquer le tampon de caractère de l’objet de données de chaîne. Une fois qu’un tampon est déverrouillé, il est partageable et peut être compté de référence.

> [!NOTE]
> Chaque appel `Lock` doit être assorti d’un appel correspondant à `Unlock`.

Le verrouillage et le déverrouillage sont utilisés lorsque le développeur doit s’assurer que les données de chaîne ne sont pas partagées. Un bon exemple de verrouillage est démontré par les méthodes `CSimpleStringT` [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) de .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
