---
title: CFtpFileFind, classe
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: e53e16f738f0436cbd02074c10ca24dbcc9d0fd8
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206230"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind, classe

Contribue à la recherche des fichiers Internet sur les serveurs FTP.

## <a name="syntax"></a>Syntaxe

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFtpFileFind :: CFtpFileFind](#cftpfilefind)|Construit un objet `CFtpFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFtpFileFind :: FindFile](#findfile)|Recherche un fichier sur un serveur FTP.|
|[CFtpFileFind :: FindNextFile](#findnextfile)|Poursuit une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|
|[CFtpFileFind :: GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin d’accès, du fichier trouvé.|

## <a name="remarks"></a>Remarques

`CFtpFileFind`comprend des fonctions membres qui commencent une recherche, localisent un fichier et retournent l’URL ou d’autres informations descriptives sur le fichier.

Les autres classes MFC conçues pour Internet et les fichiers locaux recherchés incluent [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). Avec `CFtpFileFind` , ces classes fournissent un mécanisme transparent permettant au client de rechercher des fichiers spécifiques, quel que soit le protocole serveur ou le type de fichier (un ordinateur local ou un serveur distant). Il n’existe aucune classe MFC pour la recherche sur les serveurs HTTP, car HTTP ne prend pas en charge la manipulation de fichiers directe requise pour les recherches.

Pour plus d’informations sur l’utilisation de `CFtpFileFind` et sur les autres classes WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Exemple

Le code suivant montre comment énumérer tous les fichiers dans le répertoire actif du serveur FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind :: CFtpFileFind

Cette fonction membre est appelée pour construire un `CFtpFileFind` objet.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Pointeur vers un objet `CFtpConnection`. Vous pouvez obtenir une connexion FTP en appelant [CInternetSession :: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identificateur de contexte de l' `CFtpFileFind` objet. Pour plus d’informations, consultez les **Notes**suivantes.

### <a name="remarks"></a>Remarques

La valeur par défaut pour *dwContext* est envoyée par MFC à l' `CFtpFileFind` objet à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l' `CFtpFileFind` objet. Vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

### <a name="example"></a>Exemple

  Consultez l’exemple dans la vue d’ensemble de la classe, plus haut dans cette rubrique.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind :: FindFile

Appelez cette fonction membre pour rechercher un fichier FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Paramètres

*pstrName*<br/>
Pointeur vers une chaîne contenant le nom du fichier à rechercher. Si la valeur est NULL, l’appel effectue une recherche par caractères génériques (*).

*dwFlags*<br/>
Indicateurs décrivant comment gérer cette session. Ces indicateurs peuvent être combinés avec l’opérateur or au niveau du bit (&#124;) et sont les suivants :

- `INTERNET_FLAG_RELOAD`Récupérez les données à partir du câble, même si elles sont mises en cache localement. Il s’agit de l’indicateur par défaut.

- `INTERNET_FLAG_DONT_CACHE`Ne mettez pas en cache les données, que ce soit localement ou dans une passerelle.

- `INTERNET_FLAG_RAW_DATA`Remplacez la valeur par défaut pour retourner les données brutes (structures [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour FTP).

- `INTERNET_FLAG_SECURE`Sécurise les transactions sur le câble avec protocole SSL ou PCT. Cet indicateur s’applique uniquement aux requêtes HTTP.

- `INTERNET_FLAG_EXISTING_CONNECT`Si possible, réutilisez les connexions existantes sur le serveur pour les nouvelles `FindFile` demandes au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Remarques

Après avoir appelé `FindFile` pour extraire le premier fichier FTP, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers FTP suivants.

### <a name="example"></a>Exemple

  Consultez l’exemple précédent dans cette rubrique.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind :: FindNextFile

Appelez cette fonction membre pour continuer une recherche de fichiers commencée par un appel à la fonction membre [FindFile](#findfile) .

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro s’il y a plus de fichiers ; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier du répertoire, ou si aucun fichier correspondant n’est trouvé, la `GetLastError` fonction retourne ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Remarques

Vous devez appeler cette fonction au moins une fois avant d’appeler une fonction d’attribut (consultez [CFileFind :: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`encapsule la fonction Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Exemple

  Consultez l’exemple précédent dans cette rubrique.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind :: GetFileURL

Appelez cette fonction membre pour récupérer l’URL du fichier spécifié.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur renvoyée

Fichier et chemin d’accès de l’URL (Universal Resource Locator).

### <a name="remarks"></a>Remarques

`GetFileURL`est semblable à la fonction membre [CFileFind :: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) , sauf qu’elle fournit le résultat au format URL. Comme avec `CFileFind::GetFilePath` , le résultat n’inclut pas le nom de fichier. Par exemple, `file1.txt` situé dans `//moose/dir/file1.txt:` retourne `ftp://moose/dir/` .

## <a name="see-also"></a>Voir aussi

[CFileFind, classe](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
