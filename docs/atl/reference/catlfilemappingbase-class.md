---
title: Catlfilemappingbase, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e272c9674270c1c600fee697dd77d050d6adb4e0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759826"
---
# <a name="catlfilemappingbase-class"></a>Catlfilemappingbase, classe

Cette classe représente un fichier mappé en mémoire.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
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
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Appelez cette méthode pour copier à partir d’un objet de mappage de fichier.|
|[CAtlFileMappingBase::GetData](#getdata)|Appelez cette méthode pour obtenir les données à partir d’un objet de mappage de fichier.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Appelez cette méthode pour retourner le handle de fichier.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Appelez cette méthode pour obtenir la taille de mappage à partir d’un objet de mappage de fichier.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Appelez cette méthode pour créer un objet de mappage de fichier.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Appelez cette méthode pour créer un objet de mappage de fichier qui permet un accès total à tous les processus.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Appelez cette méthode pour retourner un handle à l’objet de mappage de fichier.|
|[CAtlFileMappingBase::Unmap](#unmap)|Appelez cette méthode pour annuler le mappage d’un objet de mappage de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|Définit l’objet de mappage de fichier en cours à un autre objet de mappage de fichier.|

## <a name="remarks"></a>Notes

Mappage de fichier est l’association du contenu d’un fichier avec une partie de l’espace d’adressage virtuel d’un processus. Cette classe fournit des méthodes permettant de créer des objets de mappage de fichier qui autorisent des programmes d’accéder facilement et partager des données.

Pour plus d’informations, consultez [fichier mappage](/windows/desktop/Memory/file-mapping) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlfile.h

##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase

Constructeur.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Paramètres

*orig*  
L’objet de mappage de fichier d’origine à copier pour créer le nouvel objet.

### <a name="remarks"></a>Notes

Crée un nouvel objet de mappage de fichier, éventuellement à l’aide d’un objet existant. Il est toujours nécessaire d’appeler [CAtlFileMappingBase::MapFile](#mapfile) à ouvrir ou créer l’objet de mappage de fichier pour un fichier particulier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase :: ~ CAtlFileMappingBase

Destructeur.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées par la classe et appelle le [CAtlFileMappingBase::Unmap](#unmap) (méthode).

##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom

Appelez cette méthode pour copier à partir d’un objet de mappage de fichier.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Paramètres

*orig*  
L’objet de mappage de fichier d’origine à copier à partir de.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getdata"></a>  CAtlFileMappingBase::GetData

Appelez cette méthode pour obtenir les données à partir d’un objet de mappage de fichier.

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

Consultez l’exemple de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

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

*hFile*  
Handle au fichier à partir duquel créer un objet de mappage. *hFile* doit être valide et ne peut pas être définie sur INVALID_HANDLE_VALUE.

*nMappingSize*  
La taille du mappage. Si 0, la taille maximale de l’objet de mappage de fichier est égale à la taille actuelle du fichier identifié par *hFile.*

*nOffset*  
Le décalage de fichier dans lequel le mappage doit commencer. La valeur de décalage doit être un multiple de granularité d’allocation de mémoire du système.

*dwMappingProtection*  
La protection souhaitée pour l’affichage des fichiers quand le fichier est mappé. Consultez *flProtect* dans [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwViewDesiredAccess*  
Spécifie le type d’accès à l’affichage des fichiers et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Une fois un objet de mappage de fichier a été créé, la taille du fichier ne doit pas dépasser la taille de l’objet de mappage de fichier ; le cas échéant, tous le contenu du fichier sera disponible pour le partage. Pour plus d’informations, consultez [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) et [MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) dans le SDK Windows.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem

Appelez cette méthode pour créer un objet de mappage de fichier qui permet un accès total à tous les processus.

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

*nMappingSize*  
La taille du mappage. Si 0, la taille maximale de l’objet de mappage de fichier est égale à la taille actuelle de l’objet de mappage de fichier identifié par *szName*.

*szName*  
Le nom de l’objet de mappage.

*pbAlreadyExisted*  
Pointe vers une valeur BOOL qui a la valeur TRUE si l’objet de mappage déjà existé.

*lpsa*  
Le pointeur vers un `SECURITY_ATTRIBUTES` structure qui détermine si le handle retourné peut être hérité par les processus enfants. Consultez *lpAttributes* dans [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) dans le SDK Windows.

*dwMappingProtection*  
La protection souhaitée pour l’affichage des fichiers, quand le fichier est mappé. Consultez *flProtect* dans `CreateFileMapping` dans le SDK Windows.

*dwViewDesiredAccess*  
Spécifie le type d’accès à l’affichage des fichiers et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`MapShareMem` permet à un objet de mappage de fichier existant, créé par [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga), pour être partagés entre les processus.

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

*szName*  
Le nom de l’objet de mappage. Si un handle est ouvert à un objet de mappage de fichier à ce nom et le descripteur de sécurité sur l’objet de mappage n’est pas en conflit avec le *dwViewDesiredAccess* paramètre, l’opération d’ouverture aboutisse.

*nMappingSize*  
La taille du mappage. Si 0, la taille maximale de l’objet de mappage de fichier est égale à la taille actuelle de l’objet de mappage de fichier identifié par *szName*.

*nOffset*  
Le décalage de fichier dans lequel le mappage doit commencer. La valeur de décalage doit être un multiple de granularité d’allocation de mémoire du système.

*dwViewDesiredAccess*  
Spécifie le type d’accès à l’affichage des fichiers et, par conséquent, la protection des pages mappées par le fichier. Consultez *dwDesiredAccess* dans [MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produira si les paramètres d’entrée ne sont pas valides.

##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =

Définit l’objet de mappage de fichier en cours à un autre objet de mappage de fichier.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Paramètres

*orig*  
L’objet de mappage de fichier actuel.

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

Consultez [UnmapViewOfFile](https://msdn.microsoft.com/library/windows/desktop/aa366882) dans le SDK Windows pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Catlfilemapping, classe](../../atl/reference/catlfilemapping-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
