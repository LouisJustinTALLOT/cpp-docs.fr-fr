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
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373754"
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
|[CFtpFileFind::FindFile](#findfile)|Trouve un fichier sur un serveur FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Continue une recherche de fichiers à partir d’un appel précédent à [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtient l’URL, y compris le chemin, du fichier trouvé.|

## <a name="remarks"></a>Notes

`CFtpFileFind`comprend les fonctions des membres qui commencent une recherche, localiser un fichier et retourner l’URL ou d’autres informations descriptives sur le fichier.

D’autres classes MFC conçues pour Internet et les fichiers locaux recherchés comprennent [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). `CFtpFileFind`Avec, ces classes fournissent un mécanisme transparent pour le client de trouver des fichiers spécifiques, quel que soit le protocole du serveur ou le type de fichier (soit une machine locale ou un serveur distant). Notez qu’il n’existe pas de classe MFC pour la recherche sur les serveurs HTTP parce que HTTP ne prend pas en charge la manipulation directe des fichiers requis pour les recherches.

Pour plus d’informations `CFtpFileFind` sur la façon d’utiliser et les autres classes WinInet, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Exemple

Le code suivant montre comment énumérer tous les fichiers dans l’annuaire actuel du serveur FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Cette fonction de membre `CFtpFileFind` est appelée à construire un objet.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pConnection*<br/>
Pointeur vers un objet `CFtpConnection`. Vous pouvez obtenir une connexion FTP en appelant [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContexte*<br/>
L’identifiant de `CFtpFileFind` contexte pour l’objet. Voir **Remarques** pour plus d’informations sur ce paramètre.

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* `CFtpFileFind` est envoyée par MFC à l’objet `CFtpFileFind` de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet. Vous pouvez remplacer la valeur par défaut pour définir l’identifiant contextuelle à une valeur de votre choix. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

### <a name="example"></a>Exemple

  Voir l’exemple dans la vue d’ensemble de la classe plus tôt dans ce sujet.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind::FindFile

Appelez cette fonction de membre pour trouver un fichier FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Paramètres

*pstrName (en)*<br/>
Un pointeur à une chaîne contenant le nom du fichier à trouver. Si NULL, l’appel effectuera une recherche wildcard (MD).

*dwFlags*<br/>
Les drapeaux décrivant comment gérer cette session. Ces drapeaux peuvent être combinés avec l’opérateur BITwise OU (&#124;) et sont les suivants:

- INTERNET_FLAG_RELOAD Obtenez les données du fil même si elles sont mises en cache localement. C’est le drapeau par défaut.

- INTERNET_FLAG_DONT_CACHE Ne cachez pas les données, que ce soit localement ou dans les passerelles.

- INTERNET_FLAG_RAW_DATA Remplacer la valeur par défaut pour retourner les données brutes [(structures WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pour FTP).

- INTERNET_FLAG_SECURE sécurise les transactions sur le fil avec Secure Sockets Layer ou PCT. Ce drapeau est applicable uniquement aux demandes DE HTTP.

- INTERNET_FLAG_EXISTING_CONNECT Si possible, réutilisez les connexions `FindFile` existantes au serveur pour de nouvelles demandes au lieu de créer une nouvelle session pour chaque demande.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Après `FindFile` avoir appelé pour récupérer le premier fichier FTP, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers FTP suivants.

### <a name="example"></a>Exemple

  Voir l’exemple précédent dans ce sujet.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Appelez cette fonction de membre pour continuer une recherche de fichier commencée par un appel à la fonction membre [FindFile.](#findfile)

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valeur de retour

Nonzero s’il y a plus de fichiers; zéro si le fichier trouvé est le dernier dans l’annuaire ou si une erreur s’est produite. Pour obtenir des informations d’erreur étendues, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Si le fichier trouvé est le dernier fichier dans l’annuaire, `GetLastError` ou si aucun fichier correspondant ne peut être trouvé, la fonction renvoie ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction au moins une fois avant d’appeler toute fonction d’attribut (voir [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`enveloppe la fonction Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Exemple

  Voir l’exemple plus tôt dans ce sujet.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Appelez cette fonction de membre pour obtenir l’URL du fichier spécifié.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

Le fichier et le chemin du localisateur universel de ressource (URL).

### <a name="remarks"></a>Notes

`GetFileURL`est similaire à la fonction membre [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), sauf `ftp://moose/dir/file.txt`qu’il retourne l’URL sous le formulaire .

## <a name="see-also"></a>Voir aussi

[Classe CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Classe CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Classe CHttpFile](../../mfc/reference/chttpfile-class.md)
