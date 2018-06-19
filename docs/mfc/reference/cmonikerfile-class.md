---
title: Classe de CMonikerFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 431e743396cfc22d49c13a2a9e2f50c88c5ee036
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369227"
---
# <a name="cmonikerfile-class"></a>Classe de CMonikerFile
Représente un flux de données ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) nommé par une [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construit un objet `CMonikerFile`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|Détache et libère le flux et libère le moniker.|  
|[CMonikerFile::Detach](#detach)|Détache le `IMoniker` à partir de ce `CMonikerFile` objet.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Retourne le moniker actuel.|  
|[CMonikerFile::Open](#open)|Ouvre le fichier spécifié pour obtenir un flux de données.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtient le contexte de liaison, ou crée un contexte de liaison initialisés par défaut.|  
  
## <a name="remarks"></a>Notes  
 Un moniker contient des informations comme un chemin d’accès vers un fichier. Si vous avez un pointeur vers un objet de moniker `IMoniker` interface, vous pouvez obtenir l’accès au fichier identifié sans avoir toute autre information spécifique sur l’emplacement du fichier réellement.  
  
 Dérivée de `COleStreamFile`, `CMonikerFile` prend un moniker ou une représentation de chaîne pouvant être transformé en moniker et lie au flux pour lequel le moniker est un nom. Vous pouvez ensuite lire et écrire dans ce flux de données. L’objectif réel de `CMonikerFile` est de fournir un accès simple aux `IStream`s nommé par `IMoniker`s afin que vous n’avez pas à lier à un flux de données vous-même, encore aient `CFile` fonctionnalité dans le flux.  
  
 `CMonikerFile` ne peut pas être utilisé pour lier à autre chose qu’un flux de données. Si vous souhaitez lier à un objet ou un stockage, vous devez utiliser le `IMoniker` interface directement.  
  
 Pour plus d’informations sur les flux et les monikers, consultez [COleStreamFile](../../mfc/reference/colestreamfile-class.md) dans les *référence MFC* et [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) et [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) dans le SDK Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="close"></a>  CMonikerFile::Close  
 Appelez cette fonction pour détacher et de libérer le flux de données et pour libérer le moniker.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 Peut être appelé sur un flux fermés ou déjà fermés.  
  
##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile  
 Construit un objet `CMonikerFile`.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext  
 Appelez cette fonction pour créer un contexte de liaison initialisés par défaut.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Paramètres  
 `pError`  
 Un pointeur vers une exception de fichier. En cas d’erreur, elle est définie à la cause.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le contexte de liaison [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) pour lier avec le cas de réussite ; **NULL**. Si l’instance a été ouvert avec un `IBindHost` interface, le contexte de liaison est extraite la `IBindHost`. S’il existe aucune `IBindHost` interface ou l’interface ne peut pas retourner un contexte de liaison, un contexte de liaison est créé. Pour obtenir une description de la [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) l’interface, consultez le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Un contexte de liaison est un objet qui stocke des informations sur une opération de liaison de moniker particulier. Vous pouvez substituer cette fonction pour fournir un contexte de liaison personnalisé.  
  
##  <a name="detach"></a>  CMonikerFile::Detach  
 Appelez cette fonction pour fermer le flux.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pError`  
 Un pointeur vers une exception de fichier. En cas d’erreur, elle est définie à la cause.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker  
 Appelez cette fonction pour récupérer un pointeur vers le moniker actuel.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’interface de moniker actuel ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Notes  
 Étant donné que `CMonikerFile` n’est pas une interface, le pointeur retourné n’incrémente pas le décompte de références (via [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)), et le moniker est libéré lorsque la `CMonikerFile` objet est libéré. Si vous souhaitez conserver le moniker ou libérer vous-même, vous devez `AddRef` il.  
  
##  <a name="open"></a>  CMonikerFile::Open  
 Appelez cette fonction membre pour ouvrir un objet fichier ou le moniker.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszURL`  
 Une URL ou le nom du fichier à ouvrir.  
  
 `pError`  
 Un pointeur vers une exception de fichier. En cas d’erreur, elle est définie à la cause.  
  
 `pMoniker`  
 Un pointeur vers l’interface de moniker `IMoniker` à utiliser pour obtenir un flux de données.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le `lpszURL` paramètre ne peut pas être utilisé sur un ordinateur Macintosh. Uniquement les `pMoniker` formulaire de **ouvrir** peut être utilisé sur un ordinateur Macintosh.  
  
 Vous pouvez utiliser une URL ou un nom de fichier pour le `lpszURL` paramètre. Par exemple :  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - ou  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de COleStreamFile](../../mfc/reference/colestreamfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
