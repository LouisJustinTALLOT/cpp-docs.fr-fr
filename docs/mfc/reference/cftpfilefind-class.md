---
title: CFtpFileFind, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 2f4a394e29be135cac95edf6f504d8b066f53414
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866296"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind, classe

Contribue à la recherche des fichiers Internet sur les serveurs FTP.

## <a name="syntax"></a>Syntaxe

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CFtpFileFind :: CFtpFileFind](#cftpfilefind)|Construit un objet `CFtpFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CFtpFileFind :: FindFile](#findfile)|Recherche un fichier sur un serveur FTP.|
|[CFtpFileFind :: FindNextFile](#findnextfile)|Poursuit une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|
|[CFtpFileFind :: GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin d’accès, du fichier trouvé.|

## <a name="remarks"></a>Notes

`CFtpFileFind` comprend des fonctions membres qui commencent une recherche, localisent un fichier et retournent l’URL ou d’autres informations descriptives sur le fichier.

Les autres classes MFC conçues pour Internet et les fichiers locaux recherchés incluent [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). Avec `CFtpFileFind`, ces classes fournissent un mécanisme transparent permettant au client de rechercher des fichiers spécifiques, quel que soit le protocole serveur ou le type de fichier (un ordinateur local ou un serveur distant). Notez qu’il n’existe aucune classe MFC pour la recherche sur les serveurs HTTP, car HTTP ne prend pas en charge la manipulation de fichiers directe requise pour les recherches.

Pour plus d’informations sur l’utilisation de `CFtpFileFind` et d’autres classes WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Exemple

Le code suivant montre comment énumérer tous les fichiers dans le répertoire actif du serveur FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

##  <a name="cftpfilefind"></a>CFtpFileFind :: CFtpFileFind

Cette fonction membre est appelée pour construire un objet `CFtpFileFind`.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Pointeur vers un objet `CFtpConnection`. Vous pouvez obtenir une connexion FTP en appelant [CInternetSession :: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identificateur de contexte de l’objet `CFtpFileFind`. Pour plus d’informations sur ce paramètre, consultez la **section Notes** .

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* est envoyée par MFC à l’objet `CFtpFileFind` à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet `CFtpFileFind`. Vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

### <a name="example"></a>Exemple

  Consultez l’exemple dans la vue d’ensemble de la classe, plus haut dans cette rubrique.

##  <a name="findfile"></a>CFtpFileFind :: FindFile

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
Indicateurs décrivant comment gérer cette session. Ces indicateurs peuvent être combinés avec l’opérateur or au niveau&#124;du bit () et sont les suivants :

- INTERNET_FLAG_RELOAD d’extraire les données du câble, même si elles sont mises en cache localement. Il s’agit de l’indicateur par défaut.

- INTERNET_FLAG_DONT_CACHE ne mettez pas en cache les données, localement ou dans les passerelles.

- INTERNET_FLAG_RAW_DATA remplacer la valeur par défaut pour retourner les données brutes (structures [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour FTP).

- INTERNET_FLAG_SECURE sécurise les transactions sur le réseau avec protocole SSL ou PCT. Cet indicateur s’applique uniquement aux requêtes HTTP.

- INTERNET_FLAG_EXISTING_CONNECT si possible, réutilisez les connexions existantes sur le serveur pour les nouvelles demandes de `FindFile` au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après avoir appelé `FindFile` pour récupérer le premier fichier FTP, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers FTP suivants.

### <a name="example"></a>Exemple

  Consultez l’exemple précédent dans cette rubrique.

##  <a name="findnextfile"></a>CFtpFileFind :: FindNextFile

Appelez cette fonction membre pour continuer une recherche de fichiers commencée par un appel à la fonction membre [FindFile](#findfile) .

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro s’il y a plus de fichiers ; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour afficher les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier du répertoire, ou si aucun fichier correspondant n’est trouvé, la fonction `GetLastError` retourne ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction au moins une fois avant d’appeler une fonction d’attribut (consultez [CFileFind :: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` encapsule la fonction Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Exemple

  Consultez l’exemple précédent dans cette rubrique.

##  <a name="getfileurl"></a>CFtpFileFind :: GetFileURL

Appelez cette fonction membre pour récupérer l’URL du fichier spécifié.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

Fichier et chemin d’accès de l’URL (Universal Resource Locator).

### <a name="remarks"></a>Notes

`GetFileURL` est semblable à la fonction membre [CFileFind :: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), à ceci près qu’elle retourne l’URL sous la forme `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Voir aussi

[CFileFind, classe](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
