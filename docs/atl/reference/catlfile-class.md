---
title: Classe de CAtlFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43ee71aae842ca7100f70af67cd8845d31e39a96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="catlfile-class"></a>Classe de CAtlFile
Cette classe fournit un wrapper mince entourant les fenêtres des API de gestion de fichiers.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlFile : public CHandle
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](#catlfile)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlFile::Create](#create)|Appelez cette méthode pour créer ou ouvrir un fichier.|  
|[CAtlFile::Flush](#flush)|Appelez cette méthode pour effacer les mémoires tampons pour le fichier et de provoquer de toutes les données mises en mémoire tampon à écrire dans le fichier.|  
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Appelez cette méthode pour obtenir les résultats d’une opération superposée sur le fichier.|  
|[CAtlFile::GetPosition](#getposition)|Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier à partir du fichier.|  
|[CAtlFile::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille en octets du fichier.|  
|[CAtlFile::LockRange](#lockrange)|Appelez cette méthode pour le verrouillage d’une région dans le fichier pour empêcher les autres processus d’y accéder.|  
|[CAtlFile::Read](#read)|Appelez cette méthode pour lire des données à partir d’un fichier en commençant à la position indiquée par le pointeur de fichier.|  
|[CAtlFile::Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier.|  
|[CAtlFile::SetSize](#setsize)|Appelez cette méthode pour définir la taille du fichier.|  
|[CAtlFile::UnlockRange](#unlockrange)|Appelez cette méthode pour déverrouiller une région du fichier.|  
|[CAtlFile::Write](#write)|Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` objet|  
  
## <a name="remarks"></a>Notes  
 Utilisez cette classe lorsque les besoins de gestion de fichiers sont relativement simples, mais plus d’abstraction fournit de l’API Windows est nécessaire, sans inclure les dépendances MFC.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlfile.h  
  
##  <a name="catlfile"></a>  CAtlFile::CAtlFile  
 Constructeur.  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `file`  
 L’objet fichier.  
  
 `hFile`  
 Le handle de fichier.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="remarks"></a>Notes  
 Le constructeur de copie transfère la propriété du handle de fichier d’origine `CAtlFile` objet à l’objet qui vient d’être construit.  
  
##  <a name="create"></a>  CAtlFile::Create  
 Appelez cette méthode pour créer ou ouvrir un fichier.  
  
```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *szFilename*  
 Nom du fichier.  
  
 `dwDesiredAccess`  
 L’accès souhaité. Consultez `dwDesiredAccess` dans [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) dans le Kit de développement logiciel Windows.  
  
 `dwShareMode`  
 Le mode de partage. Consultez `dwShareMode` dans **CreateFile**.  
  
 `dwCreationDisposition`  
 La disposition de création. Consultez `dwCreationDisposition` dans **CreateFile**.  
  
 `dwFlagsAndAttributes`  
 Les indicateurs et les attributs. Consultez `dwFlagsAndAttributes` dans **CreateFile**.  
  
 `lpsa`  
 Les attributs de sécurité. Consultez *lpSecurityAttributes* dans **CreateFile**.  
  
 `hTemplateFile`  
 Le fichier de modèle. Consultez `hTemplateFile` dans **CreateFile**.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) pour créer ou ouvrir le fichier.  
  
##  <a name="flush"></a>  CAtlFile::Flush  
 Appelez cette méthode pour effacer les mémoires tampons pour le fichier et de provoquer de toutes les données mises en mémoire tampon à écrire dans le fichier.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [FlushFileBuffers](http://msdn.microsoft.com/library/windows/desktop/aa364439) pour vider les données mises en mémoire tampon dans le fichier.  
  
##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult  
 Appelez cette méthode pour obtenir les résultats d’une opération superposée sur le fichier.  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pOverlapped`  
 La structure. Consultez `lpOverlapped` dans [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) dans le Kit de développement logiciel Windows.  
  
 *dwBytesTransferred*  
 Les octets transférés. Consultez *lpNumberOfBytesTransferred* dans `GetOverlappedResult`.  
  
 `bWait`  
 L’option d’attente. Consultez `bWait` dans `GetOverlappedResult`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) pour obtenir les résultats d’une opération superposée sur le fichier.  
  
##  <a name="getposition"></a>  CAtlFile::GetPosition  
 Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nPos`  
 La position en octets.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) pour obtenir la position actuelle du pointeur de fichier.  
  
##  <a name="getsize"></a>  CAtlFile::GetSize  
 Appelez cette méthode pour obtenir la taille en octets du fichier.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nLen`  
 Le nombre d’octets dans le fichier.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955) pour obtenir la taille en octets du fichier.  
  
##  <a name="lockrange"></a>  CAtlFile::LockRange  
 Appelez cette méthode pour le verrouillage d’une région dans le fichier pour empêcher les autres processus d’y accéder.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nPos`  
 Position dans le fichier où le verrou doit commencer.  
  
 `nCount`  
 La longueur de la plage d’octets à verrouiller.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [fichier de verrouillage](http://msdn.microsoft.com/library/windows/desktop/aa365202) verrouillage d’une région dans le fichier. Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche n’est autorisées. Lorsque vous déverrouillez une région, à l’aide [CAtlFile::UnlockRange](#unlockrange), la plage d’octets doit correspondre exactement à la région qui a été précédemment verrouillée. `LockRange` ne fusionne pas les zones adjacentes ; Si deux régions verrouillées sont adjacentes, vous devez déverrouiller chacune séparément.  
  
##  <a name="m_ptm"></a>  CAtlFile::m_pTM  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="read"></a>  CAtlFile::Read  
 Appelez cette méthode pour lire des données à partir d’un fichier en commençant à la position indiquée par le pointeur de fichier.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pBuffer`  
 Pointeur vers la mémoire tampon qui reçoit les données lues à partir du fichier.  
  
 `nBufSize`  
 Taille de la mémoire tampon en octets.  
  
 `nBytesRead`  
 Nombre d'octets lus.  
  
 `pOverlapped`  
 La structure. Consultez `lpOverlapped` dans [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467) dans le Kit de développement logiciel Windows.  
  
 `pfnCompletionRoutine`  
 La routine d’exécution. Consultez *lpCompletionRoutine* dans [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Les trois premières formes appellent [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467), le dernier [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) pour lire des données à partir du fichier. Utilisez [CAtlFile::Seek](#seek) pour déplacer le pointeur de fichier.  
  
##  <a name="seek"></a>  CAtlFile::Seek  
 Appelez cette méthode pour déplacer le pointeur de fichier du fichier.  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nOffset`  
 Le décalage à partir du point de départ donné par `dwFrom`.  
  
 `dwFrom`  
 Le point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) pour déplacer le pointeur de fichier.  
  
##  <a name="setsize"></a>  CAtlFile::SetSize  
 Appelez cette méthode pour définir la taille du fichier.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nNewLen`  
 Nouvelle longueur du fichier en octets.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) et [SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531) pour définir la taille du fichier. En retour, le pointeur de fichier est placé à la fin du fichier.  
  
##  <a name="unlockrange"></a>  CAtlFile::UnlockRange  
 Appelez cette méthode pour déverrouiller une région du fichier.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nPos`  
 Position dans le fichier où le déverrouillage doit commencer.  
  
 `nCount`  
 La longueur de la plage d’octets à déverrouiller.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Appels [UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715) pour déverrouiller une région du fichier.  
  
##  <a name="write"></a>  CAtlFile::Write  
 Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.  
  
```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pBuffer`  
 La mémoire tampon qui contient les données à écrire dans le fichier.  
  
 `nBufSize`  
 Le nombre d’octets à transférer de la mémoire tampon.  
  
 `pOverlapped`  
 La structure. Consultez `lpOverlapped` dans [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747) dans le Kit de développement logiciel Windows.  
  
 `pfnCompletionRoutine`  
 La routine d’exécution. Consultez *lpCompletionRoutine* dans [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) dans le Kit de développement logiciel Windows.  
  
 `pnBytesWritten`  
 Les octets écrits.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` sur la réussite ou une erreur `HRESULT` en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Les trois premières formes appellent [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747), les appels de dernière [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) pour écrire des données dans le fichier. Utilisez [CAtlFile::Seek](#seek) pour déplacer le pointeur de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de texte défilant](../../visual-cpp-samples.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CHandle, classe](../../atl/reference/chandle-class.md)
