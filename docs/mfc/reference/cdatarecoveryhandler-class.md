---
title: CDataRecoveryHandler, classe
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: 4bb4d4ddf291cb1efc01b887c54a6573c52df8dc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842921"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler, classe

L' `CDataRecoveryHandler` enregistrement automatique enregistre les documents et les restaure si une application se ferme de manière inattendue.

## <a name="syntax"></a>Syntaxe

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Construit un objet `CDataRecoveryHandler`.|

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Enregistre de façon automatique chaque fichier enregistré avec la `CDataRecoveryHandler` classe.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Enregistre automatique le document spécifié.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Ajoute un document à la liste des documents ouverts.|
|[CDataRecoveryHandler ::D eleteAllAutosavedFiles](#deleteallautosavedfiles)|Supprime tous les fichiers enregistrés en cours.|
|[CDataRecoveryHandler ::D eleteAutosavedFile](#deleteautosavedfile)|Supprime le fichier enregistré automatique spécifié.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Génère le nom d’un fichier d’enregistrement automatique associé au nom de fichier de document fourni.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Retourne l’intervalle entre les tentatives d’enregistrement automatique.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Retourne le chemin d’accès des fichiers enregistrés de façon automatique.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Récupère le nom du document à partir d’un `CDocument` objet.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Récupère le titre normal pour le document spécifié.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crée et retourne le titre du document récupéré.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Récupère l’identificateur de redémarrage unique pour l’application.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indique si `CDataRecoveryHandler` effectue un enregistrement automatique sur la boucle inactive en cours.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indique si le gestionnaire de redémarrage a entraîné la fermeture de l’application.|
|[CDataRecoveryHandler :: Initialize](#initialize)|Initialise la `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Affiche une boîte de dialogue à l’utilisateur pour chaque document `CDataRecoveryHandler` enregistré. La boîte de dialogue détermine si l’utilisateur souhaite restaurer le document enregistré de façon automatique.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Charge la liste des documents ouverts à partir du Registre.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Supprime le document fourni de la liste des documents ouverts.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Ouvre les documents précédemment ouverts.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaure les documents enregistrés de façon automatique en fonction de l’entrée de l’utilisateur.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Enregistre la liste actuelle des documents ouverts dans le Registre Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Définit l’intervalle de temps entre les cycles d’enregistrement automatique, en millisecondes.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Définit le répertoire où sont stockés les fichiers enregistrés.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Définit l’identificateur de redémarrage unique pour cette instance du `CDataRecoveryHandler` .|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Définit si `CDataRecoveryHandler` enregistre les informations du document ouvert dans le Registre Windows pendant le cycle d’inactivité actuel.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Définit si la sortie précédente de l’application a été provoquée par le gestionnaire de redémarrage.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Met à jour les informations d’un document, car l’utilisateur l’a enregistré.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|m_bRestoringPreviousOpenDocs|Indique si le gestionnaire de récupération de données ouvre à nouveau les documents précédemment ouverts.|
|m_bSaveDocumentInfoOnIdle|Indique si le gestionnaire de récupération de données enregistre les documents à la prochaine boucle inactive.|
|m_bShutdownByRestartManager|Indique si le gestionnaire de redémarrage entraîne la fermeture de l’application.|
|m_dwRestartManagerSupportFlags|Indicateurs qui indiquent la prise en charge fournie par le gestionnaire de redémarrage pour l’application.|
|m_lstAutosavesToDelete|Liste des fichiers enregistrés de façon automatique qui n’ont pas été supprimés lors de la fermeture des documents d’origine. Lorsque l’application se ferme, le gestionnaire de redémarrage tente de supprimer les fichiers.|
|m_mapDocNameToAutosaveName|Mappage des noms de documents aux noms de fichiers enregistrés de façon automatique.|
|m_mapDocNameToDocumentPtr|Mappage des noms de documents aux pointeurs [CDocument](../../mfc/reference/cdocument-class.md) .|
|m_mapDocNameToRestoreBool|Mappage des noms de documents à un paramètre booléen qui indique s’il faut restaurer le document enregistré de façon automatique.|
|m_mapDocumentPtrToDocName|Mappage des `CDocument` pointeurs vers les noms de documents.|
|m_mapDocumentPtrToDocTitle|Mappage des `CDocument` pointeurs vers les titres de document. Ces titres sont utilisés pour l’enregistrement des fichiers.|
|m_nAutosaveInterval|Durée en millisecondes entre les sauvegardes automatique.|
|m_nTimerID|Identificateur du minuteur d’enregistrement automatique.|
|m_strAutosavePath|Emplacement de stockage des documents enregistrés.|
|m_strRestartIdentifier|Représentation sous forme de chaîne d’un GUID pour le gestionnaire de redémarrage.|

## <a name="remarks"></a>Notes

Le gestionnaire de redémarrage utilise la `CDataRecoveryHandler` classe pour effectuer le suivi de tous les documents ouverts et les enregistrer à nouveau en fonction des besoins. Pour activer l’enregistrement automatique, utilisez la méthode [CDataRecoveryHandler :: SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) . Cette méthode indique au `CDataRecoveryHandler` d’effectuer un enregistrement automatique sur la boucle inactive suivante. Le gestionnaire de redémarrage appelle `SetSaveDocumentInfoOnIdle` lorsque le `CDataRecoveryHandler` doit effectuer un enregistrement automatique.

Toutes les méthodes de la `CDataRecoveryHandler` classe sont virtuelles. Substituez les méthodes de cette classe pour créer votre propre gestionnaire de récupération de données personnalisé. À moins de créer votre propre gestionnaire de récupération de données ou le gestionnaire de redémarrage, n’instanciez pas un CDataRecoveryHandler. La [classe CWinApp](../../mfc/reference/cwinapp-class.md) crée un `CDataRecoveryHandler` objet tel qu’il est requis.

Avant de pouvoir utiliser un `CDataRecoveryHandler` objet, vous devez appeler [CDataRecoveryHandler :: Initialize](#initialize).

Étant donné que la `CDataRecoveryHandler` classe est étroitement connectée au gestionnaire de redémarrage, `CDataRecoveryHandler` dépend du paramètre global `m_dwRestartManagerSupportFlags` . Ce paramètre détermine les autorisations dont dispose le gestionnaire de redémarrage et comment il interagit avec votre application. Pour incorporer le gestionnaire de redémarrage dans une application existante, vous devez assigner `m_dwRestartManagerSupportFlags` la valeur appropriée dans le constructeur de votre application principale. Pour plus d’informations sur l’utilisation du gestionnaire de redémarrage, consultez [Comment : ajouter la prise en charge du gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdatarecovery. h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a> CDataRecoveryHandler::AutosaveAllDocumentInfo

Enregistre de façon automatique chaque fichier enregistré avec la `CDataRecoveryHandler` classe.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si `CDataRecoveryHandler` tous les documents sont enregistrés ; FALSe si un document n’a pas été enregistré.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE s’il n’y a aucun document à enregistrer. Elle retourne également la valeur TRUE sans enregistrer de documents si la récupération du `CWinApp` ou `CDocManager` de l’application génère une erreur.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL doivent être définis dans `m_dwRestartManagerSupportFlags` . Pour plus d’informations, consultez [Comment : ajouter la prise en charge du gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a> CDataRecoveryHandler::AutosaveDocumentInfo

Enregistre automatique le document spécifié.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers le `CDocument` à enregistrer.

*bResetModifiedFlag*\
dans TRUE indique que le `CDataRecoveryHandler` *pDocument* doit être modifié ; La valeur FALSe indique que le Framework considère que *pDocument* n’est pas modifié. Pour plus d’informations sur l’effet de cet indicateur, consultez la section Notes.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les indicateurs appropriés sont définis et que *pDocument* est un `CDocument` objet valide.

### <a name="remarks"></a>Notes

Chaque `CDocument` objet a un indicateur qui indique s’il a changé depuis le dernier enregistrement. Utilisez [CDocument :: IsModified](../../mfc/reference/cdocument-class.md#ismodified) pour déterminer l’état de cet indicateur. Si `CDocument` a n’a pas changé depuis le dernier enregistrement, `AutosaveDocumentInfo` supprime tous les fichiers enregistrés de façon automatique pour ce document. Si un document a été modifié depuis le dernier enregistrement, le fait de le fermer invite l’utilisateur à enregistrer le document avant de se fermer.

> [!NOTE]
> L’utilisation de *bResetModifiedFlag* pour changer l’état du document en inchangé peut entraîner la perte de données non enregistrées par l’utilisateur. Si le Framework considère qu’un document n’est pas modifié, sa fermeture ne demande pas à l’utilisateur de l’enregistrer.

Cette méthode lève une exception avec la macro [Assert](diagnostic-services.md#assert) si *pDocument* n’est pas un `CDocument` objet valide.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL doivent être définis dans *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a> CDataRecoveryHandler::CDataRecoveryHandler

Construit un objet `CDataRecoveryHandler`.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Paramètres

*dwRestartManagerSupportFlags*\
dans Indique les options du gestionnaire de redémarrage qui sont prises en charge.

*nAutosaveInterval*\
dans Durée entre les sauvegardes automatique. Ce paramètre est exprimé en millisecondes.

### <a name="remarks"></a>Notes

L’infrastructure MFC crée automatiquement un `CDataRecoveryHandler` objet pour votre application lorsque vous utilisez l’Assistant **nouveau projet** . À moins que vous ne personnalisiez le comportement de récupération des données ou le gestionnaire de redémarrage, vous ne devez pas créer d' `CDataRecoveryHandler` objet.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a> CDataRecoveryHandler::CreateDocumentInfo

Ajoute un document à la liste des documents ouverts.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers un `CDocument` . Cette méthode crée les informations de document pour ce `CDocument` .

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Cette méthode vérifie si *pDocument* figure déjà dans la liste des documents avant d’ajouter le document. Si *pDocument* figure déjà dans la liste, cette méthode supprime le fichier enregistré automatique associé à *pDocument*.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL doivent être définis dans *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a> CDataRecoveryHandler ::D eleteAllAutosavedFiles

Supprime tous les fichiers enregistrés en cours.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne toujours la valeur TRUE.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a> CDataRecoveryHandler ::D eleteAutosavedFile

Supprime le fichier enregistré automatique spécifié.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Paramètres

*strAutosavedFile*\
dans Chaîne qui contient le nom du fichier enregistré de façon automatique.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne toujours TRUE.

### <a name="remarks"></a>Notes

Si cette méthode ne peut pas supprimer le fichier enregistré, il enregistre le nom du fichier dans une liste. Le destructeur de la `CDataRecoveryHandler` tente de supprimer chaque fichier enregistré avec enregistrement automatique spécifié dans cette liste.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a> CDataRecoveryHandler::GenerateAutosaveFileName

Génère le nom d’un fichier d’enregistrement automatique associé au nom de fichier de document fourni.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Paramètres

*strDocumentName*<br/>
dans Chaîne qui contient le nom du document. `GenerateAutosaveFileName` utilise ce nom de document pour générer un nom de fichier d’enregistrement automatique correspondant.

### <a name="return-value"></a>Valeur renvoyée

Nom du fichier d’enregistrement automatique généré à partir de *strDocumentName*.

### <a name="remarks"></a>Notes

Chaque nom de document a un mappage un-à-un avec un nom de fichier d’enregistrement automatique.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a> CDataRecoveryHandler::GetAutosaveInterval

Retourne l’intervalle entre les tentatives d’enregistrement automatique.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de millisecondes entre les tentatives d’enregistrement automatique.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a> CDataRecoveryHandler::GetAutosavePath

Retourne le chemin d’accès des fichiers enregistrés de façon automatique.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Valeur renvoyée

Emplacement de stockage des documents enregistrés.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a> CDataRecoveryHandler::GetDocumentListName

Récupère le nom du document à partir d’un `CDocument` objet.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers un `CDocument` . `GetDocumentListName` Récupère le nom du document à partir de ce `CDocument` .

### <a name="return-value"></a>Valeur renvoyée

Nom du document à partir de *pDocument*.

### <a name="remarks"></a>Notes

`CDataRecoveryHandler`Utilise le nom du document comme clé dans *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*et *m_mapDocNameToRestoreBool*. Ces paramètres permettent au `CDataRecoveryHandler` de surveiller les `CDocument` objets, le nom du fichier d’enregistrement automatique et les paramètres d’enregistrement automatique.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a> CDataRecoveryHandler::GetNormalDocumentTitle

Récupère le titre normal pour le document spécifié.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers un `CDocument` .

### <a name="return-value"></a>Valeur renvoyée

Titre normal pour le document spécifié.

### <a name="remarks"></a>Notes

Le titre normal d’un document est généralement le nom de fichier du document sans le chemin d’accès. Il s’agit du titre dans le champ **nom de fichier** de la boîte de dialogue **Enregistrer sous** .

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a> CDataRecoveryHandler::GetRecoveredDocumentTitle

Crée et retourne le titre du document récupéré.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Paramètres

*strDocumentTitle*<br/>
dans Titre normal du document.

### <a name="return-value"></a>Valeur renvoyée

Titre du document récupéré.

### <a name="remarks"></a>Notes

Par défaut, le titre récupéré d’un document est le titre normal avec **[récupéré]** ajouté à celui-ci. Le titre récupéré s’affiche lorsque l’utilisateur `CDataRecoveryHandler` interroge l’utilisateur pour restaurer des documents enregistrés de façon automatique.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a> CDataRecoveryHandler::GetRestartIdentifier

Récupère l’identificateur de redémarrage unique pour l’application.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur de redémarrage unique.

### <a name="remarks"></a>Notes

L’identificateur de redémarrage est unique pour chaque exécution de l’application.

`CDataRecoveryHandler`Stocke des informations dans le registre concernant les documents actuellement ouverts. Quand le gestionnaire de redémarrage quitte une application et la redémarre, elle fournit l’identificateur de redémarrage à `CDataRecoveryHandler` . `CDataRecoveryHandler`Utilise l’identificateur de redémarrage pour récupérer la liste des documents précédemment ouverts. Cela permet `CDataRecoveryHandler` à d’essayer de rechercher et de restaurer des fichiers enregistrés de manière automatique.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a> CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Indique si `CDataRecoveryHandler` effectue un enregistrement automatique sur la boucle inactive en cours.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE indique les `CDataRecoveryHandler` sauvegardes automatique sur la boucle active en cours ; FALSe indique qu’il ne l’est pas.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a> CDataRecoveryHandler::GetShutdownByRestartManager

Indique si le gestionnaire de redémarrage a entraîné la fermeture de l’application.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE indique que le gestionnaire de redémarrage a entraîné la fermeture de l’application ; FALSe indique qu’il ne l’a pas fait.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a> CDataRecoveryHandler :: Initialize

Initialise la `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’initialisation est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le processus d’initialisation charge le chemin d’accès pour le stockage des fichiers d’enregistrement automatique à partir du Registre. Si la `Initialize` méthode ne peut pas trouver ce répertoire ou si le chemin d’accès est null, `Initialize` échoue et retourne `FALSE` .

Utilisez [CDataRecoveryHandler :: SetAutosavePath](#setautosavepath) pour modifier le chemin d’enregistrement automatique une fois que votre application a initialisé le `CDataRecoveryHandler` .

La `Initialize` méthode démarre également un minuteur pour surveiller à quel moment la prochaine sauvegarde automatique se produit. Utilisez [CDataRecoveryHandler :: SetAutosaveInterval](#setautosaveinterval) pour modifier l’intervalle d’enregistrement automatique une fois que votre application a initialisé le `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a> CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Affiche une boîte de dialogue à l’utilisateur pour chaque document `CDataRecoveryHandler` enregistré. La boîte de dialogue détermine si l’utilisateur souhaite restaurer le document enregistré de façon automatique.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Notes

Si votre application est au format Unicode, cette méthode affiche un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) à l’utilisateur. Dans le cas contraire, l’infrastructure utilise [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) pour interroger l’utilisateur.

Une fois que `QueryRestoreAutosavedDocuments` rassemble toutes les réponses de l’utilisateur, il stocke les informations dans la variable membre *m_mapDocNameToRestoreBool*. Cette méthode ne restaure pas les documents enregistrés de façon automatique.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a> CDataRecoveryHandler::ReadOpenDocumentList

Charge la liste des documents ouverts à partir du Registre.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE indique que `ReadOpenDocumentList` a chargé les informations d’au moins un document à partir du Registre ; La valeur FALSe indique qu’aucune information de document n’a été chargée.

### <a name="remarks"></a>Notes

Cette fonction charge les informations du document ouvert à partir du Registre et les stocke dans la variable membre *m_mapDocNameToAutosaveName*.

Une fois `ReadOpenDocumentList` toutes les données chargées, les informations du document sont supprimées du Registre.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a> CDataRecoveryHandler::RemoveDocumentInfo

Supprime le document fourni de la liste des documents ouverts.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers le document à supprimer.

### <a name="return-value"></a>Valeur renvoyée

TRUE si *pDocument* a été supprimé de la liste ; FALSe si une erreur s’est produite.

### <a name="remarks"></a>Notes

Lorsque l’utilisateur ferme un document, le Framework utilise cette méthode pour le supprimer de la liste des documents ouverts.

Si `RemoveDocumentInfo` ne peut pas trouver *pDocument* dans la liste des documents ouverts, il ne fait rien et retourne la valeur true.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être défini dans *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a> CDataRecoveryHandler::ReopenPreviousDocuments

Ouvre les documents précédemment ouverts.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si au moins un document a été ouvert ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode ouvre l’enregistrement le plus récent des documents précédemment ouverts. Si un document n’a pas été enregistré ou enregistré automatiquement, `ReopenPreviousDocuments` ouvre un document vide basé sur le modèle de ce type de fichier.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être défini dans *m_dwRestartManagerSupportFlags*. Si ce paramètre n’est pas défini, `ReopenPreviousDocuments` ne fait rien et retourne false.

Si aucun document n’est stocké dans la liste des documents précédemment ouverts, `ReopenPreviousDocuments` ne fait rien et retourne false.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a> CDataRecoveryHandler::RestoreAutosavedDocuments

Restaure les documents enregistrés de façon automatique en fonction de l’entrée de l’utilisateur.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode restaure correctement les documents.

### <a name="remarks"></a>Notes

Cette méthode appelle [CDataRecoveryHandler :: QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) pour déterminer les documents que l’utilisateur souhaite restaurer. Si un utilisateur décide de ne pas restaurer un document enregistré de façon automatique, `RestoreAutosavedDocuments` supprime le fichier d’enregistrement automatique. Sinon, `RestoreAutosavedDocuments` remplace le document ouvert par la version enregistrée automatique.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES ou AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES doivent être définis dans `m_dwRestartManagerSupportFlags` .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a> CDataRecoveryHandler::SaveOpenDocumentList

Enregistre la liste actuelle des documents ouverts dans le Registre Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE s’il n’y a aucun document ouvert à enregistrer ou s’il a été enregistré avec succès. FALSe s’il existe des documents à enregistrer dans le registre, mais ils n’ont pas été enregistrés, car une erreur s’est produite.

### <a name="remarks"></a>Notes

Le gestionnaire de redémarrage appelle `SaveOpenDocumentList` lorsque l’application se ferme de manière inattendue ou lorsqu’elle quitte une mise à niveau. Lorsque l’application redémarre, elle utilise [CDataRecoveryHandler :: ReadOpenDocumentList](#readopendocumentlist) pour récupérer la liste des documents ouverts.

Cette méthode enregistre uniquement la liste des documents ouverts. La méthode [CDataRecoveryHandler :: AutosaveDocumentInfo](#autosavedocumentinfo) est chargée d’enregistrer les documents eux-mêmes.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a> CDataRecoveryHandler::SetAutosaveInterval

Définit l’intervalle de temps entre les cycles d’enregistrement automatique, en millisecondes.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Paramètres

*nAutosaveInterval*<br/>
dans Nouvel intervalle d’enregistrement automatique en millisecondes.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a> CDataRecoveryHandler::SetAutosavePath

Définit le répertoire où sont stockés les fichiers enregistrés.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Paramètres

*strAutosavePath*\
dans Chemin d’accès où sont stockés les fichiers d’enregistrement automatique.

### <a name="remarks"></a>Notes

La modification du répertoire d’enregistrement automatique ne déplace pas les fichiers actuellement enregistrés.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a> CDataRecoveryHandler::SetRestartIdentifier

Définit l’identificateur de redémarrage unique pour cette instance du `CDataRecoveryHandler` .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Paramètres

*strRestartIdentifier*\
dans Identificateur unique du gestionnaire de redémarrage.

### <a name="remarks"></a>Notes

Le gestionnaire de redémarrage enregistre des informations sur les documents ouverts dans le registre. Ces informations sont stockées avec l’identificateur de redémarrage unique comme clé. Étant donné que l’identificateur de redémarrage est unique pour chaque instance d’une application, plusieurs instances d’une application peuvent se fermer de manière inattendue et le gestionnaire de redémarrage peut récupérer chacune d’elles.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a> CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Définit si `CDataRecoveryHandler` enregistre les informations du document ouvert dans le Registre Windows pendant le cycle d’inactivité actuel.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Paramètres

*bSaveOnIdle*\
dans TRUE pour enregistrer les informations du document pendant le cycle d’inactivité actuel ; FALSe pour ne pas effectuer d’enregistrement.

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a> CDataRecoveryHandler::SetShutdownByRestartManager

Définit si la sortie précédente de l’application a été provoquée par le gestionnaire de redémarrage.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Paramètres

*bShutdownByRestartManager*\
dans TRUE pour indiquer que le gestionnaire de redémarrage a entraîné la fermeture de l’application ; FALSe pour indiquer que l’application s’est fermée pour une autre raison.

### <a name="remarks"></a>Notes

Le Framework se comporte différemment selon que la sortie précédente était inattendue ou qu’elle a été initialisée par le gestionnaire de redémarrage.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a> CDataRecoveryHandler::UpdateDocumentInfo

Met à jour les informations d’un document, car l’utilisateur l’a enregistré.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

*pDocument*\
dans Pointeur vers le document enregistré.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode a supprimé le document enregistré et mis à jour les informations du document ; FALSe si une erreur s’est produite.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur enregistre un document, l’application supprime le fichier enregistré automatique, car il n’est plus nécessaire. `UpdateDocumentInfo` supprime le fichier enregistré automatique en appelant [CDataRecoveryHandler :: RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` ajoute ensuite les informations de *pDocument* à la liste des documents actuellement ouverts, car `RemoveDocumentInfo` supprime ces informations, mais le document enregistré est toujours ouvert.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être défini dans *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Procédure : ajouter la prise en charge du gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md)
