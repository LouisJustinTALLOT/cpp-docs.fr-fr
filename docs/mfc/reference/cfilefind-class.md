---
title: CFileFind, classe
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
ms.openlocfilehash: f2dfd3421d2154b4894b62b71d7993c483a77c53
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916125"
---
# <a name="cfilefind-class"></a>CFileFind, classe

Effectue des recherches de fichiers locales et constitue la classe de base pour [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), qui effectuent des recherches de fichiers sur Internet.

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
|[CFileFind::Close](#close)|Ferme la demande de recherche.|
|[CFileFind::FindFile](#findfile)|Recherche un nom de fichier spécifié dans un répertoire.|
|[CFileFind::FindNextFile](#findnextfile)|Poursuit une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Obtient l’heure à laquelle le fichier a été créé.|
|[CFileFind::GetFileName](#getfilename)|Obtient le nom, y compris l’extension, du fichier trouvé.|
|[CFileFind::GetFilePath](#getfilepath)|Obtient le chemin d’accès complet du fichier trouvé.|
|[CFileFind::GetFileTitle](#getfiletitle)|Obtient le titre du fichier trouvé. Le titre n’inclut pas l’extension.|
|[CFileFind::GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin d’accès du fichier trouvé.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Obtient l’heure du dernier accès au fichier.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Obtient l’heure à laquelle le fichier a été modifié et enregistré pour la dernière fois.|
|[CFileFind::GetLength](#getlength)|Obtient la longueur du fichier trouvé, en octets.|
|[CFileFind::GetRoot](#getroot)|Obtient le répertoire racine du fichier trouvé.|
|[CFileFind::IsArchived](#isarchived)|Détermine si le fichier trouvé est archivé.|
|[CFileFind::IsCompressed](#iscompressed)|Détermine si le fichier trouvé est compressé.|
|[CFileFind::IsDirectory](#isdirectory)|Détermine si le fichier trouvé est un répertoire.|
|[CFileFind::IsDots](#isdots)|Détermine si le nom du fichier trouvé porte le nom «.» ou «..», ce qui indique qu’il s’agit en fait d’un répertoire.|
|[CFileFind::IsHidden](#ishidden)|Détermine si le fichier trouvé est masqué.|
|[CFileFind::IsNormal](#isnormal)|Détermine si le fichier trouvé est normal (en d’autres termes, n’a pas d’autres attributs).|
|[CFileFind::IsReadOnly](#isreadonly)|Détermine si le fichier trouvé est en lecture seule.|
|[CFileFind::IsSystem](#issystem)|Détermine si le fichier trouvé est un fichier système.|
|[CFileFind::IsTemporary](#istemporary)|Détermine si le fichier trouvé est temporaire.|
|[CFileFind::MatchesMask](#matchesmask)|Indique les attributs de fichier souhaités du fichier à rechercher.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Ferme le fichier spécifié par le handle de recherche actuel.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Pointeur vers un `CAtlTransactionManager` objet.|

## <a name="remarks"></a>Notes

`CFileFind`comprend des fonctions membres qui commencent une recherche, localisent un fichier et retournent le titre, le nom ou le chemin d’accès du fichier. Pour les recherches sur Internet, la fonction membre [GetFileURL](#getfileurl) retourne l’URL du fichier.

`CFileFind`est la classe de base pour deux autres classes MFC conçues pour rechercher des types de `CGopherFileFind` serveur particuliers: fonctionne spécifiquement avec les `CFtpFileFind` serveurs Gopher et fonctionne spécifiquement avec les serveurs FTP. Ensemble, ces trois classes fournissent un mécanisme transparent permettant au client de rechercher des fichiers, quel que soit le protocole du serveur, le type de fichier ou l’emplacement, sur un ordinateur local ou sur un serveur distant.

Le code suivant énumère tous les fichiers du répertoire actif, en imprimant le nom de chaque fichier:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Pour que l’exemple reste simple, ce code utilise C++ la classe `cout` de bibliothèque standard. La `cout` ligne peut être remplacée par un appel à `CListBox::AddString`, par exemple, dans un programme avec une interface utilisateur graphique.

Pour plus d’informations sur l’utilisation `CFileFind` de et sur les autres classes WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

Cette fonction membre est appelée lorsqu’un `CFileFind` objet est construit.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Paramètres

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="example"></a>Exemples

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="close"></a>  CFileFind::Close

Appelez cette fonction membre pour terminer la recherche, réinitialiser le contexte et libérer toutes les ressources.

```
void Close();
```

### <a name="remarks"></a>Notes

Après l' `Close`appel de, il n’est pas nécessaire de `CFileFind` créer une nouvelle instance avant d’appeler [FindFile](#findfile) pour commencer une nouvelle recherche.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="closecontext"></a>  CFileFind::CloseContext

Ferme le fichier spécifié par le handle de recherche actuel.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Notes

Ferme le fichier spécifié par la valeur actuelle du handle de recherche. Substituez cette fonction pour modifier le comportement par défaut.

Vous devez appeler les fonctions [FindFile](#findfile) ou [FindNextFile](#findnextfile) au moins une fois pour récupérer un handle de recherche valide. Les `FindFile` fonctions `FindNextFile` et utilisent le descripteur de recherche pour localiser les fichiers dont les noms correspondent à un nom donné.

##  <a name="findfile"></a>  CFileFind::FindFile

Appelez cette fonction membre pour ouvrir une recherche de fichier.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Paramètres

*pstrName*<br/>
Pointeur vers une chaîne contenant le nom du fichier à rechercher. Si vous transmettez lavaleur null `FindFile` pour pstrName, effectue une recherche\*générique (*.).

*dwUnused*<br/>
Réservé pour créer `FindFile` des classes polymorphes avec des classes dérivées. Doit être 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après avoir `FindFile` appelé pour commencer la recherche de fichier, appelez [FindNextFile](#findnextfile) pour récupérer les fichiers suivants. Vous devez appeler `FindNextFile` au moins une fois avant d’appeler l’une des fonctions membres d’attribut suivantes:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

Appelez cette fonction membre pour continuer une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro s’il y a plus de fichiers; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier du répertoire, ou si aucun fichier correspondant n’est trouvé, la `GetLastError` fonction retourne ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Notes

Vous devez appeler `FindNextFile` au moins une fois avant d’appeler l’une des fonctions membres d’attribut suivantes:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`encapsule la fonction Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

Appelez cette fonction membre pour connaître l’heure à laquelle le fichier spécifié a été créé.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) contenant l’heure à laquelle le fichier a été créé.

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; 0 en cas d’échec. `GetCreationTime`retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur `CFileFind` cet objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetCreationTime`d’appeler.

> [!NOTE]
>  Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="getfilename"></a>  CFileFind::GetFileName

Appelez cette fonction membre pour récupérer le nom du fichier trouvé.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du fichier le plus récemment trouvé.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler GetFileName.

`GetFileName`est l’une des `CFileFind` trois fonctions membres qui retournent une forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient:

- `GetFileName`retourne le nom du fichier, y compris l’extension. Par exemple, l' `GetFileName` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile. txt*.

- [GetFilePath](#getfilepath) retourne le chemin d’accès complet au fichier. Par exemple, l' `GetFilePath` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le chemin d’accès du fichier *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) retourne le nom du fichier, à l’exclusion de l’extension de fichier. Par exemple, l' `GetFileTitle` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

Appelez cette fonction membre pour obtenir le chemin d’accès complet du fichier spécifié.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès du fichier spécifié.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetFilePath`d’appeler.

`GetFilePath`est l’une des `CFileFind` trois fonctions membres qui retournent une forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient:

- [GetFileName](#getfilename) retourne le nom du fichier, y compris l’extension. Par exemple, l' `GetFileName` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile. txt*.

- `GetFilePath`retourne le chemin d’accès complet au fichier. Par exemple, l' `GetFilePath` appel de pour générer un message utilisateur sur `c:\myhtml\myfile.txt` le fichier retourne le `c:\myhtml\myfile.txt`chemin d’accès au fichier.

- [GetFileTitle](#getfiletitle) retourne le nom du fichier, à l’exclusion de l’extension de fichier. Par exemple, l' `GetFileTitle` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile*.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

Appelez cette fonction membre pour récupérer le titre du fichier trouvé.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Titre du fichier.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetFileTitle`d’appeler.

`GetFileTitle`est l’une des `CFileFind` trois fonctions membres qui retournent une forme du nom de fichier. La liste suivante décrit les trois et la façon dont ils varient:

- [GetFileName](#getfilename) retourne le nom du fichier, y compris l’extension. Par exemple, l' `GetFileName` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile. txt*.

- [GetFilePath](#getfilepath) retourne le chemin d’accès complet au fichier. Par exemple, l' `GetFilePath` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le chemin d’accès du fichier *c:\myhtml\myfile.txt*.

- `GetFileTitle`retourne le nom du fichier, à l’exclusion de l’extension de fichier. Par exemple, l' `GetFileTitle` appel de pour générer un message utilisateur sur le fichier *c:\myhtml\myfile.txt* retourne le nom de fichier *MyFile*.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

Appelez cette fonction membre pour récupérer l’URL spécifiée.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

URL complète.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetFileURL`d’appeler.

`GetFileURL`est semblable à la fonction membre [GetFilePath](#getfilepath), à ceci près qu’elle retourne l’URL sous `file://path`la forme. Par exemple, l' `GetFileURL` appel à pour obtenir l’URL complète de *MyFile. txt* retourne `file://c:\myhtml\myfile.txt`l’URL.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

Appelez cette fonction membre pour connaître l’heure du dernier accès au fichier spécifié.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Paramètres

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) contenant l’heure du dernier accès au fichier.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; 0 en cas d’échec. `GetLastAccessTime`retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur `CFileFind` cet objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetLastAccessTime`d’appeler.

> [!NOTE]
>  Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

Appelez cette fonction membre pour connaître l’heure de la dernière modification du fichier.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) contenant l’heure de la dernière écriture dans le fichier.

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; 0 en cas d’échec. `GetLastWriteTime`retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur `CFileFind` cet objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetLastWriteTime`d’appeler.

> [!NOTE]
>  Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

### <a name="example"></a>Exemples

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="getlength"></a>  CFileFind::GetLength

Appelez cette fonction membre pour récupérer la longueur du fichier trouvé, en octets.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du fichier trouvé, en octets.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetLength`d’appeler.

`GetLength`utilise la structure Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) pour obtenir et retourner la valeur de la taille du fichier, en octets.

> [!NOTE]
>  À partir de MFC 7,0 `GetLength` , prend en charge les types entiers 64 bits. Le code précédemment existant généré avec cette version plus récente de la bibliothèque peut entraîner des avertissements de troncation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

Appelez cette fonction membre pour récupérer la racine du fichier trouvé.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Racine de la recherche active.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `GetRoot`d’appeler.

Cette fonction membre retourne le spécificateur de lecteur et le nom de chemin d’accès utilisés pour démarrer une recherche. Par exemple, l' `GetRoot` appel de `*.dat` [FindFile](#findfile) avec entraîne le retour d’une chaîne vide. Passage d’un chemin d’accès `c:\windows\system\*.dll`, tel que `GetRoot` , `c:\windows\system\`aux résultats qui `FindFile` retournent.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CFileFind:: GetFileName](#getfilename).

##  <a name="isarchived"></a>  CFileFind::IsArchived

Appelez cette fonction membre pour déterminer si le fichier trouvé est archivé.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les applications marquent un fichier d’archive, qui doit être sauvegardé ou supprimé, avec FILE_ATTRIBUTE_ARCHIVE, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) .

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsArchived`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemples

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

Appelez cette fonction membre pour déterminer si le fichier trouvé est compressé.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier compressé est marqué avec FILE_ATTRIBUTE_COMPRESSED, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Pour un fichier, cet attribut indique que toutes les données du fichier sont compressées. Pour un répertoire, cet attribut indique que la compression est la valeur par défaut pour les fichiers et les sous-répertoires nouvellement créés.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsCompressed`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

Appelez cette fonction membre pour déterminer si le fichier trouvé est un répertoire.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier qui est un répertoire est marqué avec FILE_ATTRIBUTE_DIRECTORY un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) .

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsDirectory`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

Ce petit programme recurset tous les répertoires sur le C:\ et imprime le nom du répertoire.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

Appelez cette fonction membre pour tester le répertoire actif et les marqueurs de répertoire parents lors de l’itération au sein des fichiers.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si le fichier trouvé porte le nom «.» ou «..», ce qui indique que le fichier trouvé est effectivement un répertoire. Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsDots`d’appeler.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="ishidden"></a>  CFileFind::IsHidden

Appelez cette fonction membre pour déterminer si le fichier trouvé est masqué.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les fichiers masqués, qui sont marqués avec FILE_ATTRIBUTE_HIDDEN, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Un fichier masqué n’est pas inclus dans une liste de répertoires ordinaire.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsHidden`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="isnormal"></a>  CFileFind::IsNormal

Appelez cette fonction membre pour déterminer si le fichier trouvé est un fichier normal.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Fichiers marqués avec FILE_ATTRIBUTE_NORMAL, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Aucun autre attribut n’est défini pour un fichier normal. Tous les autres attributs de fichier remplacent cet attribut.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsNormal`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

Appelez cette fonction membre pour déterminer si le fichier trouvé est en lecture seule.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier en lecture seule est marqué avec FILE_ATTRIBUTE_READONLY, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Les applications peuvent lire ce type de fichier, mais elles ne peuvent pas y écrire ou les supprimer.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsReadOnly`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemples

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="issystem"></a>  CFileFind::IsSystem

Appelez cette fonction membre pour déterminer si le fichier trouvé est un fichier système.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier système est marqué avec FILE_ATTRIBUTE_SYSTEM,, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Un fichier système fait partie de, ou est utilisé exclusivement par le système d’exploitation.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsSystem`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="istemporary"></a>  CFileFind::IsTemporary

Appelez cette fonction membre pour déterminer si le fichier trouvé est un fichier temporaire.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Un fichier temporaire est marqué avec FILE_ATTRIBUTE_TEMPORARY, un attribut de fichier identifié dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Un fichier temporaire est utilisé pour le stockage temporaire. Les applications doivent écrire dans le fichier uniquement si cela est absolument nécessaire. La plupart des données du fichier sont conservées en mémoire sans être vidées sur le support car le fichier sera bientôt supprimé.

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `IsTemporary`d’appeler.

Pour obtenir la liste complète des attributs de fichier, consultez la fonction membre [MatchesMask](#matchesmask) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFileFind:: GetLength](#getlength).

##  <a name="m_ptm"></a>  CFileFind::m_pTM

Pointeur vers un `CAtlTransactionManager` objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

Appelez cette fonction membre pour tester les attributs de fichier sur le fichier trouvé.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Paramètres

*dwMask*<br/>
Spécifie un ou plusieurs attributs de fichier, identifiés dans la structure [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) , pour le fichier trouvé. Pour rechercher plusieurs attributs, utilisez l’opérateur or au niveau&#124;du bit (). Toutes les combinaisons des attributs suivants sont acceptables:

- FILE_ATTRIBUTE_ARCHIVE le fichier est un fichier d’archive. Les applications utilisent cet attribut pour marquer des fichiers pour la sauvegarde ou la suppression.

- FILE_ATTRIBUTE_COMPRESSED le fichier ou le répertoire est compressé. Pour un fichier, cela signifie que toutes les données du fichier sont compressées. Pour un répertoire, cela signifie que la compression est la valeur par défaut pour les fichiers et les sous-répertoires nouvellement créés.

- FILE_ATTRIBUTE_DIRECTORY le fichier est un répertoire.

- FILE_ATTRIBUTE_NORMAL aucun autre attribut n’est défini pour le fichier. Cet attribut est valide uniquement s’il est utilisé seul. Tous les autres attributs de fichier remplacent cet attribut.

- FILE_ATTRIBUTE_HIDDEN le fichier est masqué. Il ne doit pas être inclus dans une liste de répertoires ordinaire.

- FILE_ATTRIBUTE_READONLY le fichier est en lecture seule. Les applications peuvent lire le fichier, mais ne peut pas y écrire ou le supprimer.

- FILE_ATTRIBUTE_SYSTEM le fichier fait partie de ou est utilisé exclusivement par le système d’exploitation.

- FILE_ATTRIBUTE_TEMPORARY le fichier est utilisé pour le stockage temporaire. Les applications doivent écrire dans le fichier uniquement si cela est absolument nécessaire. La plupart des données du fichier sont conservées en mémoire sans être vidées sur le support car le fichier sera bientôt supprimé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant `MatchesMask`d’appeler.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind, classe](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
