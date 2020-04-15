---
title: CGopherFileFind, classe
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373683"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind, classe

Contribue à la recherche des fichiers Internet sur les serveurs Gopher.

> [!NOTE]
> Les `CGopherConnection`classes `CGopherFile` `CGopherFileFind`, `CGopherLocator` , et leurs membres ont été dépréciés parce qu’ils ne travaillent pas sur la plate-forme Windows XP, mais ils continueront à travailler sur des plates-formes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Construit un objet `CGopherFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Trouve un fichier sur un serveur gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Continue une recherche de fichiers à partir d’un appel précédent à [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtient le temps que le fichier spécifié a été créé.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtient le temps que le fichier spécifié a été consulté pour la dernière fois.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtient l’heure à la dernière écriture du fichier spécifié.|
|[CGopherFileFind::GetLength](#getlength)|Obtient la longueur du fichier trouvé, dans les octets.|
|[CGopherFileFind::GetLocator](#getlocator)|Prends `CGopherLocator` un objet.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtient le nom d’un écran de gaufre.|
|[CGopherFileFind::IsDots](#isdots)|Tests pour le répertoire actuel et les marqueurs d’annuaire des parents tout en itérant à travers les fichiers.|

## <a name="remarks"></a>Notes

`CGopherFileFind`comprend les fonctions des membres qui commencent une recherche, localiser un fichier et retourner l’URL d’un fichier.

D’autres classes MFC conçues pour Internet et les fichiers locaux recherchés comprennent [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). `CGopherFileFind`Avec, ces classes fournissent un mécanisme sans couture pour l’utilisateur de trouver des fichiers spécifiques, quel que soit le protocole du serveur, le type de fichier, ou l’emplacement (soit une machine locale ou un serveur distant.) Notez qu’il n’existe pas de classe MFC pour la recherche sur les serveurs HTTP parce que HTTP ne prend pas en charge la manipulation directe des fichiers requis par les recherches.

> [!NOTE]
> `CGopherFileFind`ne prend pas en charge les fonctions de membre suivantes de sa classe de base [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath (en)](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle (en)](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL (en anglais)](../../mfc/reference/cfilefind-class.md#getfileurl)

En outre, lorsqu’il est utilisé avec `CGopherFileFind`, la `CFileFind` fonction membre [IsDots](../../mfc/reference/cfilefind-class.md#isdots) est toujours FALSE.

Pour plus d’informations `CGopherFileFind` sur la façon d’utiliser et les autres classes WinInet, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Cette fonction de membre `CGopherFileFind` est appelée à construire un objet.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Un pointeur vers un objet [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*dwContexte*<br/>
L’identifiant de contexte pour l’opération. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* `CGopherFileFind` est envoyée par MFC à l’objet `CGopherFileFind` de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet. Lorsque vous `CGopherFileFind` construisez un objet, vous pouvez remplacer la valeur par défaut pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopherFileFind::FindFile

Appelez cette fonction de membre pour trouver un fichier de gopher.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Une référence à un objet [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pstrString*<br/>
Un pointeur à une chaîne contenant le nom du fichier.

*dwFlags*<br/>
Les drapeaux décrivant comment gérer cette session. Les drapeaux valides sont les :

- INTERNET_FLAG_RELOAD Obtenez les données à partir du serveur distant même si elles sont mises en cache localement.

- INTERNET_FLAG_DONT_CACHE Ne cachez pas les données, que ce soit localement ou dans les passerelles.

- INTERNET_FLAG_SECURE Demandez des transactions sécurisées sur le fil avec Secure Sockets Layer ou PCT. Ce drapeau est applicable uniquement aux demandes DE HTTP.

- INTERNET_FLAG_USE_EXISTING Si possible, réutilisez les connexions `FindFile` existantes au serveur pour les nouvelles demandes, au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après `FindFile` avoir appelé pour récupérer le premier objet gopher, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers gopher suivants.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopherFileFind::FindNextFile

Appelez cette fonction de membre pour continuer une recherche de fichier commencée par un appel à [CGopherFileFind:FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Nonzero s’il y a plus de fichiers; zéro si le fichier trouvé est le dernier dans l’annuaire ou si une erreur s’est produite. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier dans l’annuaire, `GetLastError` ou si aucun fichier correspondant ne peut être trouvé, la fonction renvoie ERROR_NO_MORE_FILES.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Obtient le temps de création pour le fichier en cours.

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

Nonzero en cas de succès; 0 en cas d’échec. `GetCreationTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetCreationTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’exploitation, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Obtient le temps que le fichier spécifié a été consulté pour la dernière fois.

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

Nonzero en cas de succès; 0 en cas d’échec. `GetLastAccessTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetLastAccessTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’exploitation, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Obtient la dernière fois que le fichier a été changé.

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

Nonzero en cas de succès; 0 en cas d’échec. `GetLastWriteTime`retourne 0 seulement si [FindNextFile n’a](#findnextfile) jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `GetLastWriteTime`moins une fois avant d’appeler .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter le horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de timbre-temps si le système de fichiers sous-jacent ou le serveur ne prend pas en charge le maintien de l’attribut de temps. Consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour plus d’informations sur les formats de temps. Sur certains systèmes d’exploitation, l’heure de retour est dans le fuseau horaire local à la machine ont été le fichier est situé. Consultez l’API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) pour plus d’informations.

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopherFileFind::GetLength

Appelez cette fonction de membre pour obtenir la longueur, dans les octets, du fichier trouvé.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur, dans les octets, du fichier trouvé.

### <a name="remarks"></a>Notes

`GetLength`utilise la structure Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour obtenir la valeur de la taille du fichier dans les octets.

> [!NOTE]
> À partir de MFC 7.0, `GetLength` prend en charge les types d’intégrant 64 bits. Le code précédemment existant construit avec cette nouvelle version de la bibliothèque peut entraîner des avertissements de troncation.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CFile:GetLength](../../mfc/reference/cfile-class.md#getlength) (la mise en œuvre de la classe de base).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopherFileFind::GetLocator

Appelez cette fonction de membre pour obtenir l’objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) que [FindFile](#findfile) utilise pour trouver le fichier gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `CGopherLocator` .

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopherFileFind::GetScreenName

Appelez cette fonction de membre pour obtenir le nom de l’écran de gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de l’écran de la gaufre.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopherFileFind::IsDots

Tests pour le répertoire actuel et les marqueurs d’annuaire des parents tout en itérant à travers les fichiers.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le fichier trouvé a le nom "." ou "..", qui indique que le fichier trouvé est en fait un répertoire. Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au `IsDots`moins une fois avant d’appeler .

## <a name="see-also"></a>Voir aussi

[Classe CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind, classe](../../mfc/reference/cftpfilefind-class.md)<br/>
[Classe CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Classe CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Classe CHttpFile](../../mfc/reference/chttpfile-class.md)
