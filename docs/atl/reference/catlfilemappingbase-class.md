---
title: Classe CAtlFileMappingBase
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: ae790cf1248c78ff9aa70c0e586f86af6c8f3b9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318941"
---
# <a name="catlfilemappingbase-class"></a>Classe CAtlFileMappingBase

Cette classe représente un fichier cartographié par la mémoire.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlFileMappingBase
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Constructeur.|
|[CAtlFileMappingBase::CAtlFileMappingBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::CopyDe](#copyfrom)|Appelez cette méthode pour copier à partir d’un objet de cartographie de fichiers.|
|[CAtlFileMappingBase::GetData](#getdata)|Appelez cette méthode pour obtenir les données à partir d’un objet de cartographie de fichiers.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Appelez cette méthode pour retourner la poignée de fichier.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Appelez cette méthode pour obtenir la taille de la cartographie à partir d’un objet de cartographie de fichiers.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Appelez cette méthode pour créer un objet de cartographie de fichiers.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Appelez cette méthode pour créer un objet de cartographie de fichiers qui permet un accès complet à tous les processus.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Appelez cette méthode pour retourner une poignée à l’objet de cartographie de fichiers.|
|[CAtlFileMappingBase::Unmap](#unmap)|Appelez cette méthode pour débrancher un objet de cartographie de fichiers.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::opérateur](#operator_eq)|Définit l’objet de cartographie de fichiers actuel à un autre objet de cartographie de fichiers.|

## <a name="remarks"></a>Notes

La cartographie des fichiers est l’association du contenu d’un fichier avec une partie de l’espace d’adresse virtuelle d’un processus. Cette classe fournit des méthodes pour créer des objets de cartographie de fichiers qui permettent aux programmes d’accéder et de partager facilement des données.

Pour plus d’informations, voir [La cartographie des fichiers](/windows/win32/Memory/file-mapping) dans windows SDK.

## <a name="requirements"></a>Spécifications

**En-tête:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Constructeur.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Paramètres

*Bail*<br/>
L’objet original de cartographie de fichiers à copier pour créer le nouvel objet.

### <a name="remarks"></a>Notes

Crée un nouvel objet de cartographie de fichiers, en option à l’aide d’un objet existant. Il est encore nécessaire d’appeler [CAtlFileMappingBase::MapFile](#mapfile) pour ouvrir ou créer l’objet de cartographie de fichiers pour un fichier particulier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase::CAtlFileMappingBase

Destructeur.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées par la classe et appelle la [CAtlFileMappingBase::Unmap](#unmap) méthode.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::CopyDe

Appelez cette méthode pour copier à partir d’un objet de cartographie de fichiers.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Paramètres

*Bail*<br/>
L’objet original de cartographie de fichier à copier à partir.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase::GetData

Appelez cette méthode pour obtenir les données à partir d’un objet de cartographie de fichiers.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur aux données.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase::GetHandle

Appelez cette méthode pour retourner une poignée à l’objet de cartographie de fichiers.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Valeur de retour

Retourne une poignée à l’objet de cartographie des fichiers.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Appelez cette méthode pour obtenir la taille de la cartographie à partir d’un objet de cartographie de fichiers.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille de la cartographie.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase::MapFile

Appelez cette méthode pour ouvrir ou créer un objet de cartographie de fichiers pour le fichier spécifié.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Paramètres

*hFile (en)*<br/>
Gérer le fichier à partir duquel créer un objet de cartographie. *hFile* doit être valide et ne peut pas être mis à INVALID_HANDLE_VALUE.

*nMappingSize (en)*<br/>
La taille de la cartographie. Si 0, la taille maximale de l’objet de cartographie de fichier est égale à la taille actuelle du fichier identifié par *hFile.*

*nOffset (en anglais)*<br/>
Le fichier compense l’endroit où la cartographie doit commencer. La valeur offset doit être un multiple de la granularité d’allocation de mémoire du système.

*dwMappingProtection*<br/>
La protection souhaitée pour la vue du fichier lorsque le fichier est cartographié. Voir *flProtect* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue du fichier et, par conséquent, la protection des pages cartographiées par le fichier. Voir *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Une fois qu’un objet de cartographie de fichiers a été créé, la taille du fichier ne doit pas dépasser la taille de l’objet de cartographie des fichiers ; si c’est le cas, tout le contenu du fichier ne sera pas disponible pour le partage. Pour plus de détails, voir [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) et [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Appelez cette méthode pour créer un objet de cartographie de fichiers qui permet un accès complet à tous les processus.

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Paramètres

*nMappingSize (en)*<br/>
La taille de la cartographie. Si 0, la taille maximale de l’objet de cartographie de fichier est égale à la taille actuelle de l’objet de cartographie de fichier identifié par *szName*.

*szName (szName)*<br/>
Le nom de l’objet de cartographie.

*pbAlreadyExisted pbAlreadyExisted pbAlreadyExisted pb*<br/>
Points à une valeur BOOL qui est réglé à VRAI si l’objet de cartographie existait déjà.

*lpsa lpsa*<br/>
Le pointeur `SECURITY_ATTRIBUTES` d’une structure qui détermine si la poignée retournée peut être héritée par les processus de l’enfant. Voir *lpAttributes* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwMappingProtection*<br/>
La protection souhaitée pour la vue du fichier, lorsque le fichier est cartographié. Voir *flProtect* dans `CreateFileMapping` le Windows SDK.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue du fichier et, par conséquent, la protection des pages cartographiées par le fichier. Voir *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

`MapShareMem`permet de partager un objet de cartographie de fichiers existant, créé par [CreateFileMapping.](/windows/win32/api/winbase/nf-winbase-createfilemappinga)

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Appelez cette méthode pour ouvrir un objet de cartographie de fichiers nommé pour le fichier spécifié.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Paramètres

*szName (szName)*<br/>
Le nom de l’objet de cartographie. S’il y a une poignée ouverte à un objet de cartographie de fichiers par ce nom et que le descripteur de sécurité sur l’objet cartographique n’entre pas en conflit avec le paramètre *dwViewDesiredAccess,* l’opération ouverte réussit.

*nMappingSize (en)*<br/>
La taille de la cartographie. Si 0, la taille maximale de l’objet de cartographie de fichier est égale à la taille actuelle de l’objet de cartographie de fichier identifié par *szName*.

*nOffset (en anglais)*<br/>
Le fichier compense l’endroit où la cartographie doit commencer. La valeur offset doit être un multiple de la granularité d’allocation de mémoire du système.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue du fichier et, par conséquent, la protection des pages cartographiées par le fichier. Voir *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si les paramètres d’entrée sont invalides.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase::opérateur

Définit l’objet de cartographie de fichiers actuel à un autre objet de cartographie de fichiers.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Paramètres

*Bail*<br/>
L’objet de cartographie de fichiers actuel.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à l’objet actuel.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase::Unmap

Appelez cette méthode pour débrancher un objet de cartographie de fichiers.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Voir [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) dans le Windows SDK pour plus de détails.

## <a name="see-also"></a>Voir aussi

[Classe CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
