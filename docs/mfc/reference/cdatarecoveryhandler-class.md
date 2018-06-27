---
title: Classe de CDataRecoveryHandler | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73596ec5ec9f17b2007a6816bbe0ab90b1463430
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957102"
---
# <a name="cdatarecoveryhandler-class"></a>Classe de CDataRecoveryHandler
Le `CDataRecoveryHandler` enregistre automatiquement les documents et les restaure si une application se ferme de façon inattendue.  
  
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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Enregistre automatiquement chaque fichier enregistré avec le `CDataRecoveryHandler` classe.|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Enregistre automatiquement le document spécifié.|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Ajoute un document à la liste des documents ouverts.|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Supprime tous les fichiers enregistrée automatiquement en cours.|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Supprime le fichier enregistré automatiquement spécifié.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Génère le nom d’un fichier d’enregistrement automatique associé au nom de fichier du document fourni.|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Retourne l’intervalle entre les tentatives d’enregistrement automatique.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Retourne le chemin d’accès des fichiers enregistrée automatiquement.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Récupère le nom du document à partir d’un `CDocument` objet.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Récupère le titre normal pour le document spécifié.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crée et retourne le titre du document récupéré.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Récupère l’identificateur unique de redémarrage de l’application.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indique si le `CDataRecoveryHandler` effectue un enregistrement automatique sur la boucle inactive en cours.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indique si le Gestionnaire de redémarrage a entraîné la fermeture de l’application.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Initialise la `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Affiche une boîte de dialogue à l’utilisateur pour chaque document la `CDataRecoveryHandler` enregistrée automatiquement. La boîte de dialogue détermine si l’utilisateur souhaite restaurer le document enregistré automatiquement.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Charge la liste des documents ouverts à partir du Registre.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Supprime le document fourni à partir de la liste des documents ouverts.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Ouvre les documents précédemment ouverts.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaure les documents enregistrée automatiquement en fonction de l’entrée d’utilisateur.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Enregistre la liste actuelle des documents ouverts dans le Registre Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Définit le délai entre les cycles d’enregistrement automatique en millisecondes.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Définit le répertoire où sont stockés les fichiers enregistrée automatiquement.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Définit l’identificateur unique de redémarrage pour cette instance de la `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Définit si la `CDataRecoveryHandler` enregistre les informations de document ouvert dans le Registre Windows au cours du cycle d’inactivité en cours.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Définit si la sortie précédente de l’application a été provoquée par le Gestionnaire de redémarrage.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Met à jour les informations pour un document, car l’utilisateur enregistré.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Indique si le Gestionnaire de récupération de données est rouverte documents précédemment ouverts.|  
|m_bSaveDocumentInfoOnIdle|Indique si le Gestionnaire de récupération données enregistre automatiquement des documents sur la boucle inactive suivante.|  
|m_bShutdownByRestartManager|Indique si le Gestionnaire de redémarrage entraîne la fermeture de l’application.|  
|m_dwRestartManagerSupportFlags|Fournit des indicateurs qui indiquent ce qui prend en charge le Gestionnaire de redémarrage de l’application.|  
|m_lstAutosavesToDelete|Une liste de fichiers enregistrée automatiquement qui n’ont pas été supprimés lorsque les documents d’origine ont été fermés. Lorsque l’application s’arrête, les tentatives de gestionnaire de redémarrage suppression des fichiers.|  
|m_mapDocNameToAutosaveName|Un mappage des noms de document pour les noms de fichiers enregistrée automatiquement.|  
|m_mapDocNameToDocumentPtr|Un mappage des noms de document à la [CDocument](../../mfc/reference/cdocument-class.md) pointeurs.|  
|m_mapDocNameToRestoreBool|Un mappage des noms de document à un paramètre booléen qui indique s’il faut restaurer le document enregistré automatiquement.|  
|m_mapDocumentPtrToDocName|Un mappage de la `CDocument` des pointeurs vers les noms de document.|  
|m_mapDocumentPtrToDocTitle|Un mappage de la `CDocument` des pointeurs vers les titres de document. Ces noms sont utilisés pour l’enregistrement de fichiers.|  
|m_nAutosaveInterval|Durée en millisecondes entre enregistre automatiquement.|  
|m_nTimerID|Identificateur de la minuterie d’enregistrement automatique.|  
|m_strAutosavePath|L’emplacement où sont stockés les documents enregistrée automatiquement.|  
|m_strRestartIdentifier|La représentation de chaîne d’un GUID pour le Gestionnaire de redémarrage.|  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de redémarrage utilise la `CDataRecoveryHandler` classe conserver assurer le suivi de tous les documents ouverts et enregistrement automatique si nécessaire. Pour activer cette fonctionnalité, utilisez le [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) (méthode). Cette méthode dirige le `CDataRecoveryHandler` pour effectuer un enregistrement automatique sur la boucle inactive suivante. Les appels de gestionnaire de redémarrage `SetSaveDocumentInfoOnIdle` lorsque le `CDataRecoveryHandler` doit effectuer un enregistrement automatique.  
  
 Toutes les méthodes de la `CDataRecoveryHandler` classe sont virtuelles. Substituez les méthodes dans cette classe pour créer votre propre gestionnaire de récupération de données personnalisé. Sauf si vous créez votre propre gestionnaire de récupération de données ou que vous redémarrez le gestionnaire, n’instanciez pas un CDataRecoveryHandler. Le [CWinApp (classe)](../../mfc/reference/cwinapp-class.md) crée un `CDataRecoveryHandler` de l’objet car il est requis.  
  
 Avant de pouvoir utiliser un `CDataRecoveryHandler` de l’objet, vous devez appeler [CDataRecoveryHandler::Initialize](#initialize).  
  
 Étant donné que la `CDataRecoveryHandler` classe est étroitement lié au Gestionnaire de redémarrage, `CDataRecoveryHandler` dépend du paramètre global `m_dwRestartManagerSupportFlags`. Ce paramètre détermine les autorisations du Gestionnaire de redémarrage et leur interaction avec votre application. Pour intégrer le Gestionnaire de redémarrage dans une application existante, vous devez attribuer `m_dwRestartManagerSupportFlags` la valeur appropriée dans le constructeur de votre application principale. Pour plus d’informations sur la façon d’utiliser le Gestionnaire de redémarrage, consultez [Comment : ajouter prise en charge du Gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Enregistre automatiquement chaque fichier enregistré avec le `CDataRecoveryHandler` classe.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le `CDataRecoveryHandler` enregistré tous les documents ; `FALSE` si n’importe quel document n’a pas été enregistré.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne `TRUE` si aucun document doit être enregistré. Il renvoie également `TRUE` sans enregistrer les documents si la récupération de la `CWinApp` ou `CDocManager` pour l’application génère une erreur.  
  
 Pour utiliser cette méthode, soit `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` ou `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` doit être définie dans `m_dwRestartManagerSupportFlags`. Consultez [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) pour plus d’informations.  
  
##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo  
 Enregistre automatiquement le document spécifié.  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Un pointeur vers le `CDocument` à enregistrer.|  
|[in] *bResetModifiedFlag*|`TRUE` Indique que le `CDataRecoveryHandler` considère *pDocument* à être modifié ; `FALSE` indique que le framework prend en compte *pDocument* à être modifié. Consultez la section Notes pour plus d’informations sur l’impact de cet indicateur.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si les indicateurs appropriés sont définis et *pDocument* n’est valide `CDocument` objet.  
  
### <a name="remarks"></a>Notes  
 Chaque `CDocument` objet a un indicateur qui indique si elle a été modifié depuis le dernier enregistrement. Utilisez [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) pour déterminer l’état de cet indicateur. Si un `CDocument` n’a pas changé depuis le dernier enregistrement, `AutosaveDocumentInfo` supprime tous les fichiers enregistrée automatiquement pour ce document. Si un document a changé depuis le dernier enregistrement, fermeture invite l’utilisateur d’enregistrer le document avant la fermeture.  
  
> [!NOTE]
>  À l’aide de *bResetModifiedFlag* pour modifier l’état du document à non modifié l’utilisateur risque de perdre des données non enregistrées. Si le framework considère comme un document non modifié, sa fermeture n’affiche aucune invite l’utilisateur à enregistrer.  
  
 Cette méthode lève une exception avec le [ASSERT](diagnostic-services.md#assert) macro si *pDocument* n’est pas valide `CDocument` objet.  
  
 Pour utiliser cette méthode, soit `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` ou `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` doit être définie dans *m_dwRestartManagerSupportFlags*.   
  
##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler  
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
|[in] *dwRestartManagerSupportFlags*|Indique les options du Gestionnaire de redémarrage sont pris en charge.|  
|[in] *nAutosaveInterval*|Délai entre enregistre automatiquement. Ce paramètre est exprimée en millisecondes.|  
  
### <a name="remarks"></a>Notes  
 L’infrastructure MFC crée automatiquement un `CDataRecoveryHandler` objet pour votre application lorsque vous utilisez la **nouveau projet** Assistant. Sauf si vous personnalisez le comportement de récupération de données ou le Gestionnaire de redémarrage, vous ne devez pas créer un `CDataRecoveryHandler` objet.  
  
  
##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo  
 Ajoute un document à la liste des documents ouverts.  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Un pointeur vers un `CDocument`. Cette méthode crée les informations de document pour ce `CDocument`.|  
  
### <a name="return-value"></a>Valeur de retour  
 L'implémentation par défaut retourne la valeur `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode vérifie si *pDocument* est déjà dans la liste des documents avant d’ajouter le document. Si *pDocument* figure déjà dans la liste, cette méthode supprime le fichier enregistré automatiquement associé *pDocument*.  
  
 Pour utiliser cette méthode, soit `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` ou `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` doit être définie dans *m_dwRestartManagerSupportFlags*. 
  
##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Supprime tous les fichiers enregistrée automatiquement en cours.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation par défaut toujours retourne `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile  
 Supprime le fichier enregistré automatiquement spécifié.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *strAutosavedFile*|Chaîne qui contient le nom du fichier enregistré automatiquement.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation par défaut retournent toujours `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Si cette méthode ne peut pas supprimer le fichier enregistré automatiquement, elle enregistre le nom du fichier dans une liste. Le destructeur de la `CDataRecoveryHandler` tente de supprimer chaque fichier enregistré automatiquement spécifié dans cette liste.  
  
##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName  
 Génère le nom d’un fichier d’enregistrement automatique associé au nom de fichier du document fourni.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *strDocumentName*  
 Chaîne qui contient le nom du document. `GenerateAutosaveFileName` utilise le nom de ce document pour générer un nom de fichier d’enregistrement automatique correspondante.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom de fichier d’enregistrement automatique généré à partir de *strDocumentName*.  
  
### <a name="remarks"></a>Notes  
 Chaque nom de document a un mappage avec un nom de fichier d’enregistrement automatique.  
  
##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval  
 Retourne l’intervalle entre les tentatives d’enregistrement automatique.  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de millisecondes écoulées entre l’enregistrement automatique tente de.  
  
##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath  
 Retourne le chemin d’accès des fichiers enregistrée automatiquement.  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’emplacement où sont stockés les documents enregistrée automatiquement.  
  
##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName  
 Récupère le nom du document à partir d’un `CDocument` objet.  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Un pointeur vers un `CDocument`. `GetDocumentListName` Récupère le nom du document à partir de ce `CDocument`.|  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom du document à partir de *pDocument*.  
  
### <a name="remarks"></a>Notes  
 Le `CDataRecoveryHandler` utilise le nom du document comme clé dans *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*, et *m_mapDocNameToRestoreBool*. Ces paramètres permettent la `CDataRecoveryHandler` pour surveiller `CDocument` objets, le nom de fichier d’enregistrement automatique et les paramètres d’enregistrement automatique.  
  
##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle  
 Récupère le titre normal pour le document spécifié.  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Un pointeur vers un `CDocument`.|  
  
### <a name="return-value"></a>Valeur de retour  
 Le titre normal pour le document spécifié.  
  
### <a name="remarks"></a>Notes  
 Le titre normale d’un document est généralement le nom de fichier du document sans le chemin d’accès. Ceci est le titre dans le **nom de fichier** champ le **Enregistrer sous** boîte de dialogue.  
  
##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle  
 Crée et retourne le titre du document récupéré.  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *strDocumentTitle*  
 Le titre normal pour le document.  
  
### <a name="return-value"></a>Valeur de retour  
 Le titre du document récupéré.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le titre récupéré d’un document est le titre normale avec **[Récupéré]** ajouté à la fin. Le titre récupéré est affiché à l’utilisateur lorsque le `CDataRecoveryHandler` interroge l’utilisateur pour restaurer les documents enregistrée automatiquement.  
  
##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier  
 Récupère l’identificateur unique de redémarrage de l’application.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur unique de redémarrage.  
  
### <a name="remarks"></a>Notes  
 L’identificateur de redémarrage est unique pour chaque exécution de l’application.  
  
 La `CDataRecoveryHandler` stocke les informations dans le Registre sur les documents actuellement ouverts. Lorsque le Gestionnaire de redémarrage ferme une application et le redémarre, il fournit l’identificateur de redémarrage à le `CDataRecoveryHandler`. Le `CDataRecoveryHandler` utilise l’identificateur de redémarrage pour récupérer la liste des documents précédemment ouverts. Cela permet la `CDataRecoveryHandler` pour tenter de rechercher et restaurer des fichiers d’enregistrée automatiquement.  
  
##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Indique si le `CDataRecoveryHandler` effectue un enregistrement automatique sur la boucle inactive en cours.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Indique le `CDataRecoveryHandler` enregistre automatiquement sur la boucle inactive en cours ; `FALSE` indique qu’il n’est pas le cas.  
  
##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager  
 Indique si le Gestionnaire de redémarrage a entraîné la fermeture de l’application.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Indique le Gestionnaire de redémarrage a provoqué l’application à s’arrêter ; `FALSE` indique qu’il n’a pas.  
  
##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize  
 Initialise la `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si l’initialisation a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le processus d’initialisation charge le chemin d’accès pour stocker les fichiers d’enregistrement automatique à partir du Registre. Si le `Initialize` méthode ne peut pas trouver ce répertoire, ou si le chemin d’accès est `NULL`, `Initialize` échoue et retourne `FALSE`.  
  
 Utilisez [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) pour modifier le chemin d’accès de l’enregistrement automatique une fois que votre application a initialisé le `CDataRecoveryHandler`.  
  
 Le `Initialize` méthode démarre également un minuteur pour contrôler le moment où l’enregistrement automatique suivant se produit. Utilisez [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) pour modifier l’intervalle d’enregistrement automatique une fois que votre application a initialisé le `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Affiche une boîte de dialogue à l’utilisateur pour chaque document la `CDataRecoveryHandler` enregistrée automatiquement. La boîte de dialogue détermine si l’utilisateur souhaite restaurer le document enregistré automatiquement.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Notes  
 Si votre application est au format Unicode, cette méthode affiche une [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) à l’utilisateur. Sinon, le framework utilise [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) pour demander à l’utilisateur.  
  
 Après avoir `QueryRestoreAutosavedDocuments` rassemble toutes les réponses de l’utilisateur, elle stocke les informations dans la variable membre *m_mapDocNameToRestoreBool*. Cette méthode ne restaure pas les documents enregistrée automatiquement.  
  
##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList  
 Charge la liste des documents ouverts à partir du Registre.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Indique que `ReadOpenDocumentList` chargé les informations pour au moins un document à partir du Registre ; `FALSE` indique aucune information de document a été chargée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction charge les informations de document ouvert à partir du Registre et les stocke dans la variable membre *m_mapDocNameToAutosaveName*.  
  
 Après avoir `ReadOpenDocumentList` charge toutes les données, il supprime les informations de document à partir du Registre.  
  
##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo  
 Supprime le document fourni à partir de la liste des documents ouverts.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Pointeur vers le document à supprimer.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si *pDocument* a été supprimé de la liste. `FALSE` si une erreur s’est produite.  
  
### <a name="remarks"></a>Notes  
 Lorsque l’utilisateur ferme un document, le framework utilise cette méthode pour le supprimer de la liste des documents ouverts.  
  
 Si `RemoveDocumentInfo` Impossible de trouver *pDocument* dans la liste des documents ouverts, il ne fait rien et retourne `TRUE`.  
  
 Pour utiliser cette méthode, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` doit être définie dans *m_dwRestartManagerSupportFlags*.   
  
##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments  
 Ouvre les documents précédemment ouverts.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si au moins un document a été ouvert ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode ouvre l’enregistrement le plus récent des documents précédemment ouverts. Si un document n’a pas été enregistré ou enregistré automatiquement, `ReopenPreviousDocuments` ouvre un document vide basé sur le modèle pour ce type de fichier.  
  
 Pour utiliser cette méthode, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` doit être définie dans *m_dwRestartManagerSupportFlags*. Si ce paramètre n’est pas défini, `ReopenPreviousDocuments` ne fait rien et retourne `FALSE`.  
  
 Si aucun document stocké dans la liste des documents précédemment ouverts, `ReopenPreviousDocuments` ne fait rien et retourne `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments  
 Restaure les documents enregistrée automatiquement en fonction de l’entrée d’utilisateur.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode restaure correctement les documents.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) pour déterminer les documents de l’utilisateur souhaite restaurer. Si un utilisateur décide de ne pas restaurer un document enregistré automatiquement, `RestoreAutosavedDocuments` supprime le fichier d’enregistrement automatique. Dans le cas contraire, `RestoreAutosavedDocuments` remplace le document ouvert avec la version enregistrée automatiquement.  
  
 Pour utiliser cette méthode, soit `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` ou `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` doit être définie dans `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList  
 Enregistre la liste actuelle des documents ouverts dans le Registre Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si aucun document ouvert pour enregistrer ou s’ils ont été enregistrés avec succès. `FALSE` Si le document à enregistrer dans le Registre, mais ils n’étaient pas enregistrés, car une erreur s’est produite.  
  
### <a name="remarks"></a>Notes  
 Les appels de gestionnaire de redémarrage `SaveOpenDocumentList` lorsque l’application se ferme de façon inattendue ou lorsqu’il se termine pour une mise à niveau. Lorsque l’application redémarre, il utilise [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) pour récupérer la liste des documents ouverts.  
  
 Cette méthode enregistre uniquement la liste des documents ouverts. La méthode [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) est responsable de l’enregistrement des documents eux-mêmes.  
  
##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval  
 Définit le délai entre les cycles d’enregistrement automatique en millisecondes.  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nAutosaveInterval*  
 Le nouvel intervalle d’enregistrement automatique en millisecondes.  
  
##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath  
 Définit le répertoire où sont stockés les fichiers enregistrée automatiquement.  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *strAutosavePath*|Le chemin d’accès où sont stockés les fichiers d’enregistrement automatique.|  
  
### <a name="remarks"></a>Notes  
 Modification du répertoire d’enregistrement automatique ne déplace pas actuellement enregistrée automatiquement les fichiers.  
  
##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier  
 Définit l’identificateur unique de redémarrage pour cette instance de la `CDataRecoveryHandler`.  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *strRestartIdentifier*|Identificateur unique pour le Gestionnaire de redémarrage.|  
  
### <a name="remarks"></a>Notes  
 Le Gestionnaire de redémarrage enregistre des informations sur les documents ouverts dans le Registre. Ces informations sont stockées avec l’identificateur de redémarrage unique comme clé. Étant donné que l’identificateur de redémarrage est unique pour chaque instance d’une application, plusieurs instances d’une application se ferme de façon inattendue et le Gestionnaire de redémarrage peut récupérer chacun d’eux.  
  
##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 Définit si la `CDataRecoveryHandler` enregistre les informations de document ouvert dans le Registre Windows au cours du cycle d’inactivité en cours.  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *bSaveOnIdle*|`TRUE` Pour enregistrer les informations de document au cours du cycle d’inactivité en cours ; `FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager  
 Définit si la sortie précédente de l’application a été provoquée par le Gestionnaire de redémarrage.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *bShutdownByRestartManager*|`TRUE` pour indiquer que le Gestionnaire de redémarrage a provoqué l’application à s’arrêter ; `FALSE` pour indiquer que l’application s’est arrêté pour une autre raison.|  
  
### <a name="remarks"></a>Notes  
 L’infrastructure se comporte différemment selon que la sortie précédente était inattendue ou si elle a été initiée par le Gestionnaire de redémarrage.  
  
##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo  
 Met à jour les informations pour un document, car l’utilisateur enregistré.  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pDocument*|Pointeur vers le document enregistré.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode supprimé le document enregistré automatiquement et mis à jour les informations de document ; `FALSE` si une erreur s’est produite.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un utilisateur enregistre un document, l’application supprime le fichier enregistré automatiquement, car il n’est plus nécessaire. `UpdateDocumentInfo` Supprime le fichier enregistré automatiquement en appelant [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` Ajoute les informations à partir de *pDocument* à la liste des actuellement ouvrir des documents, car `RemoveDocumentInfo` supprime ces informations, mais les documents sont encore ouverts.  
  
 Pour utiliser cette méthode, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` doit être définie dans *m_dwRestartManagerSupportFlags*.   
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Guide pratique pour ajouter la prise en charge du Gestionnaire de redémarrage](../../mfc/how-to-add-restart-manager-support.md)

