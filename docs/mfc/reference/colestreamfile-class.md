---
title: Classe de COleStreamFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs:
- C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 805c32145d844cc1103cab7c4987c0595ff5935f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371388"
---
# <a name="colestreamfile-class"></a>Classe de COleStreamFile
Représente un flux de données ( `IStream`) dans un fichier composé dans le cadre du stockage structuré OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construit un objet `COleStreamFile`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|Associe un flux de données à l’objet.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crée un flux à partir de la mémoire globale et l’associe à l’objet.|  
|[COleStreamFile::CreateStream](#createstream)|Crée un flux de données et l’associe à l’objet.|  
|[COleStreamFile::Detach](#detach)|Dissocie le flux à partir de l’objet.|  
|[COleStreamFile::GetStream](#getstream)|Retourne le flux actuel.|  
|[COleStreamFile::OpenStream](#openstream)|En toute sécurité ouvre un flux de données et l’associe à l’objet.|  
  
## <a name="remarks"></a>Notes  
 Un `IStorage` objet doit exister pour que le flux de données peut être ouvert ou créé à moins qu’il s’agit d’un flux de mémoire.  
  
 `COleStreamFile` les objets sont manipulés exactement comme [CFile](../../mfc/reference/cfile-class.md) objets.  
  
 Pour plus d’informations sur la manipulation des flux et stockages, consultez l’article [conteneurs : fichiers composés](../../mfc/containers-compound-files.md)...  
  
 Pour plus d’informations, consultez [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) et [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="attach"></a>  COleStreamFile::Attach  
 Associe le flux OLE fourni avec le `COleStreamFile` objet.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpStream`  
 Pointe vers le flux de données OLE ( `IStream`) à associer à l’objet. Ne peut pas être **NULL**.  
  
### <a name="remarks"></a>Notes  
 L’objet ne doit pas déjà être associé à un flux OLE.  
  
 Pour plus d’informations, consultez [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) dans le Kit de développement logiciel Windows.  
  
##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile  
 Crée un objet `COleStreamFile`.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpStream`  
 Pointeur vers le flux OLE à associer à l’objet.  
  
### <a name="remarks"></a>Notes  
 Si `lpStream` est **NULL**, l’objet n’est pas associé à un flux OLE, dans le cas contraire, l’objet est associé avec le flux OLE fourni.  
  
 Pour plus d’informations, consultez [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) dans le Kit de développement logiciel Windows.  
  
##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream  
 En toute sécurité crée un flux de données en dehors de la mémoire partagée globale où une défaillance est une condition normale, attendue.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pError`  
 Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou **NULL** qui indique l’état d’achèvement de l’opération de création. Spécifiez ce paramètre si vous souhaitez analyser des exceptions possibles générées par la tentative de création du flux.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le flux est créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La mémoire est allouée par le sous-système OLE.  
  
 Pour plus d’informations, consultez [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) dans le Kit de développement logiciel Windows.  
  
##  <a name="createstream"></a>  COleStreamFile::CreateStream  
 En toute sécurité crée un flux de données dans l’objet de stockage fourni où une défaillance est une condition normale, attendue.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpStorage`  
 Pointe vers l’objet de stockage OLE qui contient le flux doit être créé. Ne peut pas être **NULL**.  
  
 `lpszStreamName`  
 Nom du flux de données doit être créé. Ne peut pas être **NULL**.  
  
 `nOpenFlags`  
 Mode d’accès à utiliser lors de l’ouverture du flux. Exclusif, en lecture/écriture et créer des modes sont utilisés par défaut. Pour obtenir une liste complète des modes disponibles, consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou **NULL**. Spécifiez ce paramètre si vous souhaitez analyser des exceptions possibles générées par la tentative de création du flux.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le flux est créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Une exception de fichier sera levée si la fonction open échoue et `pError` n’est pas **NULL**.  
  
 Pour plus d’informations, consultez [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) dans le Kit de développement logiciel Windows.  
  
##  <a name="detach"></a>  COleStreamFile::Detach  
 Dissocie le flux à partir de l’objet sans fermer le flux de données.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le flux de données ( `IStream`) qui a été associé à l’objet.  
  
### <a name="remarks"></a>Notes  
 Le flux doit être fermé d’une autre façon avant la fin du programme.  
  
 Pour plus d’informations, consultez [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) dans le Kit de développement logiciel Windows.  
  
##  <a name="getstream"></a>  COleStreamFile::GetStream  
 Appelez cette fonction pour retourner un pointeur vers le flux actuel.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’interface de flux de données actuelle ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="openstream"></a>  COleStreamFile::OpenStream  
 Ouvre un flux existant.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpStorage`  
 Pointe vers l’objet de stockage OLE qui contient le flux à ouvrir. Ne peut pas être **NULL**.  
  
 `lpszStreamName`  
 Nom du flux à ouvrir. Ne peut pas être **NULL**.  
  
 `nOpenFlags`  
 Mode d’accès à utiliser lors de l’ouverture du flux. Exclusif et en lecture/écriture, les modes sont utilisés par défaut. Pour obtenir la liste complète des modes disponibles, consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou **NULL**. Spécifiez ce paramètre si vous souhaitez analyser des exceptions possibles générées par une tentative d’ouverture du flux.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le flux est ouvert avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Une exception de fichier sera levée si la fonction open échoue et `pError` n’est pas **NULL**.  
  
 Pour plus d’informations, consultez [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



