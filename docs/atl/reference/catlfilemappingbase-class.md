---
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
ms.openlocfilehash: 3d9627c7a19cccc0cd3aec46d71b23c8a84711bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497772"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase, classe

Cette classe représente un fichier mappé en mémoire.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlFileMappingBase
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Constructeur.|
|[CAtlFileMappingBase::~CAtlFileMappingBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Appelez cette méthode pour effectuer une copie à partir d’un objet de mappage de fichiers.|
|[CAtlFileMappingBase::GetData](#getdata)|Appelez cette méthode pour obtenir les données d’un objet de mappage de fichier.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Appelez cette méthode pour retourner le descripteur de fichier.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Appelez cette méthode pour obtenir la taille de mappage à partir d’un objet de mappage de fichier.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Appelez cette méthode pour créer un objet de mappage de fichier.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Appelez cette méthode pour créer un objet de mappage de fichiers qui autorise un accès complet à tous les processus.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Appelez cette méthode pour retourner un handle à l’objet de mappage de fichier.|
|[CAtlFileMappingBase::Unmap](#unmap)|Appelez cette méthode pour annuler le mappage d’un objet de mappage de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|Définit l’objet de mappage de fichiers en cours sur un autre objet de mappage de fichier.|

## <a name="remarks"></a>Notes

Le mappage de fichier est l’Association du contenu d’un fichier avec une partie de l’espace d’adressage virtuel d’un processus. Cette classe fournit des méthodes pour créer des objets de mappage de fichiers qui permettent aux programmes d’accéder facilement aux données et de les partager.

Pour plus d’informations, consultez [mappage de fichiers](/windows/win32/Memory/file-mapping) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête:** atlfile. h

##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase

Constructeur.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier d’origine à copier pour créer le nouvel objet.

### <a name="remarks"></a>Notes

Crée un objet de mappage de fichiers, éventuellement à l’aide d’un objet existant. Il est toujours nécessaire d’appeler [CAtlFileMappingBase::](#mapfile) fichier de mappage pour ouvrir ou créer l’objet de mappage de fichiers pour un fichier particulier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase::~CAtlFileMappingBase

Destructeur.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées par la classe et appelle la méthode [CAtlFileMappingBase::](#unmap) unout.

##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom

Appelez cette méthode pour effectuer une copie à partir d’un objet de mappage de fichiers.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier d’origine à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getdata"></a>  CAtlFileMappingBase::GetData

Appelez cette méthode pour obtenir les données d’un objet de mappage de fichier.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers les données.

##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle

Appelez cette méthode pour retourner un handle à l’objet de mappage de fichier.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle vers l’objet de mappage de fichier.

##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize

Appelez cette méthode pour obtenir la taille de mappage à partir d’un objet de mappage de fichier.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille du mappage.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile

Appelez cette méthode pour ouvrir ou créer un objet de mappage de fichier pour le fichier spécifié.

```
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
Protection souhaitée pour la vue de fichier lorsque le fichier est mappé. Consultez *flProtect* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) dans le SDK Windows.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue de fichier et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Après la création d’un objet de mappage de fichiers, la taille du fichier ne doit pas dépasser la taille de l’objet de mappage de fichiers; Si c’est le cas, tout le contenu du fichier ne sera pas disponible pour le partage. Pour plus d’informations, consultez [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) et [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem

Appelez cette méthode pour créer un objet de mappage de fichiers qui autorise un accès complet à tous les processus.

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

*nMappingSize*<br/>
Taille du mappage. Si la valeur est 0, la taille maximale de l’objet de mappage de fichiers est égale à la taille actuelle de l’objet de mappage de fichiers identifié par *szName*.

*szName*<br/>
Nom de l’objet de mappage.

*pbAlreadyExisted*<br/>
Pointe vers une valeur BOOL qui a la valeur TRUE si l’objet de mappage existait déjà.

*lpsa*<br/>
Pointeur vers une `SECURITY_ATTRIBUTES` structure qui détermine si le handle retourné peut être hérité par les processus enfants. Consultez *lpAttributes* dans [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) dans le SDK Windows.

*dwMappingProtection*<br/>
Protection souhaitée pour la vue de fichier, lorsque le fichier est mappé. Consultez *flProtect* dans `CreateFileMapping` dans le SDK Windows.

*dwViewDesiredAccess*<br/>
Spécifie le type d’accès à la vue de fichier et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`MapShareMem`permet à un objet de mappage de fichiers existant, créé par [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw), d’être partagé entre des processus.

##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping

Appelez cette méthode pour ouvrir un objet de mappage de fichier nommé pour le fichier spécifié.

```
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

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si les paramètres d’entrée ne sont pas valides.

##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =

Définit l’objet de mappage de fichiers en cours sur un autre objet de mappage de fichier.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Paramètres

*orig*<br/>
Objet de mappage de fichier actuel.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’objet actuel.

##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap

Appelez cette méthode pour annuler le mappage d’un objet de mappage de fichier.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CAtlFileMapping, classe](../../atl/reference/catlfilemapping-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
