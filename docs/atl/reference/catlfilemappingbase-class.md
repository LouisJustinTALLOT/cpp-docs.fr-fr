---
description: 'En savoir plus sur : classe CAtlFileMappingBase'
title: CAtlFileMappingBase, classe
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
ms.openlocfilehash: 14bf275024dc95a3fdaf76c4e4d699127feaa8f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147457"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase, classe

Cette classe représente un fichier mappé en mémoire.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlFileMappingBase
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Constructeur.|
|[CAtlFileMappingBase :: ~ CAtlFileMappingBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase :: CopyFrom](#copyfrom)|Appelez cette méthode pour effectuer une copie à partir d’un objet de mappage de fichiers.|
|[CAtlFileMappingBase :: GetData](#getdata)|Appelez cette méthode pour obtenir les données d’un objet de mappage de fichier.|
|[CAtlFileMappingBase :: GetHandle](#gethandle)|Appelez cette méthode pour retourner le descripteur de fichier.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Appelez cette méthode pour obtenir la taille de mappage à partir d’un objet de mappage de fichier.|
|[CAtlFileMappingBase :: mappage](#mapfile)|Appelez cette méthode pour créer un objet de mappage de fichier.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Appelez cette méthode pour créer un objet de mappage de fichiers qui autorise un accès complet à tous les processus.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Appelez cette méthode pour retourner un handle à l’objet de mappage de fichier.|
|[CAtlFileMappingBase :: DEMAPPAGE](#unmap)|Appelez cette méthode pour annuler le mappage d’un objet de mappage de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase :: Operator =](#operator_eq)|Définit l’objet de mappage de fichiers en cours sur un autre objet de mappage de fichier.|

## <a name="remarks"></a>Notes

Le mappage de fichier est l’Association du contenu d’un fichier avec une partie de l’espace d’adressage virtuel d’un processus. Cette classe fournit des méthodes pour créer des objets de mappage de fichiers qui permettent aux programmes d’accéder facilement aux données et de les partager.

Pour plus d’informations, consultez [mappage de fichiers](/windows/win32/Memory/file-mapping) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** atlfile. h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a> CAtlFileMappingBase::CAtlFileMappingBase

Constructeur.

```cpp
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier d’origine à copier pour créer le nouvel objet.

### <a name="remarks"></a>Notes

Crée un objet de mappage de fichiers, éventuellement à l’aide d’un objet existant. Il est toujours nécessaire d’appeler [CAtlFileMappingBase ::](#mapfile) fichier de mappage pour ouvrir ou créer l’objet de mappage de fichiers pour un fichier particulier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a> CAtlFileMappingBase :: ~ CAtlFileMappingBase

Destructeur.

```cpp
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées par la classe et appelle la méthode [CAtlFileMappingBase ::](#unmap) unout.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a> CAtlFileMappingBase :: CopyFrom

Appelez cette méthode pour effectuer une copie à partir d’un objet de mappage de fichiers.

```cpp
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier d’origine à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a> CAtlFileMappingBase :: GetData

Appelez cette méthode pour obtenir les données d’un objet de mappage de fichier.

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers les données.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a> CAtlFileMappingBase :: GetHandle

Appelez cette méthode pour retourner un handle à l’objet de mappage de fichier.

```cpp
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle vers l’objet de mappage de fichier.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a> CAtlFileMappingBase::GetMappingSize

Appelez cette méthode pour obtenir la taille de mappage à partir d’un objet de mappage de fichier.

```cpp
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la taille du mappage.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlFileMappingBase :: CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a> CAtlFileMappingBase :: mappage

Appelez cette méthode pour ouvrir ou créer un objet de mappage de fichier pour le fichier spécifié.

```cpp
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Paramètres

*hFile*<br/>
Handle du fichier à partir duquel créer un objet de mappage. *hFile* doit être valide et ne peut pas être défini sur INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Taille du mappage. Si la valeur est 0, la taille maximale de l’objet de mappage de fichiers est égale à la taille actuelle du fichier identifié par *hFile.*

*nOffset*<br/>
Offset de fichier où le mappage doit commencer. La valeur de décalage doit être un multiple de la granularité d’allocation de mémoire du système.

*dwMappingProtection*<br/>
Protection souhaitée pour la vue de fichier lorsque le fichier est mappé. Consultez *flProtect* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue de fichier et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Après la création d’un objet de mappage de fichiers, la taille du fichier ne doit pas dépasser la taille de l’objet de mappage de fichiers ; Si c’est le cas, tout le contenu du fichier ne sera pas disponible pour le partage. Pour plus d’informations, consultez [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) et [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlFileMappingBase :: CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a> CAtlFileMappingBase::MapSharedMem

Appelez cette méthode pour créer un objet de mappage de fichiers qui autorise un accès complet à tous les processus.

```cpp
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Paramètres

*nMappingSize*<br/>
Taille du mappage. Si la valeur est 0, la taille maximale de l’objet de mappage de fichiers est égale à la taille actuelle de l’objet de mappage de fichiers identifié par *szName*.

*szName*<br/>
Nom de l’objet de mappage.

*pbAlreadyExisted*<br/>
Pointe vers une valeur BOOL qui a la valeur TRUE si l’objet de mappage existait déjà.

*lpsa*<br/>
Pointeur vers une `SECURITY_ATTRIBUTES` structure qui détermine si le handle retourné peut être hérité par les processus enfants. Consultez *lpAttributes* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwMappingProtection*<br/>
Protection souhaitée pour la vue de fichier, lorsque le fichier est mappé. Consultez *flProtect* dans `CreateFileMapping` dans le SDK Windows.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue de fichier et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

`MapShareMem` permet à un objet de mappage de fichiers existant, créé par [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga), d’être partagé entre des processus.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a> CAtlFileMappingBase::OpenMapping

Appelez cette méthode pour ouvrir un objet de mappage de fichier nommé pour le fichier spécifié.

```cpp
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Paramètres

*szName*<br/>
Nom de l’objet de mappage. S’il existe un handle ouvert à un objet de mappage de fichiers portant ce nom et que le descripteur de sécurité sur l’objet de mappage n’est pas en conflit avec le paramètre *dwViewDesiredAccess* , l’opération d’ouverture est réussie.

*nMappingSize*<br/>
Taille du mappage. Si la valeur est 0, la taille maximale de l’objet de mappage de fichiers est égale à la taille actuelle de l’objet de mappage de fichiers identifié par *szName*.

*nOffset*<br/>
Offset de fichier où le mappage doit commencer. La valeur de décalage doit être un multiple de la granularité d’allocation de mémoire du système.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue de fichier et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si les paramètres d’entrée ne sont pas valides.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a> CAtlFileMappingBase :: Operator =

Définit l’objet de mappage de fichiers en cours sur un autre objet de mappage de fichier.

```cpp
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier actuel.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’objet actuel.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a> CAtlFileMappingBase :: DEMAPPAGE

Appelez cette méthode pour annuler le mappage d’un objet de mappage de fichier.

```cpp
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CAtlFileMapping, classe](../../atl/reference/catlfilemapping-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
