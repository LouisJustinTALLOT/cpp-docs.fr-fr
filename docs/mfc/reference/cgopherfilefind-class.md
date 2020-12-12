---
description: 'En savoir plus sur : classe CGopherFileFind'
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
ms.openlocfilehash: 483a0a6221d08cc3821b0dbc44dd1003c0c40114
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184047"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind, classe

Contribue à la recherche des fichiers Internet sur les serveurs Gopher.

> [!NOTE]
> Les classes `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` et leurs membres ont été dépréciées, car elles ne fonctionnent pas sur la plateforme Windows XP, mais elles continuent de fonctionner sur les plateformes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherFileFind :: CGopherFileFind](#cgopherfilefind)|Construit un objet `CGopherFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGopherFileFind :: FindFile](#findfile)|Recherche un fichier sur un serveur Gopher.|
|[CGopherFileFind :: FindNextFile](#findnextfile)|Poursuit une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|
|[CGopherFileFind :: GetCreationTime](#getcreationtime)|Obtient l’heure à laquelle le fichier spécifié a été créé.|
|[CGopherFileFind :: GetLastAccessTime](#getlastaccesstime)|Obtient l’heure du dernier accès au fichier spécifié.|
|[CGopherFileFind :: GetLastWriteTime](#getlastwritetime)|Obtient l’heure de la dernière écriture dans le fichier spécifié.|
|[CGopherFileFind :: GetLength](#getlength)|Obtient la longueur du fichier trouvé, en octets.|
|[CGopherFileFind :: GetLocator](#getlocator)|Obtient un `CGopherLocator` objet.|
|[CGopherFileFind :: GetScreenName](#getscreenname)|Obtient le nom d’un écran Gopher.|
|[CGopherFileFind :: IsDots](#isdots)|Teste le répertoire actif et les marqueurs de répertoire parents lors de l’itération au sein des fichiers.|

## <a name="remarks"></a>Notes

`CGopherFileFind` comprend des fonctions membres qui commencent une recherche, localisent un fichier et retournent l’URL d’un fichier.

Les autres classes MFC conçues pour Internet et les fichiers locaux recherchés incluent [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). Avec `CGopherFileFind` , ces classes fournissent un mécanisme transparent permettant à l’utilisateur de rechercher des fichiers spécifiques, quel que soit le protocole serveur, le type de fichier ou l’emplacement (un ordinateur local ou un serveur distant). Notez qu’il n’existe aucune classe MFC pour la recherche sur les serveurs HTTP, car HTTP ne prend pas en charge la manipulation de fichiers directe requise par les recherches.

> [!NOTE]
> `CGopherFileFind` ne prend pas en charge les fonctions membres suivantes de sa classe de base [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

En outre, lorsqu' `CGopherFileFind` il est utilisé avec, la `CFileFind` fonction membre [ISDOTS](../../mfc/reference/cfilefind-class.md#isdots) est toujours false.

Pour plus d’informations sur l’utilisation de `CGopherFileFind` et sur les autres classes WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a> CGopherFileFind :: CGopherFileFind

Cette fonction membre est appelée pour construire un `CGopherFileFind` objet.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Pointeur vers un objet [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) .

*dwContext*<br/>
Identificateur de contexte de l’opération. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* est envoyée par MFC à l' `CGopherFileFind` objet à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l' `CGopherFileFind` objet. Lorsque vous construisez un `CGopherFileFind` objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a> CGopherFileFind :: FindFile

Appelez cette fonction membre pour rechercher un fichier Gopher.

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
Référence à un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*pstrString*<br/>
Pointeur vers une chaîne contenant le nom de fichier.

*dwFlags*<br/>
Indicateurs décrivant comment gérer cette session. Les indicateurs valides sont les suivants :

- INTERNET_FLAG_RELOAD d’extraire les données du serveur distant, même si elles sont mises en cache localement.

- INTERNET_FLAG_DONT_CACHE ne mettez pas en cache les données, localement ou dans les passerelles.

- INTERNET_FLAG_SECURE demander des transactions sécurisées sur le réseau avec protocole SSL ou PCT. Cet indicateur s’applique uniquement aux requêtes HTTP.

- INTERNET_FLAG_USE_EXISTING si possible, réutilisez les connexions existantes sur le serveur pour les nouvelles `FindFile` demandes, au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après avoir appelé `FindFile` pour extraire le premier objet Gopher, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers Gopher suivants.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a> CGopherFileFind :: FindNextFile

Appelez cette fonction membre pour continuer une recherche de fichiers commencée par un appel à [CGopherFileFind :: FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro s’il y a plus de fichiers ; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier du répertoire, ou si aucun fichier correspondant n’est trouvé, la `GetLastError` fonction retourne ERROR_NO_MORE_FILES.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a> CGopherFileFind :: GetCreationTime

Obtient l’heure de création du fichier actuel.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure à laquelle le fichier a été créé.

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; 0 en cas d’échec. `GetCreationTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetCreationTime` .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a> CGopherFileFind :: GetLastAccessTime

Obtient l’heure du dernier accès au fichier spécifié.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Paramètres

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure du dernier accès au fichier.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; 0 en cas d’échec. `GetLastAccessTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetLastAccessTime` .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a> CGopherFileFind :: GetLastWriteTime

Obtient l’heure de la dernière modification du fichier.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Paramètres

*pTimeStamp*<br/>
Pointeur vers une structure [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) contenant l’heure de la dernière écriture dans le fichier.

*refTime*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; 0 en cas d’échec. `GetLastWriteTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelé sur cet `CGopherFileFind` objet.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetLastWriteTime` .

> [!NOTE]
> Tous les systèmes de fichiers n’utilisent pas la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions d’horodatage si le système de fichiers ou le serveur sous-jacent ne prend pas en charge la conservation de l’attribut d’heure. Pour plus d’informations sur les formats d’heure, consultez la structure [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Sur certains systèmes d’exploitation, l’heure renvoyée se trouve dans le fuseau horaire local de l’ordinateur où se trouvait le fichier. Pour plus d’informations, consultez API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) Win32.

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a> CGopherFileFind :: GetLength

Appelez cette fonction membre pour connaître la longueur, en octets, du fichier trouvé.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur, en octets, du fichier trouvé.

### <a name="remarks"></a>Notes

`GetLength` utilise la structure Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour récupérer la valeur de la taille du fichier en octets.

> [!NOTE]
> À partir de MFC 7,0, `GetLength` prend en charge les types entiers 64 bits. Le code existant précédemment généré avec cette version plus récente de la bibliothèque peut entraîner des avertissements de troncation.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CFile :: GetLength](../../mfc/reference/cfile-class.md#getlength) (implémentation de la classe de base).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a> CGopherFileFind :: GetLocator

Appelez cette fonction membre pour obtenir l’objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) que [FindFile](#findfile) utilise pour trouver le fichier Gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet `CGopherLocator`.

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a> CGopherFileFind :: GetScreenName

Appelez cette fonction membre pour récupérer le nom de l’écran Gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom de l’écran Gopher.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a> CGopherFileFind :: IsDots

Teste le répertoire actif et les marqueurs de répertoire parents lors de l’itération au sein des fichiers.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si le fichier trouvé porte le nom « . » ou « .. », ce qui indique que le fichier trouvé est effectivement un répertoire. Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `IsDots` .

## <a name="see-also"></a>Voir aussi

[CFileFind, classe](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind, classe](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind, classe](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
