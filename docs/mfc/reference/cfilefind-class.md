---
title: Classe CFileFind
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: f01aa84593afed5a4f2f102da7d161ad42917080
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373876"
---
# <a name="cfilefind-class"></a>Classe CFileFind

Effectue des recherches de fichiers locaux et est la classe de base pour [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), qui effectuent des recherches de fichiers Internet.

## <a name="syntax"></a>Syntaxe

```
class CFileFind : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Construit un objet `CFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFileFind::Fermer](#close)|Ferme la demande de recherche.|
|[CFileFind::FindFile](#findfile)|Recherche un répertoire pour obtenir un nom de fichier spécifié.|
|[CFileFind::FindNextFile](#findnextfile)|Continue une recherche de fichiers à partir d’un appel précédent à [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Obtient le temps que le fichier a été créé.|
|[CFileFind::GetFileName](#getfilename)|Obtient le nom, y compris l’extension, du fichier trouvé|
|[CFileFind::GetFilePath](#getfilepath)|Obtient tout le chemin du fichier trouvé.|
|[CFileFind::GetFileTitle](#getfiletitle)|Obtient le titre du fichier trouvé. Le titre n’inclut pas l’extension.|
|[CFileFind::GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin de fichier, du fichier trouvé.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Obtient le temps que le fichier a été accédé pour la dernière fois.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Obtient le temps que le fichier a été changé pour la dernière fois et enregistré.|
|[CFileFind::GetLength](#getlength)|Obtient la longueur du fichier trouvé, dans les octets.|
|[CFileFind::GetRoot](#getroot)|Obtient le répertoire racine du fichier trouvé.|
|[CFileFind::IsArchived](#isarchived)|Détermine si le fichier trouvé est archivé.|
|[CFileFind::IsCompressed](#iscompressed)|Détermine si le fichier trouvé est comprimé.|
|[CFileFind::IsDirectory](#isdirectory)|Détermine si le fichier trouvé est un répertoire.|
|[CFileFind::IsDots](#isdots)|Détermine si le nom du fichier trouvé a le nom "." ou "..", indiquant qu’il s’agit en fait d’un répertoire.|
|[CFileFind::IsHidden](#ishidden)|Détermine si le fichier trouvé est caché.|
|[CFileFind::IsNormal](#isnormal)|Détermine si le fichier trouvé est normal (en d’autres termes, n’a pas d’autres attributs).|
|[CFileFind::IsReadOnly](#isreadonly)|Détermine si le fichier trouvé est lu uniquement.|
|[CFileFind::IsSystem](#issystem)|Détermine si le fichier trouvé est un fichier système.|
|[CFileFind::IsTemporaire](#istemporary)|Détermine si le fichier trouvé est temporaire.|
|[CFileFind::MatchesMask](#matchesmask)|Indique les attributs de fichier souhaités du fichier à trouver.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Ferme le fichier spécifié par la poignée de recherche actuelle.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Pointeur `CAtlTransactionManager` vers un objet.|

## <a name="remarks"></a>Notes

`CFileFind`comprend les fonctions des membres qui commencent une recherche, localisent un fichier et renvoient le titre, le nom ou le chemin du fichier. Pour les recherches sur Internet, la fonction membre [GetFileURL renvoie](#getfileurl) l’URL du fichier.

`CFileFind`est la classe de base de deux autres classes `CGopherFileFind` MFC conçues pour rechercher `CFtpFileFind` des types de serveurs particuliers: fonctionne spécifiquement avec les serveurs gopher, et fonctionne spécifiquement avec les serveurs FTP. Ensemble, ces trois classes fournissent un mécanisme transparent permettant au client de trouver des fichiers, quel que soit le protocole serveur, le type de fichier ou l’emplacement, soit sur une machine locale ou un serveur distant.

Le code suivant énumérera tous les fichiers dans l’annuaire actuel, en imprimant le nom de chaque fichier :

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Pour garder l’exemple simple, ce code `cout` utilise la classe de la Bibliothèque standard. La `cout` ligne peut être remplacée `CListBox::AddString`par un appel à , par exemple, dans un programme avec une interface utilisateur graphique.

Pour plus d’informations `CFileFind` sur la façon d’utiliser et les autres classes WinInet, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind

Cette fonction de membre `CFileFind` est appelée lorsqu’un objet est construit.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Paramètres

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindclose"></a><a name="close"></a>CFileFind::Fermer

Appelez cette fonction de membre pour mettre fin à la recherche, réinitialiser le contexte et libérer toutes les ressources.

```
void Close();
```

### <a name="remarks"></a>Notes

Après `Close`avoir appelé , vous n’avez pas à créer une nouvelle `CFileFind` instance avant d’appeler [FindFile](#findfile) pour commencer une nouvelle recherche.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::CloseContext

Ferme le fichier spécifié par la poignée de recherche actuelle.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Notes

Ferme le fichier spécifié par la valeur actuelle de la poignée de recherche. Remplacer cette fonction pour modifier le comportement par défaut.

Vous devez appeler les fonctions [FindFile](#findfile) ou [FindNextFile](#findnextfile) au moins une fois pour récupérer une poignée de recherche valide. Les `FindFile` `FindNextFile` fonctions et les fonctions utilisent la poignée de recherche pour localiser les fichiers avec des noms qui correspondent à un nom donné.

## <a name="cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile

Appelez cette fonction de membre pour ouvrir une recherche de fichier.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Paramètres

*pstrName (en)*<br/>
Un pointeur à une chaîne contenant le nom du fichier à trouver. Si vous passez NULL pour *pstrName*, `FindFile` fait\*une wildcard (. ) recherche.

*dwUnused*<br/>
Réservé pour `FindFile` faire polymorphe avec des classes dérivées. Doit être égal à 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après `FindFile` avoir appelé pour commencer la recherche de fichiers, appelez [FindNextFile](#findnextfile) pour récupérer les fichiers suivants. Vous devez `FindNextFile` appeler au moins une fois avant d’appeler l’une des fonctions suivantes des membres d’attribut :

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle (en)](#getfiletitle)

- [GetFilePath (en)](#getfilepath)

- [GetFileURL (en anglais)](#getfileurl)

- [GetLastAccessTime (en anglais)](#getlastaccesstime)

- [GetLastWriteTime (en)](#getlastwritetime)

- [GetLength (en)](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory (en)](#isdirectory)

- [Isdots](#isdots)

- [IsHidden (en anglais)](#ishidden)

- [IsNormal (en)](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporaire](#istemporary)

- [MatchesMask (en)](#matchesmask)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile

Appelez cette fonction de membre pour continuer une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Nonzero s’il y a plus de fichiers; zéro si le fichier trouvé est le dernier dans l’annuaire ou si une erreur s’est produite. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier dans l’annuaire, `GetLastError` ou si aucun fichier correspondant ne peut être trouvé, la fonction renvoie ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Notes

Vous devez `FindNextFile` appeler au moins une fois avant d’appeler l’une des fonctions suivantes des membres d’attribut :

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle (en)](#getfiletitle)

- [GetFilePath (en)](#getfilepath)

- [GetFileURL (en anglais)](#getfileurl)

- [GetLastAccessTime (en anglais)](#getlastaccesstime)

- [GetLastWriteTime (en)](#getlastwritetime)

- [GetLength (en)](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory (en)](#isdirectory)

- [Isdots](#isdots)

- [IsHidden (en anglais)](#ishidden)

- [IsNormal (en)](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporaire](#istemporary)

- [MatchesMask (en)](#matchesmask)

`FindNextFile`enveloppe la fonction Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime

Appelez cette fonction de membre pour obtenir le temps de création du fichier spécifié.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Un pointeur vers une structure [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure de la création du fichier.

*refTime*<br/>
Une référence à un objet [CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 en cas d’échec. `GetCreationTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetCreationTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’opération, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName

Appelez cette fonction de membre pour obtenir le nom du fichier trouvé.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du fichier le plus récemment trouvé.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler GetFileName.

`GetFileName`est l’une des trois `CFileFind` fonctions de membre qui renvoient une certaine forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient :

- `GetFileName`retourne le nom du fichier, y compris la prolongation. Par exemple, `GetFileName` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le nom de fichier *myfile.txt*.

- [GetFilePath](#getfilepath) retourne l’ensemble du chemin pour le fichier. Par exemple, `GetFilePath` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le chemin de fichier *c:myhtml-myfile.txt*.

- [GetFileTitle renvoie](#getfiletitle) le nom du fichier, à l’exclusion de l’extension du fichier. Par exemple, `GetFileTitle` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le titre de fichier *myfile*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath

Appelez cette fonction de membre pour obtenir le chemin complet du fichier spécifié.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin du fichier spécifié.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetFilePath`moins une fois avant d’appeler .

`GetFilePath`est l’une des trois `CFileFind` fonctions de membre qui renvoient une certaine forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient :

- [GetFileName renvoie](#getfilename) le nom du fichier, y compris l’extension. Par exemple, `GetFileName` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le nom de fichier *myfile.txt*.

- `GetFilePath`retourne le chemin entier pour le fichier. Par exemple, `GetFilePath` appeler pour générer un `c:\myhtml\myfile.txt` message utilisateur `c:\myhtml\myfile.txt`sur le fichier renvoie le chemin de fichier .

- [GetFileTitle renvoie](#getfiletitle) le nom du fichier, à l’exclusion de l’extension du fichier. Par exemple, `GetFileTitle` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le titre de fichier *myfile*.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle

Appelez cette fonction de membre pour obtenir le titre du fichier trouvé.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Le titre du fichier.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetFileTitle`moins une fois avant d’appeler .

`GetFileTitle`est l’une des trois `CFileFind` fonctions de membre qui renvoient une certaine forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient :

- [GetFileName renvoie](#getfilename) le nom du fichier, y compris l’extension. Par exemple, `GetFileName` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le nom de fichier *myfile.txt*.

- [GetFilePath](#getfilepath) retourne l’ensemble du chemin pour le fichier. Par exemple, `GetFilePath` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le chemin de fichier *c:myhtml-myfile.txt*.

- `GetFileTitle`retourne le nom du fichier, à l’exclusion de l’extension du fichier. Par exemple, `GetFileTitle` appeler pour générer un message utilisateur sur le fichier *c:myhtml-myfile.txt* retourne le titre de fichier *myfile*.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL

Appelez cette fonction de membre pour récupérer l’URL spécifiée.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

L’URL complète.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetFileURL`moins une fois avant d’appeler .

`GetFileURL`est similaire à la fonction membre [GetFilePath](#getfilepath), sauf `file://path`qu’il retourne l’URL dans le formulaire . Par exemple, `GetFileURL` appeler pour obtenir l’URL complète pour *myfile.txt* renvoie l’URL `file://c:\myhtml\myfile.txt`.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Appelez cette fonction de membre pour obtenir le temps que le fichier spécifié a été accédé pour la dernière fois.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Paramètres

*refTime*<br/>
Une référence à un objet [CTime.](../../atl-mfc-shared/reference/ctime-class.md)

*pTimeStamp*<br/>
Un pointeur d’une structure [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure à l’accès du fichier.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 en cas d’échec. `GetLastAccessTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetLastAccessTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’opération, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Appelez cette fonction de membre pour obtenir la dernière fois que le fichier a été changé.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Un pointeur d’une structure [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure à la dernière écriture du fichier.

*refTime*<br/>
Une référence à un objet [CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 en cas d’échec. `GetLastWriteTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetLastWriteTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’opération, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength

Appelez cette fonction de membre pour obtenir la longueur du fichier trouvé, dans les octets.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du fichier trouvé, dans les octets.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetLength`moins une fois avant d’appeler .

`GetLength`utilise la structure Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour obtenir et retourner la valeur de la taille du fichier, dans les octets.

> [!NOTE]
> À partir de MFC 7.0, `GetLength` prend en charge les types d’intégrant 64 bits. Auparavant, le code existant construit avec cette nouvelle version de la bibliothèque peut entraîner des avertissements de troncation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot

Appelez cette fonction de membre pour obtenir la racine du fichier trouvé.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Valeur de retour

La racine de la recherche active.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetRoot`moins une fois avant d’appeler .

Cette fonction de membre renvoie le spécificateur de disque et le nom du chemin utilisé pour démarrer une recherche. Par exemple, appeler [FindFile](#findfile) avec `*.dat` des résultats dans `GetRoot` le retour d’une chaîne vide. Passer un chemin, `c:\windows\system\*.dll`comme `FindFile` `GetRoot` , `c:\windows\system\`aux résultats de retour .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind:GetFileName](#getfilename).

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::IsArchived

Appelez cette fonction de membre pour déterminer si le fichier trouvé est archivé.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les applications marquent un fichier d’archives, qui doit être sauvegardé ou supprimé, avec FILE_ATTRIBUTE_ARCHIVE, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Vous devez appeler [FindNextFile](#findnextfile) au `IsArchived`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::IsCompressed

Appelez cette fonction de membre pour déterminer si le fichier trouvé est comprimé.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier compressé est marqué de FILE_ATTRIBUTE_COMPRESSED, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Pour un fichier, cet attribut indique que toutes les données du fichier sont compressées. Pour un répertoire, cet attribut indique que la compression est la valeur par défaut pour les fichiers et sous-directeurs nouvellement créés.

Vous devez appeler [FindNextFile](#findnextfile) au `IsCompressed`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>CFileFind::IsDirectory

Appelez cette fonction de membre pour déterminer si le fichier trouvé est un répertoire.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier qui est un répertoire est marqué avec FILE_ATTRIBUTE_DIRECTORY un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Vous devez appeler [FindNextFile](#findnextfile) au `IsDirectory`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

Ce petit programme récure tous les répertoires sur le C : conduire et imprime le nom du répertoire.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots

Appelez cette fonction de membre pour tester pour le répertoire actuel et les marqueurs d’annuaire parent tout en itérant à travers des fichiers.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le fichier trouvé a le nom "." ou "..", qui indique que le fichier trouvé est en fait un répertoire. Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `IsDots`moins une fois avant d’appeler .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindishidden"></a><a name="ishidden"></a>CFileFind::IsHidden

Appelez cette fonction de membre pour déterminer si le fichier trouvé est caché.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Fichiers cachés, qui sont marqués avec FILE_ATTRIBUTE_HIDDEN, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un fichier caché n’est pas inclus dans une liste d’annuaire ordinaire.

Vous devez appeler [FindNextFile](#findnextfile) au `IsHidden`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>CFileFind::IsNormal

Appelez cette fonction de membre pour déterminer si le fichier trouvé est un fichier normal.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Fichiers marqués avec FILE_ATTRIBUTE_NORMAL, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un fichier normal n’a pas d’autres attributs définis. Tous les autres attributs de fichier l’emportent sur cet attribut.

Vous devez appeler [FindNextFile](#findnextfile) au `IsNormal`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>CFileFind::IsReadOnly

Appelez cette fonction de membre pour déterminer si le fichier trouvé est lu uniquement.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier de lecture seulement est marqué de FILE_ATTRIBUTE_READONLY, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Les applications peuvent lire un tel fichier, mais elles ne peuvent pas l’écrire ou le supprimer.

Vous devez appeler [FindNextFile](#findnextfile) au `IsReadOnly`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindissystem"></a><a name="issystem"></a>CFileFind::IsSystem

Appelez cette fonction de membre pour déterminer si le fichier trouvé est un fichier système.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier système est marqué de FILE_ATTRIBUTE_SYSTEM, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un fichier système fait partie du système d’exploitation ou est utilisé exclusivement par le système d’exploitation.

Vous devez appeler [FindNextFile](#findnextfile) au `IsSystem`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>CFileFind::IsTemporaire

Appelez cette fonction de membre pour déterminer si le fichier trouvé est un fichier temporaire.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier temporaire est marqué de FILE_ATTRIBUTE_TEMPORARY, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un fichier temporaire est utilisé pour le stockage temporaire. Les demandes ne doivent être écrites au fichier que si cela est absolument nécessaire. La plupart des données du fichier restent en mémoire sans être rincés dans les médias car le fichier sera bientôt supprimé.

Vous devez appeler [FindNextFile](#findnextfile) au `IsTemporary`moins une fois avant d’appeler .

Consultez la fonction membre [MatchesMask](#matchesmask) pour une liste complète des attributs de fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFileFind::GetLength](#getlength).

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>CFileFind::m_pTM

Pointeur `CAtlTransactionManager` vers un objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::MatchesMask

Appelez cette fonction de membre pour tester les attributs du fichier sur le fichier trouvé.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Paramètres

*dwMask*<br/>
Spécifie un ou plusieurs attributs de fichiers, identifiés dans la structure [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour le fichier trouvé. Pour rechercher plusieurs attributs, utilisez l’opérateur BITwise OU (&#124;). Toute combinaison des attributs suivants est acceptable :

- FILE_ATTRIBUTE_ARCHIVE Le fichier est un fichier d’archives. Les applications utilisent cet attribut pour marquer les fichiers pour la sauvegarde ou la suppression.

- FILE_ATTRIBUTE_COMPRESSED Le fichier ou l’annuaire est comprimé. Pour un fichier, cela signifie que toutes les données du fichier sont compressées. Pour un répertoire, cela signifie que la compression est la valeur par défaut pour les fichiers et sous-directeurs nouvellement créés.

- FILE_ATTRIBUTE_DIRECTORY Le dossier est un répertoire.

- FILE_ATTRIBUTE_NORMAL Le fichier n’a pas d’autres attributs définis. Cet attribut n’est valable que s’il est utilisé seul. Tous les autres attributs de fichier l’emportent sur cet attribut.

- FILE_ATTRIBUTE_HIDDEN Le fichier est caché. Il ne doit pas être inclus dans une liste d’annuaire ordinaire.

- FILE_ATTRIBUTE_READONLY Le fichier est lu uniquement. Les applications peuvent lire le fichier, mais ne peuvent pas l’écrire ou le supprimer.

- FILE_ATTRIBUTE_SYSTEM Le fichier fait partie ou est utilisé exclusivement par le système d’exploitation.

- FILE_ATTRIBUTE_TEMPORARY Le fichier est utilisé pour le stockage temporaire. Les demandes ne doivent être écrites au fichier que si cela est absolument nécessaire. La plupart des données du fichier restent en mémoire sans être rincés dans les médias car le fichier sera bientôt supprimé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `MatchesMask`moins une fois avant d’appeler .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind, classe](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Classe CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Classe CHttpFile](../../mfc/reference/chttpfile-class.md)
