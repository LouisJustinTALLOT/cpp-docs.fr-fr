---
title: Classe CAtlServiceModuleT
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
ms.openlocfilehash: 6d1985384c2d9a324abac548f27be6be5f0cacf5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748593"
---
# <a name="catlservicemodulet-class"></a>Classe CAtlServiceModuleT

Cette classe met en œuvre un service.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe `CAtlServiceModuleT`dérivée de .

*nServiceNameID (en)*<br/>
L’identifiant de ressource du service.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|La routine du gestionnaire pour le service.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Fournit les paramètres de sécurité par défaut pour le service.|
|[CAtlServiceModuleT::Installation](#install)|Installe et crée le service.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Confirme que le service a été installé.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Écrit au journal de l’événement.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Remplacer cette méthode pour continuer le service.|
|[CAtlServiceModuleT::SurInterrogate](#oninterrogate)|Remplacer cette méthode pour interroger le service.|
|[CAtlServiceModuleT::OnPause](#onpause)|Remplacer cette méthode pour mettre en pause le service.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Remplacer cette méthode pour fermer le service|
|[CAtlServiceModuleT::OnStop](#onstop)|Remplacer cette méthode pour arrêter le service|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Remplacer cette méthode pour traiter les demandes inconnues au service|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Parse la ligne de commande et effectue l’enregistrement si nécessaire.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Cette méthode est appelée immédiatement avant d’entrer la boucle de message.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Enregistre le service dans le registre.|
|[CAtlServiceModuleT::Run](#run)|Exécute le service.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Méthode appelée par le gestionnaire de contrôle de service.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Mise à jour de l’état du service.|
|[CAtlServiceModuleT::Démarrer](#start)|Appelé `CAtlServiceModuleT::WinMain` par quand le service commence.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Arrête et supprime le service.|
|[CAtlServiceModuleT::Unlock](#unlock)|Décrément le nombre de serrures du service.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Supprime le service du registre.|
|[CAtlServiceModuleT::WinMain](#winmain)|Cette méthode implémente le code requis pour exécuter le service.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Drapeau indiquant que le programme fonctionne comme un service.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Variable de membre stockant l’identifiant de thread.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Le membre variable stockant une poignée à la structure d’information d’état pour le service actuel.|
|[CAtlServiceModuleT::m_status](#m_status)|Variable de membre stockant la structure d’information d’état pour le service actuel.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Le nom du service étant enregistré.|

## <a name="remarks"></a>Notes

`CAtlServiceModuleT`, dérivé de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implémente un module de service ATL. `CAtlServiceModuleT`fournit des méthodes de traitement, d’installation, d’enregistrement et de suppression de lignes de commande. Si des fonctionnalités supplémentaires sont nécessaires, ces méthodes et d’autres peuvent être remplacées.

Cette classe remplace la [classe CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL. Voir [les classes de module ATL](../../atl/atl-module-classes.md) pour plus de détails.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT

Constructeur.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Notes

Initialise les membres des données et définit le statut de service initial.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::Handler

La routine du gestionnaire pour le service.

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Paramètres

*dwOpcode*<br/>
Un interrupteur qui définit le fonctionnement du gestionnaire. Pour plus de détails, voir les remarques.

### <a name="remarks"></a>Notes

C’est le code que le gestionnaire de contrôle de service (SCM) appelle pour récupérer l’état du service et émettre des instructions telles que l’arrêt ou la pause. Le SCM adopte un code d’opération, indiqué ci-dessous, pour `Handler` indiquer ce que le service doit faire.

|Code d’opération|Signification|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|arrête le service. Remplacer la méthode [CAtlServiceModuleT::OnStop](#onstop) in atlbase.h pour changer le comportement.|
|SERVICE_CONTROL_PAUSE|Mise en œuvre de l’utilisateur. Remplacer la méthode vide [CAtlServiceModuleT::OnPause](#onpause) in atlbase.h pour mettre en pause le service.|
|SERVICE_CONTROL_CONTINUE|Mise en œuvre de l’utilisateur. Remplacer la méthode vide [CAtlServiceModuleT::OnContinue](#oncontinue) dans atlbase.h pour continuer le service.|
|SERVICE_CONTROL_INTERROGATE|Mise en œuvre de l’utilisateur. Remplacer la méthode vide [CAtlServiceModuleT::OnInterrogate](#oninterrogate) in atlbase.h pour interroger le service.|
|SERVICE_CONTROL_SHUTDOWN|Mise en œuvre de l’utilisateur. Remplacer la méthode vide [CAtlServiceModuleT::OnShutdown](#onshutdown) in atlbase.h pour arrêter le service.|

Si le code d’opération n’est pas reconnu, la méthode [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) est appelée.

Un service généré par défaut par ATL ne gère que l’instruction d’arrêt. Si le SCM passe l’instruction d’arrêt, le service indique au SCM que le programme est sur le point de s’arrêter. Le service `PostThreadMessage` appelle alors pour poster un message d’abandon à lui-même. Cela met fin à la boucle de message et le service finira par fermer.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity

Fournit les paramètres de sécurité par défaut pour le service.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Toute classe qui `CAtlServiceModuleT` dérive de doit mettre en œuvre cette méthode dans la classe dérivée.

Utilisez l’authentification au niveau de la PKT, le niveau d’usurpation `CoInitializeSecurity`d’identité de RPC_C_IMP_LEVEL_IDENTIFY et un descripteur de sécurité approprié non nul dans l’appel à .

Pour les projets de service non attribués générés par les sorciers, ce serait en

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Pour les projets de services attribués, il s’agirait de

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT::Installation

Installe et crée le service.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Installe le service dans la base de données du Gestionnaire de Contrôle de Service (SCM), puis crée l’objet de service. Si le service n’a pas pu être créé, une boîte de message est affichée et la méthode renvoie FALSE.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled

Confirme que le service a été installé.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le service est installé, FALSE autrement.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::LogEvent

Écrit au journal de l’événement.

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Chaîne à écrire dans le journal des événements.

*...*<br/>
Chaînes supplémentaires facultatives à écrire sur le journal de l’événement.

### <a name="remarks"></a>Notes

Cette méthode écrit des détails sur un journal d’événements, en utilisant la fonction [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Si aucun service n’est en cours d’exécution, la chaîne est envoyée à la console.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT::m_bService

Drapeau indiquant que le programme fonctionne comme un service.

```
BOOL m_bService;
```

### <a name="remarks"></a>Notes

Utilisé pour distinguer un service EXE d’une application EXE.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID

Variable de membre stockant l’identifiant de thread du Service.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Notes

Cette variable stocke l’identifiant de thread du thread actuel.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus

Le membre variable stockant une poignée à la structure d’information d’état pour le service actuel.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Notes

La structure [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contient des informations sur un service.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT::m_status

Variable de membre stockant la structure d’information d’état pour le service actuel.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Notes

La structure [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contient des informations sur un service.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName

Le nom du service étant enregistré.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Notes

Une chaîne non terminée qui stocke le nom du service.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT::OnContinue

Remplacer cette méthode pour continuer le service.

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::SurInterrogate

Remplacer cette méthode pour interroger le service.

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT::OnPause

Remplacer cette méthode pour mettre en pause le service.

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown

Remplacez cette méthode pour arrêter le service.

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT::OnStop

Remplacer cette méthode pour arrêter le service.

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest

Remplacer cette méthode pour traiter les demandes inconnues au service.

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Paramètres

*dwOpcode*<br/>
Réservé.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine

Parse la ligne de commande et effectue l’enregistrement si nécessaire.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Paramètres

*lpCmdLine (en)*<br/>
Ligne de commande.

*code pnRet*<br/>
Le HRESULT correspondant à l’enregistrement (si elle a eu lieu).

### <a name="return-value"></a>Valeur de retour

Les déclarations sont vraies sur le succès, ou fausses si le fichier RGS fourni dans la ligne de commandement ne pouvait pas être enregistré.

### <a name="remarks"></a>Notes

Parse la ligne de commande et enregistre ou non le fichier RGS fourni si nécessaire. Cette méthode appelle [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) pour vérifier **pour /RegServer** et **/UnregServer**. Ajout de l’argument **-/Service** enregistrera le service.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop

Cette méthode est appelée immédiatement avant d’entrer la boucle de message.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Ce paramètre est transmis à [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour ajouter du code d’initialisation personnalisé pour le Service.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId

Enregistre le service dans le registre.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Paramètres

*bService (en)*<br/>
Doit être vrai pour s’inscrire en tant que service.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT::Run

Exécute le service.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Précise comment la fenêtre doit être montrée. Ce paramètre peut être l’une des valeurs discutées dans la section [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) La valeur par défaut est SW_HIDE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Après avoir `Run` été appelé, appelle [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), et [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT::ServiceMain

Cette méthode est appelée par le gestionnaire de contrôle de service.

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Paramètres

*dwArgc dwArgc*<br/>
L’argument de l’argc.

*lpszArgv*<br/>
L’argument de l’argv.

### <a name="remarks"></a>Notes

Le gestionnaire de contrôle de `ServiceMain` service (SCM) appelle lorsque vous ouvrez l’application Services dans le panneau de contrôle, sélectionnez le service et cliquez sur Démarrer.

Après les appels `ServiceMain`SCM , un service doit donner au SCM une fonction de gestionnaire. Cette fonction permet au SCM d’obtenir le statut du service et de passer des instructions spécifiques (telles que la pause ou l’arrêt). Par la suite, [CAtlServiceModuleT::Run](#run) est appelé à effectuer le travail principal du service. `Run`continue d’exécuter jusqu’à ce que le service soit arrêté.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus

Cette méthode met à jour l’état du service.

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Paramètres

*dwState (en)*<br/>
Nouvel état. Voir [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) pour les valeurs possibles.

### <a name="remarks"></a>Notes

Mise à jour des informations sur l’état du service du gestionnaire de contrôle de service pour le service. Il est appelé par [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) et d’autres méthodes de manutention. L’état est également stocké dans le membre variable [CAtlServiceModuleT::m_status](#m_status).

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT::Démarrer

Appelé `CAtlServiceModuleT::WinMain` par quand le service commence.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Précise comment la fenêtre doit être montrée. Ce paramètre peut être l’une des valeurs discutées dans la section [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

La méthode [CAtlServiceModuleT::WinMain](#winmain) gère à la fois l’enregistrement et l’installation, ainsi que les tâches liées à la suppression des entrées de registre et à la désinstallation du module. Lorsque le service `WinMain` est `Start`exécuté, appelle .

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::Uninstall

Arrête et supprime le service.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Empêche le service de fonctionner et le supprime de la base de données De service Control Manager.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT::Unlock

Décrément le nombre de serrures du service.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de serrures, qui peut être utile pour le diagnostic et le débogage.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId

Supprime le service du registre.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::WinMain

Cette méthode implémente le code requis pour démarrer le service.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Précise comment la fenêtre doit être montrée. Ce paramètre peut être l’une des valeurs discutées dans la section [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de retour du service.

### <a name="remarks"></a>Notes

Cette méthode traite la ligne de commande (avec [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) et commence ensuite le service (à l’aide [de CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Voir aussi

[Classe CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
