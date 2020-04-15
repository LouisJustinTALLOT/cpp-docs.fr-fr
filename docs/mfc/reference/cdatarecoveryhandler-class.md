---
title: Classe CDataRecoveryHandler
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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321933"
---
# <a name="cdatarecoveryhandler-class"></a>Classe CDataRecoveryHandler

L’autosaves `CDataRecoveryHandler` documents et les restaure si une application sort de façon inattendue.

## <a name="syntax"></a>Syntaxe

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Construit un objet `CDataRecoveryHandler`.|

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Autosaves chaque fichier `CDataRecoveryHandler` enregistré auprès de la classe.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Autosaves le document spécifié.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Ajoute un document à la liste des documents ouverts.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Supprime tous les fichiers autosavés actuels.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Supprime le fichier autosaved spécifié.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Génère le nom d’un fichier autosave associé au nom fourni du fichier document.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Retourne l’intervalle entre les essais autosave.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Retourne le chemin des fichiers autosavés.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Récupère le nom du `CDocument` document à partir d’un objet.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Récupère le titre normal pour le document spécifié.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crée et renvoie le titre du document récupéré.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Récupère l’identifiant de redémarrage unique pour l’application.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indique si `CDataRecoveryHandler` l’exécute une autosave sur la boucle de ralenti actuelle.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indique si le gestionnaire de redémarrage a causé la sortie de l’application.|
|[CDataRecoveryHandler::Initialize](#initialize)|Initialise la `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Affiche une boîte de dialogue à l’utilisateur pour chaque document que l’autosavé. `CDataRecoveryHandler` La boîte de dialogue détermine si l’utilisateur veut restaurer le document autosavé.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Charge la liste des documents ouverts à partir du registre.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Supprime le document fourni de la liste des documents ouverts.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Ouvre les documents précédemment ouverts.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaure les documents autosavés en fonction de l’entrée de l’utilisateur.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Enregistre la liste actuelle des documents ouverts au registre Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Définit le temps entre les cycles autosave en millisecondes.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Définit l’annuaire où les fichiers autosavés sont stockés.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Définit l’identifiant de redémarrage `CDataRecoveryHandler`unique pour cet exemple de la .|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Définit si `CDataRecoveryHandler` l’enregistrement des informations de document ouvertes au registre Windows pendant le cycle de ralenti actuel.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Définit si la sortie précédente de l’application a été causée par le gestionnaire de redémarrage.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Mise à jour des informations d’un document parce que l’utilisateur l’a enregistré.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Indique si le gestionnaire de récupération de données rouvre des documents précédemment ouverts.|
|m_bSaveDocumentInfoOnIdle|Indique si le gestionnaire de récupération de données autosave les documents sur la boucle de ralenti suivante.|
|m_bShutdownByRestartManager|Indique si le gestionnaire de redémarrage provoque la sortie de l’application.|
|m_dwRestartManagerSupportFlags|Drapeaux indiquant le support que le gestionnaire de redémarrage fournit pour l’application.|
|m_lstAutosavesToDelete|Une liste de fichiers autosavisés qui n’ont pas été supprimés lorsque les documents originaux ont été fermés. Lorsque l’application sort, le gestionnaire de redémarrage retries suppression des fichiers.|
|m_mapDocNameToAutosaveName|Une carte des noms de documents aux noms de fichiers autosavés.|
|m_mapDocNameToDocumentPtr|Une carte des noms de documents aux pointeurs [CDocument.](../../mfc/reference/cdocument-class.md)|
|m_mapDocNameToRestoreBool|Une carte des noms du document à un paramètre Boolean qui indique s’il faut restaurer le document autosavé.|
|m_mapDocumentPtrToDocName|Une carte `CDocument` des pointeurs aux noms du document.|
|m_mapDocumentPtrToDocTitle|Une carte `CDocument` des pointeurs aux titres de documents. Ces titres sont utilisés pour enregistrer des fichiers.|
|m_nAutosaveInterval|Temps en millisecondes entre les autosaves.|
|m_nTimerID|L’identifiant pour la minuterie autosave.|
|m_strAutosavePath|L’endroit où les documents autosavés sont stockés.|
|m_strRestartIdentifier|La représentation de chaîne d’un GUID pour le gestionnaire de redémarrage.|

## <a name="remarks"></a>Notes

Le gestionnaire de `CDataRecoveryHandler` redémarrage utilise la classe pour garder une trace de tous les documents ouverts et pour les éviter au besoin. Pour activer l’autosave, utilisez la méthode [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) méthode. Cette méthode `CDataRecoveryHandler` dirige l’exécution d’une autosave sur la boucle de ralenti suivante. Le gestionnaire `SetSaveDocumentInfoOnIdle` de `CDataRecoveryHandler` redémarrage appelle quand le doit effectuer un autosave.

Toutes les méthodes `CDataRecoveryHandler` de la classe sont virtuelles. Remplacez les méthodes de cette classe pour créer votre propre gestionnaire de récupération de données personnalisé. À moins que vous ne créiez votre propre gestionnaire de récupération de données ou que vous ne redémarrez pas, n’instantanéisez pas un CDataRecoveryHandler. La [classe CWinApp](../../mfc/reference/cwinapp-class.md) crée un `CDataRecoveryHandler` objet au besoin.

Avant de pouvoir `CDataRecoveryHandler` utiliser un objet, vous devez appeler [CDataRecoveryHandler::Initialize](#initialize).

Parce `CDataRecoveryHandler` que la classe est étroitement `CDataRecoveryHandler` liée au `m_dwRestartManagerSupportFlags`gestionnaire de redémarrage, dépend du paramètre global . Ce paramètre détermine les autorisations du gestionnaire de redémarrage et comment il interagit avec votre application. Pour intégrer le gestionnaire de redémarrage dans `m_dwRestartManagerSupportFlags` une application existante, vous devez attribuer la valeur appropriée dans le constructeur de votre application principale. Pour plus d’informations sur la façon d’utiliser le gestionnaire de redémarrage, voir [Comment : Ajouter le support de gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Spécifications

**En-tête:** afxdatarecovery.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo

Autosaves chaque fichier `CDataRecoveryHandler` enregistré auprès de la classe.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Valeur de retour

VRAI si `CDataRecoveryHandler` le enregistré tous les documents; FALSE si un document n’a pas été enregistré.

### <a name="remarks"></a>Notes

Cette méthode renvoie VRAI s’il n’y a pas de documents qui doivent être enregistrés. Il renvoie également TRUE sans enregistrer de `CWinApp` `CDocManager` documents si la récupération de l’application ou pour l’application génère une erreur.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL doit être `m_dwRestartManagerSupportFlags`mis en . Pour plus d’informations, voir [Comment : Ajouter le support de gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo

Autosaves le document spécifié.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur `CDocument` à l’enregistrer.|
|*bResetModifiedFlag (en)*|[dans] TRUE indique `CDataRecoveryHandler` que le *pDocument* considère qu’il est modifié; FALSE indique que le cadre considère *le pDocument* comme non modifié. Consultez la section Remarques pour plus d’informations sur l’effet de ce drapeau.|

### <a name="return-value"></a>Valeur de retour

VRAI si les drapeaux appropriés sont réglés `CDocument` et *pDocument* est un objet valide.

### <a name="remarks"></a>Notes

Chaque `CDocument` objet a un drapeau qui indique s’il a changé depuis le dernier enregistrement. Utilisez [CDocument:IsModified](../../mfc/reference/cdocument-class.md#ismodified) pour déterminer l’état de ce drapeau. Si `CDocument` a pas changé depuis `AutosaveDocumentInfo` le dernier enregistrement, supprime les fichiers autosavés pour ce document. Si un document a changé depuis le dernier enregistrement, le fermer incite l’utilisateur à enregistrer le document avant la fermeture.

> [!NOTE]
> L’utilisation *de bResetModifiedFlag* pour modifier l’état du document pour non modifié peut faire perdre à l’utilisateur des données nonavées. Si le cadre considère un document non modifié, le fermer ne pousse pas l’utilisateur à enregistrer.

Cette méthode jette une exception avec la macro [ASSERT](diagnostic-services.md#assert) si `CDocument` *pDocument n’est* pas un objet valide.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL doit être mis en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler

Construit un objet `CDataRecoveryHandler`.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*dwRestartManagerSupportFlags dwRestartManagerSupportFlags*|[dans] Indique quelles options du gestionnaire de redémarrage sont prises en charge.|
|*nAutosaveInterval*|[dans] Le temps entre les autosaves. Ce paramètre est en millisecondes.|

### <a name="remarks"></a>Notes

Le cadre MFC `CDataRecoveryHandler` crée automatiquement un objet pour votre application lorsque vous utilisez l’assistant **Du nouveau projet.** Sauf si vous personnalisez le comportement de récupération `CDataRecoveryHandler` des données ou le gestionnaire de redémarrage, vous ne devez pas créer un objet.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo

Ajoute un document à la liste des documents ouverts.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur `CDocument`à un . Cette méthode crée les `CDocument`informations de document pour cela .|

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie TRUE.

### <a name="remarks"></a>Notes

Cette méthode vérifie si *pDocument* est déjà dans la liste des documents avant d’ajouter le document. Si *pDocument* est déjà dans la liste, cette méthode supprime le fichier autosaved associé à *pDocument*.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART ou AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL doit être mis en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles

Supprime tous les fichiers autosavés actuels.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut renvoie toujours TRUE.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile

Supprime le fichier autosaved spécifié.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*strAutosavedFile (en)*|[dans] Une chaîne qui contient le nom de fichier autosaved.|

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne toujours VRAI.

### <a name="remarks"></a>Notes

Si cette méthode ne peut pas supprimer le fichier autosaved, elle enregistre le nom du fichier dans une liste. Le destructeur pour `CDataRecoveryHandler` les tente de supprimer chaque fichier autosavé spécifié dans cette liste.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName

Génère le nom d’un fichier autosave associé au nom fourni du fichier document.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Paramètres

*strDocumentName (en)*<br/>
[dans] Une chaîne qui contient le nom du document. `GenerateAutosaveFileName`utilise ce nom de document pour générer un nom de fichier autosave correspondant.

### <a name="return-value"></a>Valeur de retour

Le nom de fichier autosave généré à partir de *strDocumentName*.

### <a name="remarks"></a>Notes

Chaque nom de document a une cartographie en tête-à-tête avec un nom de fichier autosave.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval

Retourne l’intervalle entre les essais autosave.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de millisecondes entre les essais autosave.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath

Retourne le chemin des fichiers autosavés.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Valeur de retour

L’endroit où les documents autosavés sont stockés.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName

Récupère le nom du `CDocument` document à partir d’un objet.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur `CDocument`à un . `GetDocumentListName`récupère le nom du `CDocument`document de cette .|

### <a name="return-value"></a>Valeur de retour

Le nom du document de *pDocument*.

### <a name="remarks"></a>Notes

Le `CDataRecoveryHandler` document utilise le nom du document comme clé dans *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*, et *m_mapDocNameToRestoreBool*. Ces paramètres `CDataRecoveryHandler` permettent `CDocument` de surveiller les objets, le nom du fichier autosave et les paramètres autosave.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle

Récupère le titre normal pour le document spécifié.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur `CDocument`à un .|

### <a name="return-value"></a>Valeur de retour

Le titre normal pour le document spécifié.

### <a name="remarks"></a>Notes

Le titre normal d’un document est généralement le nom de fichier du document sans le chemin. C’est le titre dans le champ **de nom de fichier** de la boîte de dialogue Save **As.**

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle

Crée et renvoie le titre du document récupéré.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Paramètres

*strDocumentTitle (en)*<br/>
[dans] Le titre normal pour le document.

### <a name="return-value"></a>Valeur de retour

Le titre de document récupéré.

### <a name="remarks"></a>Notes

Par défaut, le titre récupéré d’un document est le titre normal avec **[récupéré]** joint à elle. Le titre récupéré s’affiche `CDataRecoveryHandler` à l’utilisateur lorsque l’utilisateur demande de restaurer les documents autosavés.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier

Récupère l’identifiant de redémarrage unique pour l’application.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant de redémarrage unique.

### <a name="remarks"></a>Notes

L’identifiant de redémarrage est unique pour chaque exécution de l’application.

Les `CDataRecoveryHandler` magasins de l’information dans le registre sur les documents actuellement ouverts. Lorsque le gestionnaire de redémarrage quitte une application et la `CDataRecoveryHandler`redémarre, il fournit l’identifiant de redémarrage à la . L’utilisation `CDataRecoveryHandler` de l’identifiant de redémarrage pour récupérer la liste des documents précédemment ouverts. Cela permet `CDataRecoveryHandler` d’essayer de trouver et de restaurer les fichiers autosavés.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Indique si `CDataRecoveryHandler` l’exécute une autosave sur la boucle de ralenti actuelle.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE indique `CDataRecoveryHandler` les autosaves sur la boucle de ralenti actuelle; FALSE indique que ce n’est pas le cas.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager

Indique si le gestionnaire de redémarrage a causé la sortie de l’application.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE indique que le gestionnaire de redémarrage a causé la sortie de l’application; FALSE indique qu’il ne l’a pas fait.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CDataRecoveryHandler::Initialize

Initialise la `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’initialisation est réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Le processus d’initialisation charge le chemin pour stocker les fichiers autosave du registre. Si `Initialize` la méthode ne peut pas trouver ce `Initialize` répertoire `FALSE`ou si le chemin est NULL, échoue et retourne .

Utilisez [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) pour changer le chemin autosave `CDataRecoveryHandler`après que votre application initialise le .

La `Initialize` méthode commence également une minuterie à surveiller lorsque la prochaine autosave se produit. Utilisez [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) pour changer l’intervalle d’autosave après que votre application initialise le `CDataRecoveryHandler`.

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Affiche une boîte de dialogue à l’utilisateur pour chaque document que l’autosavé. `CDataRecoveryHandler` La boîte de dialogue détermine si l’utilisateur veut restaurer le document autosavé.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Notes

Si votre application est Unicode, cette méthode affiche un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) à l’utilisateur. Dans le cas contraire, le cadre utilise [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) pour interroger l’utilisateur.

Après `QueryRestoreAutosavedDocuments` avoir recueilli toutes les réponses de l’utilisateur, il stocke les informations dans la variable du membre *m_mapDocNameToRestoreBool*. Cette méthode ne restaure pas les documents autosavés.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList

Charge la liste des documents ouverts à partir du registre.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Valeur de retour

TRUE indique `ReadOpenDocumentList` que l’information chargée d’au moins un document du registre; FALSE indique qu’aucune information sur les documents n’a été chargée.

### <a name="remarks"></a>Notes

Cette fonction charge les informations de document ouvert du registre et les stocke dans la variable *membre m_mapDocNameToAutosaveName*.

Après `ReadOpenDocumentList` avoir chargé toutes les données, il supprime les informations de document du registre.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo

Supprime le document fourni de la liste des documents ouverts.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur sur le document à supprimer.|

### <a name="return-value"></a>Valeur de retour

VRAI si *pDocument* a été retiré de la liste; FALSE en cas d’erreur.

### <a name="remarks"></a>Notes

Lorsque l’utilisateur ferme un document, le cadre utilise cette méthode pour le supprimer de la liste des documents ouverts.

S’il `RemoveDocumentInfo` ne peut pas trouver *pDocument* dans la liste des documents ouverts, il ne fait rien et retourne VRAI.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être mis en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments

Ouvre les documents précédemment ouverts.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Valeur de retour

VRAI si au moins un document a été ouvert; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode ouvre l’enregistrement le plus récent des documents précédemment ouverts. Si un document n’a pas `ReopenPreviousDocuments` été enregistré ou autosavé, ouvre un document vierge basé sur le modèle pour ce type de fichier.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être mis en *m_dwRestartManagerSupportFlags*. Si ce paramètre `ReopenPreviousDocuments` n’est pas défini, ne fait rien et renvoie FALSE.

S’il n’y a pas de `ReopenPreviousDocuments` documents stockés dans la liste des documents précédemment ouverts, ne fait rien et renvoie FALSE.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments

Restaure les documents autosavés en fonction de l’entrée de l’utilisateur.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode restaure avec succès les documents.

### <a name="remarks"></a>Notes

Cette méthode appelle [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) pour déterminer quels documents l’utilisateur veut restaurer. Si un utilisateur décide de ne pas `RestoreAutosavedDocuments` restaurer un document autosavé, supprime le fichier autosave. Dans `RestoreAutosavedDocuments` le cas contraire, remplace le document ouvert par la version autosavée.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES ou AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES doit être `m_dwRestartManagerSupportFlags`mis en .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList

Enregistre la liste actuelle des documents ouverts au registre Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il n’y a pas de documents ouverts à enregistrer ou s’ils ont été sauvegardés avec succès. FALSE s’il y a des documents à enregistrer au registre, mais ils n’ont pas été enregistrés parce qu’une erreur s’est produite.

### <a name="remarks"></a>Notes

Le gestionnaire `SaveOpenDocumentList` de redémarrage appelle lorsque l’application sort de façon inattendue ou lorsqu’elle quitte pour une mise à niveau. Lorsque l’application redémarre, elle utilise [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) pour récupérer la liste des documents ouverts.

Cette méthode n’enregistre que la liste des documents ouverts. La méthode [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) est responsable de l’enregistrement des documents eux-mêmes.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval

Définit le temps entre les cycles autosave en millisecondes.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Paramètres

*nAutosaveInterval*<br/>
[dans] Le nouvel intervalle autosave en millisecondes.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath

Définit l’annuaire où les fichiers autosavés sont stockés.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*strAutosavePath (en)*|[dans] Le chemin où les fichiers autosave sont stockés.|

### <a name="remarks"></a>Notes

Changer le répertoire autosave ne déplace pas actuellement les fichiers autosavés.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier

Définit l’identifiant de redémarrage `CDataRecoveryHandler`unique pour cet exemple de la .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*strRestartIdentifier*|[dans] L’identifiant unique pour le gestionnaire de redémarrage.|

### <a name="remarks"></a>Notes

Le gestionnaire de redémarrage enregistre des informations sur les documents ouverts du registre. Ces informations sont stockées avec l’identifiant de redémarrage unique comme clé. Étant donné que l’identifiant de redémarrage est unique pour chaque instance d’une application, plusieurs instances d’une application peuvent sortir de façon inattendue et le gestionnaire de redémarrage peut récupérer chacun d’eux.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Définit si `CDataRecoveryHandler` l’enregistrement des informations de document ouvertes au registre Windows pendant le cycle de ralenti actuel.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*bSaveOnIdle*|[dans] VRAI pour enregistrer l’information sur les documents pendant le cycle inactif actuel; FALSE de ne pas effectuer un enregistrement.|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager

Définit si la sortie précédente de l’application a été causée par le gestionnaire de redémarrage.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*bShutdownByRestartManager*|[dans] VRAI pour indiquer que le gestionnaire de redémarrage a causé la sortie de l’application; FALSE pour indiquer que la demande est sortie pour une autre raison.|

### <a name="remarks"></a>Notes

Le cadre se comporte différemment en fonction de la question de savoir si la sortie précédente était inattendue ou si elle a été initiée par le gestionnaire du redémarrage.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo

Mise à jour des informations d’un document parce que l’utilisateur l’a enregistré.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pDocument*|[dans] Un pointeur vers le document enregistré.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode a supprimé le document autosavisé et mis à jour les informations du document; FALSE en cas d’erreur.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur enregistre un document, l’application supprime le fichier autosavé parce qu’il n’est plus nécessaire. `UpdateDocumentInfo`supprime le fichier autosaved en appelant [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`ajoute ensuite les informations de *pDocument* à `RemoveDocumentInfo` la liste des documents actuellement ouverts parce que supprime ces informations, mais le document enregistré est toujours ouvert.

Pour utiliser cette méthode, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES doit être mis en *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Guide pratique pour ajouter la prise en charge du Gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md)
