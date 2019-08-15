---
title: CAtlServiceModuleT (classe)
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497739"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT (classe)

Cette classe implémente un service.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `CAtlServiceModuleT`.

*nServiceNameID*<br/>
Identificateur de ressource du service.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|Routine du gestionnaire pour le service.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Fournit les paramètres de sécurité par défaut pour le service.|
|[CAtlServiceModuleT::Install](#install)|Installe et crée le service.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Confirme que le service a été installé.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Écrit dans le journal des événements.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Substituez cette méthode pour continuer le service.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Substituez cette méthode pour interroger le service.|
|[CAtlServiceModuleT::OnPause](#onpause)|Substituez cette méthode pour suspendre le service.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Substituez cette méthode pour arrêter le service|
|[CAtlServiceModuleT::OnStop](#onstop)|Substituez cette méthode pour arrêter le service|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Substituez cette méthode pour gérer les demandes inconnues du service|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analyse la ligne de commande et effectue l’inscription si nécessaire.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Cette méthode est appelée juste avant l’entrée dans la boucle de message.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Inscrit le service dans le registre.|
|[CAtlServiceModuleT::Run](#run)|Exécute le service.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Méthode appelée par le gestionnaire de contrôle des services.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Met à jour l’état du service.|
|[CAtlServiceModuleT::Start](#start)|Appelé par `CAtlServiceModuleT::WinMain` lorsque le service démarre.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Arrête et supprime le service.|
|[CAtlServiceModuleT::Unlock](#unlock)|Décrémente le nombre de verrous du service.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Supprime le service du Registre.|
|[CAtlServiceModuleT::WinMain](#winmain)|Cette méthode implémente le code requis pour exécuter le service.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Indicateur spécifiant que le programme s’exécute en tant que service.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Variable membre stockant l’identificateur de thread.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Variable membre stockant un handle vers la structure d’informations d’État pour le service actuel.|
|[CAtlServiceModuleT::m_status](#m_status)|Variable membre stockant la structure d’informations d’État pour le service actuel.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Nom du service en cours d’inscription.|

## <a name="remarks"></a>Notes

`CAtlServiceModuleT`, dérivé de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implémente un module ATL service. `CAtlServiceModuleT`fournit des méthodes pour le traitement de ligne de commande, l’installation, l’inscription et la suppression. Si des fonctionnalités supplémentaires sont requises, ces méthodes et d’autres peuvent être remplacées.

Cette classe remplace la [classe CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL. Pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

Constructeur.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Notes

Initialise les données membres et définit l’état initial du service.

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

Routine du gestionnaire pour le service.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Paramètres

*dwOpcode*<br/>
Commutateur qui définit l’opération du gestionnaire. Pour plus d’informations, consultez les notes.

### <a name="remarks"></a>Notes

Il s’agit du code que le gestionnaire de contrôle des services (SCM) appelle pour récupérer l’état du service et émettre des instructions telles que arrêter ou suspendre. Le SCM passe un code d’opération, comme indiqué ci `Handler` -dessous, à pour indiquer ce que le service doit faire.

|Code d’opération|Signification|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Arrête le service. Substituez la méthode [CAtlServiceModuleT:: OnStop](#onstop) dans atlbase. h pour modifier le comportement.|
|SERVICE_CONTROL_PAUSE|Implémentée par l’utilisateur. Substituez la méthode vide [CAtlServiceModuleT:: OnPause](#onpause) dans atlbase. h pour suspendre le service.|
|SERVICE_CONTROL_CONTINUE|Implémentée par l’utilisateur. Substituez la méthode vide [CAtlServiceModuleT:: OnContinue](#oncontinue) dans atlbase. h pour continuer le service.|
|SERVICE_CONTROL_INTERROGATE|Implémentée par l’utilisateur. Remplacez la méthode vide [CAtlServiceModuleT:: OnInterrogate](#oninterrogate) dans atlbase. h pour interroger le service.|
|SERVICE_CONTROL_SHUTDOWN|Implémentée par l’utilisateur. Substituez la méthode vide [CAtlServiceModuleT:: OnShutdown](#onshutdown) dans atlbase. h pour arrêter le service.|

Si le code d’opération n’est pas reconnu, la méthode [CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) est appelée.

Un service généré par ATL par défaut gère uniquement l’instruction Stop. Si le SCM passe l’instruction Stop, le service indique au SCM que le programme est sur le point de s’arrêter. Le service appelle `PostThreadMessage` ensuite pour envoyer un message Quit à lui-même. Cela met fin à la boucle de message et le service se ferme finalement.

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

Fournit les paramètres de sécurité par défaut pour le service.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Toute classe qui dérive de `CAtlServiceModuleT` doit implémenter cette méthode dans la classe dérivée.

Utilisez l’authentification au niveau PKT, le niveau d’emprunt d’identité de RPC_C_IMP_LEVEL_IDENTIFY et un descripteur de sécurité non null `CoInitializeSecurity`approprié dans l’appel à.

Pour les projets de service non attributés générés par l’Assistant, il s’agit de

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Pour les projets de service avec attributs, il s’agit de

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

Installe et crée le service.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Installe le service dans la base de données du gestionnaire de contrôle des services (SCM), puis crée l’objet de service. Si le service n’a pas pu être créé, une boîte de message s’affiche et la méthode retourne la valeur FALSe.

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

Confirme que le service a été installé.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le service est installé; sinon, FALSe.

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

Écrit dans le journal des événements.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Chaîne à écrire dans le journal des événements.

*...*<br/>
Chaînes supplémentaires facultatives à écrire dans le journal des événements.

### <a name="remarks"></a>Notes

Cette méthode écrit des détails dans un journal des événements, à l’aide de la fonction [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Si aucun service n’est en cours d’exécution, la chaîne est envoyée à la console.

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

Indicateur spécifiant que le programme s’exécute en tant que service.

```
BOOL m_bService;
```

### <a name="remarks"></a>Notes

Utilisé pour distinguer un EXE de service d’un EXE d’application.

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

Variable membre stockant l’identificateur de thread du service.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Notes

Cette variable stocke l’identificateur du thread actuel.

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

Variable membre stockant un handle vers la structure d’informations d’État pour le service actuel.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Notes

La structure [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contient des informations sur un service.

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

Variable membre stockant la structure d’informations d’État pour le service actuel.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Notes

La structure [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contient des informations sur un service.

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

Nom du service en cours d’inscription.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Notes

Chaîne terminée par le caractère null qui stocke le nom du service.

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

Substituez cette méthode pour continuer le service.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

Substituez cette méthode pour interroger le service.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

Substituez cette méthode pour suspendre le service.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

Substituez cette méthode pour arrêter le service.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

Substituez cette méthode pour arrêter le service.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

Substituez cette méthode pour gérer les demandes inconnues du service.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Paramètres

*dwOpcode*<br/>
Réservé.

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

Analyse la ligne de commande et effectue l’inscription si nécessaire.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Paramètres

*lpCmdLine*<br/>
Ligne de commande.

*pnRetCode*<br/>
HRESULT correspondant à l’inscription (si elle a eu lieu).

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, ou false si le fichier RGS fourni dans la ligne de commande n’a pas pu être enregistré.

### <a name="remarks"></a>Notes

Analyse la ligne de commande et inscrit ou annule l’enregistrement du fichier RGS fourni si nécessaire. Cette méthode appelle [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline) pour vérifier **/regserver** et **commutateur/unregserver**. L’ajout de l’argument **-/service** inscrira le service.

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

Cette méthode est appelée juste avant l’entrée dans la boucle de message.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Ce paramètre est passé à [CAtlExeModuleT::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Substituez cette méthode pour ajouter du code d’initialisation personnalisé pour le service.

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

Inscrit le service dans le registre.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Paramètres

*bService*<br/>
Doit avoir la valeur true pour pouvoir s’inscrire en tant que service.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="run"></a>  CAtlServiceModuleT::Run

Exécute le service.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Spécifie la façon dont la fenêtre doit être affichée. Ce paramètre peut être l’une des valeurs décrites dans la section [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . La valeur par défaut est SW_HIDE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Une fois appelé, `Run` appelle [CAtlServiceModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)et [CAtlExeModuleT::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain

Cette méthode est appelée par le gestionnaire de contrôle des services.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Paramètres

*dwArgc*<br/>
Argument argc.

*lpszArgv*<br/>
Argument argv.

### <a name="remarks"></a>Notes

Le gestionnaire de contrôle des services (SCM `ServiceMain` ) appelle lorsque vous ouvrez l’application services dans le panneau de configuration, sélectionnez le service, puis cliquez sur Démarrer.

Une fois le SCM `ServiceMain`appelé, un service doit fournir au SCM une fonction de gestionnaire. Cette fonction permet au SCM d’obtenir l’état du service et de transmettre des instructions spécifiques (telles que la suspension ou l’arrêt). Par la suite, [CAtlServiceModuleT:: Run](#run) est appelé pour effectuer le travail principal du service. `Run`continue à s’exécuter jusqu’à ce que le service soit arrêté.

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

Cette méthode met à jour l’état du service.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Paramètres

*dwState*<br/>
Nouvel État. Pour connaître les valeurs possibles, consultez [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) .

### <a name="remarks"></a>Notes

Met à jour les informations d’État du gestionnaire de contrôle des services pour le service. Elle est appelée par [CAtlServiceModuleT:: Run](#run), [CAtlServiceModuleT:: ServiceMain](#servicemain) et d’autres méthodes de gestionnaire. L’État est également stocké dans la variable membre [CAtlServiceModuleT:: m_status](#m_status).

##  <a name="start"></a>  CAtlServiceModuleT::Start

Appelé par `CAtlServiceModuleT::WinMain` lorsque le service démarre.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Spécifie la façon dont la fenêtre doit être affichée. Ce paramètre peut être l’une des valeurs décrites dans la section [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

La méthode [CAtlServiceModuleT:: WinMain](#winmain) gère à la fois l’inscription et l’installation, ainsi que les tâches impliquées dans la suppression des entrées de Registre et la désinstallation du module. Lorsque le service est exécuté, `WinMain` appelle `Start`.

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

Arrête et supprime le service.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Arrête l’exécution du service et le supprime de la base de données du gestionnaire de contrôle des services.

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

Décrémente le nombre de verrous du service.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de verrous, ce qui peut être utile pour les diagnostics et le débogage.

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

Supprime le service du Registre.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

Cette méthode implémente le code requis pour démarrer le service.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Spécifie la façon dont la fenêtre doit être affichée. Ce paramètre peut être l’une des valeurs décrites dans la section [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de retour du service.

### <a name="remarks"></a>Notes

Cette méthode traite la ligne de commande (avec [CAtlServiceModuleT::P arsecommandline](#parsecommandline)), puis démarre le service (à l’aide de [CAtlServiceModuleT:: Start](#start)).

## <a name="see-also"></a>Voir aussi

[CAtlExeModuleT, classe](../../atl/reference/catlexemodulet-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
