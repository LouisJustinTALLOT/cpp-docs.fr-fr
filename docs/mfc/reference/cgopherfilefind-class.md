---
title: CGopherFileFind, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 690c7bd36046161fb39a560b7aa2f7bf13c55828
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339619"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind, classe
Contribue à la recherche des fichiers Internet sur les serveurs Gopher.  
  
> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plate-forme Windows XP, mais ils continueront à fonctionner sur des plateformes antérieures.  
  
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
|[CGopherFileFind::FindFile](#findfile)|Recherche un fichier sur un serveur gopher.|  
|[CGopherFileFind::FindNextFile](#findnextfile)|Continue une recherche de fichier à partir d’un appel précédent à [FindFile](#findfile).|  
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtient l’heure de création du fichier spécifié.|  
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtient l’heure de que dernier accès au fichier spécifié.|  
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtient l’heure de que dernière écriture dans le fichier spécifié.|  
|[CGopherFileFind::GetLength](#getlength)|Obtient la longueur du fichier est trouvé, en octets.|  
|[CGopherFileFind::GetLocator](#getlocator)|Obtenir un `CGopherLocator` objet.|  
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtient le nom d’un écran gopher.|  
|[CGopherFileFind::IsDots](#isdots)|Vérifie si les marqueurs de répertoire actuels pour le répertoire et parent lors de l’itération via des fichiers.|  
  
## <a name="remarks"></a>Notes  
 `CGopherFileFind` inclut les fonctions membres qui commencent une recherche, rechercher un fichier et retournent l’URL d’un fichier.  
  
 Autres classes MFC conçus pour Internet et le fichier local recherchés incluent [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) et [CFileFind](../../mfc/reference/cfilefind-class.md). Avec `CGopherFileFind`, ces classes fournissent un mécanisme transparent pour l’utilisateur de trouver des fichiers spécifiques, quelle que soit le protocole de serveur, le type de fichier ou l’emplacement (un ordinateur local ou un serveur distant.) Notez qu’il n’existe aucune classe MFC pour la recherche sur les serveurs HTTP car HTTP ne prend pas en charge la manipulation directe de fichiers requise par les recherches.  
  
> [!NOTE]
> `CGopherFileFind` ne prend pas en charge les fonctions de membre suivantes de sa classe de base [CFileFind](../../mfc/reference/cfilefind-class.md):  
  
- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)  
  
- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)  
  
- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)  
  
- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)  
  
- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)  
  
 En outre, lorsqu’il est utilisé avec `CGopherFileFind`, le `CFileFind` fonction membre [IsDots](../../mfc/reference/cfilefind-class.md#isdots) est toujours FALSE.  
  
 Pour plus d’informations sur l’utilisation `CGopherFileFind` et les autres classes WinInet, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxinet.h  
  
##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind  
 Cette fonction membre est appelée pour construire un `CGopherFileFind` objet.  
  
```  
explicit CGopherFileFind(
    CGopherConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 *pConnection*  
 Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet.  
  
 *dwContext*  
 L’identificateur de contexte pour l’opération. Consultez **remarques** pour plus d’informations sur *dwContext*.  
  
### <a name="remarks"></a>Notes  
 La valeur par défaut *dwContext* est envoyé par MFC pour le `CGopherFileFind` à partir de l’objet le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le `CGopherFileFind` objet. Lorsque vous construisez un `CGopherFileFind` de l’objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est renvoyé à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
##  <a name="findfile"></a>  CGopherFileFind::FindFile  
 Appelez cette fonction membre pour rechercher un fichier gopher.  
  
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
 *refLocator*  
 Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.  
  
 *pstrString*  
 Un pointeur vers une chaîne contenant le nom de fichier.  
  
 *dwFlags*  
 Indicateurs décrivant comment gérer cette session. Les indicateurs valides sont :  
  
-   INTERNET_FLAG_RELOAD obtenir les données à partir du serveur distant, même s’il est mis en cache localement.  
  
-   Faire INTERNET_FLAG_DONT_CACHE met pas en cache les données, localement ou dans les passerelles.  
  
-   INTERNET_FLAG_SECURE demander les transactions sécurisées sur le câble avec (Secure Sockets Layer) ou de pourcentage. Cet indicateur s’applique aux requêtes HTTP uniquement.  
  
-   INTERNET_FLAG_USE_EXISTING si possible, réutiliser les connexions existantes sur le serveur pour le nouveau `FindFile` demandes, au lieu de créer une nouvelle session pour chaque demande.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Pour obtenir les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé `FindFile` pour récupérer le premier objet gopher, vous pouvez appeler [FindNextFile](#findnextfile) pour récupérer les fichiers suivants gopher.  
  
##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile  
 Appelez cette fonction membre pour continuer une recherche de fichier commencée avec un appel à [CGopherFileFind::FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro s’il existe plusieurs fichiers ; zéro si le fichier trouvé est le dernier dans le répertoire ou si une erreur s’est produite. Pour obtenir les informations d’erreur étendues, appelez la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Si le fichier trouvé est le dernier fichier dans le répertoire, ou si aucune correspondance fichiers peuvent être trouvés, le `GetLastError` fonction retourne ERROR_NO_MORE_FILES.  
  
##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime  
 Obtient l’heure de création pour le fichier actuel.  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pTimeStamp*  
 Un pointeur vers un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) structure contenant l’heure de création du fichier.  
  
 *refTime*  
 Une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; 0 en cas d’échec. `GetCreationTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelée sur ce `CGopherFileFind` objet.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetCreationTime`.  
  
> [!NOTE]
>  Pas tous les systèmes de fichiers utilisent la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de cachet de temps si le système de fichiers ou le serveur sous-jacent ne prend pas en charge en conservant l’attribut de temps. Consultez le [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) structure pour plus d’informations sur les formats d’heure. Sur certains systèmes d’exploitation, l’heure retournée est dans l’heure locale de zone à l’ordinateur ont été trouve le fichier. Consultez Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API pour plus d’informations.  
  
##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime  
 Obtient l’heure de que dernier accès au fichier spécifié.  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *refTime*  
 Une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet.  
  
 *pTimeStamp*  
 Un pointeur vers un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) structure contenant l’heure de dernier accès au fichier.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; 0 en cas d’échec. `GetLastAccessTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelée sur ce `CGopherFileFind` objet.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetLastAccessTime`.  
  
> [!NOTE]
>  Pas tous les systèmes de fichiers utilisent la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de cachet de temps si le système de fichiers ou le serveur sous-jacent ne prend pas en charge en conservant l’attribut de temps. Consultez le [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) structure pour plus d’informations sur les formats d’heure. Sur certains systèmes d’exploitation, l’heure retournée est dans l’heure locale de zone à l’ordinateur ont été trouve le fichier. Consultez Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API pour plus d’informations.  
  
##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime  
 Obtient la dernière fois que le fichier a été modifié.  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pTimeStamp*  
 Un pointeur vers un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) structure contenant l’heure de dernière écriture dans le fichier.  
  
 *refTime*  
 Une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; 0 en cas d’échec. `GetLastWriteTime` retourne 0 uniquement si [FindNextFile](#findnextfile) n’a jamais été appelée sur ce `CGopherFileFind` objet.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `GetLastWriteTime`.  
  
> [!NOTE]
>  Pas tous les systèmes de fichiers utilisent la même sémantique pour implémenter l’horodatage retourné par cette fonction. Cette fonction peut retourner la même valeur retournée par d’autres fonctions de cachet de temps si le système de fichiers ou le serveur sous-jacent ne prend pas en charge en conservant l’attribut de temps. Consultez le [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) structure pour plus d’informations sur les formats d’heure. Sur certains systèmes d’exploitation, l’heure retournée est dans l’heure locale de zone à l’ordinateur ont été trouve le fichier. Consultez Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API pour plus d’informations.  
  
##  <a name="getlength"></a>  CGopherFileFind::GetLength  
 Appelez cette fonction membre pour obtenir la longueur, en octets, du fichier trouvé.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur, en octets, du fichier trouvé.  
  
### <a name="remarks"></a>Notes  
 `GetLength` utilise la structure Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) pour obtenir la valeur de la taille du fichier en octets.  
  
> [!NOTE]
>  À compter de MFC 7.0, `GetLength` prend en charge les types d’entier 64 bits. Code préexistants généré avec cette version plus récente de la bibliothèque peut entraîner des avertissements de troncation.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (l’implémentation de classe de base).  
  
##  <a name="getlocator"></a>  CGopherFileFind::GetLocator  
 Appelez cette fonction membre pour obtenir le [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet [FindFile](#findfile) utilise pour rechercher le fichier gopher.  
  
```  
CGopherLocator GetLocator() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet `CGopherLocator`.  
  
##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName  
 Appelez cette fonction membre pour obtenir le nom de l’écran de gopher.  
  
```  
CString GetScreenName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom de l’écran de gopher.  
  
##  <a name="isdots"></a>  CGopherFileFind::IsDots  
 Vérifie si les marqueurs de répertoire actuels pour le répertoire et parent lors de l’itération via des fichiers.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le fichier trouvé porte le nom «. « ou ».. », ce qui indique que le fichier trouvé est un répertoire. Sinon 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [FindNextFile](#findnextfile) au moins une fois avant d’appeler `IsDots`.  
  
## <a name="see-also"></a>Voir aussi  
 [CFileFind, classe](../../mfc/reference/cfilefind-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind, classe](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind, classe](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile (classe)](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
