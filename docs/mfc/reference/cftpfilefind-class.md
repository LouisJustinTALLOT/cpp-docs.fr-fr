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
ms.openlocfilehash: 885005cc04da94ff4339a5f538956b1bfc96b4c3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503680"
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
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Construit un objet `CFtpFileFind`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Recherche un fichier sur un serveur FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Continue une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin d’accès, du fichier trouvé.|

## <a name="remarks"></a>Notes

`CFtpFileFind` inclut les fonctions membres qui commencent une recherche, rechercher un fichier et retournent l’URL ou autres informations descriptives sur le fichier.

Autres classes MFC conçus pour Internet et le fichier local recherchés incluent [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). Avec `CFtpFileFind`, ces classes fournissent un mécanisme transparent pour le client rechercher des fichiers spécifiques, quelle que soit le serveur de type de protocole ou de fichier (un ordinateur local ou un serveur distant). Notez qu’il n’existe aucune classe MFC pour la recherche sur les serveurs HTTP car HTTP ne prend pas en charge la manipulation directe de fichiers requise pour les recherches.

Pour plus d’informations sur l’utilisation `CFtpFileFind` et les autres classes WinInet, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Exemple

Le code suivant montre comment énumérer tous les fichiers dans le répertoire actif du serveur FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

Cette fonction membre est appelée pour construire un `CFtpFileFind` objet.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Pointeur vers un objet `CFtpConnection` . Vous pouvez obtenir une connexion FTP en appelant [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
L’identificateur de contexte pour le `CFtpFileFind` objet. Consultez **remarques** pour plus d’informations sur ce paramètre.

### <a name="remarks"></a>Notes

La valeur par défaut *dwContext* est envoyé par MFC pour le `CFtpFileFind` à partir de l’objet le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le `CFtpFileFind` objet. Vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est renvoyé à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

### <a name="example"></a>Exemple

  Consultez l’exemple dans la vue d’ensemble de la classe plus haut dans cette rubrique.

##  <a name="findfile"></a>  CFtpFileFind::FindFile

Appelez cette fonction membre pour rechercher un fichier FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Paramètres

*pstrName*<br/>
Un pointeur vers une chaîne contenant le nom du fichier à rechercher. Si NULL, l’appel effectue une recherche par caractères génériques (*).

*dwFlags*<br/>
Indicateurs décrivant comment gérer cette session. Ces indicateurs peuvent être combinés avec l’opérateur OR au niveau du bit (&#124;) et sont les suivantes :

- INTERNET_FLAG_RELOAD obtenir les données depuis le câble, même s’il est mis en cache localement. Il s’agit de l’indicateur par défaut.

- Faire INTERNET_FLAG_DONT_CACHE met pas en cache les données, localement ou dans les passerelles.

- INTERNET_FLAG_RAW_DATA remplacer la valeur par défaut pour retourner les données brutes ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) structures pour FTP).

- INTERNET_FLAG_SECURE sécurise les transactions sur le câble avec le protocole SSL (Secure Sockets Layer) ou de pourcentage. Cet indicateur s’applique aux requêtes HTTP uniquement.

- INTERNET_FLAG_EXISTING_CONNECT si possible, réutiliser les connexions existantes sur le serveur pour le nouveau `FindFile` demandes au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après avoir appelé `FindFile` pour récupérer le premier fichier FTP, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers suivants de FTP.

### <a name="example"></a>Exemple

  Consultez l’exemple précédent dans cette rubrique.

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

Appelez cette fonction membre pour continuer une recherche de fichier commencée avec un appel à la [FindFile](#findfile) fonction membre.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro s’il existe plusieurs fichiers ; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour obtenir les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier dans le répertoire, ou si aucune correspondance fichiers peuvent être trouvés, le `GetLastError` fonction retourne ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction au moins une fois avant d’appeler n’importe quelle fonction de l’attribut (voir [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` encapsule la fonction Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Exemple

  Consultez l’exemple plus haut dans cette rubrique.

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

Appelez cette fonction membre pour obtenir l’URL du fichier spécifié.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

Le fichier et le chemin d’accès de l’URL Universal Resource Locator ().

### <a name="remarks"></a>Notes

`GetFileURL` est similaire à la fonction membre [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), à ceci près qu’elle renvoie l’URL sous la forme `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Voir aussi

[CFileFind, classe](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
