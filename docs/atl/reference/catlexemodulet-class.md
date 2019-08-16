---
title: CAtlExeModuleT, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497843"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT, classe

Cette classe représente le module pour une application.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `CAtlExeModuleT`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Constructeur.|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Initialise COM.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analyse la ligne de commande et effectue l’inscription si nécessaire.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Cette méthode est appelée immédiatement après la sortie de la boucle de message.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Cette méthode est appelée juste avant l’entrée dans la boucle de message.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Inscrit l’objet de classe.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Révoque l’objet de classe.|
|[CAtlExeModuleT::Run](#run)|Cette méthode exécute le code dans le module EXE pour initialiser, exécuter la boucle de message et nettoyer.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Cette méthode exécute la boucle de message.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Réinitialise COM.|
|[CAtlExeModuleT::Unlock](#unlock)|Décrémente le nombre de verrous du module.|
|[CAtlExeModuleT::WinMain](#winmain)|Cette méthode implémente le code requis pour exécuter un EXE.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Indicateur qui spécifie qu’il doit y avoir un délai d’arrêt du module.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Valeur de pause utilisée pour garantir que tous les objets sont libérés avant l’arrêt.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Valeur de délai d’attente utilisée pour retarder le déchargement du module.|

## <a name="remarks"></a>Notes

`CAtlExeModuleT`représente le module pour une application (EXE) et contient le code qui prend en charge la création d’un EXE, le traitement de la ligne de commande, l’inscription des objets de classe, l’exécution de la boucle de message et le nettoyage en quittant.

Cette classe est conçue pour améliorer les performances lorsque des objets COM dans le serveur EXE sont créés et détruits continuellement. Après la publication du dernier objet COM, le fichier EXE attend une durée spécifiée par le membre de données [CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout) . S’il n’y a aucune activité pendant cette période (autrement dit, aucun objet COM n’est créé), le processus d’arrêt est initié.

Le membre de données [CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown) est un indicateur utilisé pour déterminer si l’exe doit utiliser le mécanisme défini ci-dessus. S’il est défini sur false, le module se termine immédiatement.

Pour plus d’informations sur les modules dans ATL, consultez [ATL Module classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

Constructeur.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Notes

Si le module EXE n’a pas pu être initialisé, WinMain est immédiatement retourné sans traitement supplémentaire.

##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

Destructeur.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

Initialise COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode est appelée à partir du constructeur et peut être substituée pour initialiser COM de manière différente de l’implémentation par défaut. L’implémentation par défaut appelle `CoInitializeEx(NULL, COINIT_MULTITHREADED)` ou `CoInitialize(NULL)` en fonction de la configuration du projet.

La substitution de cette méthode nécessite normalement le remplacement de [CAtlExeModuleT:: UninitializeCom](#uninitializecom).

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

Indicateur qui spécifie qu’il doit y avoir un délai d’arrêt du module.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez la [vue d’ensemble de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) .

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

Valeur de pause utilisée pour vérifier que tous les objets ont disparu avant l’arrêt.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Notes

Modifiez cette valeur après avoir appelé [CAtlExeModuleT:: InitializeCom](#initializecom) pour définir le nombre de millisecondes utilisé comme valeur de pause pour arrêter le serveur. La valeur par défaut est 1000 millisecondes.

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

Valeur de délai d’attente utilisée pour retarder le déchargement du module.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Notes

Modifiez cette valeur après avoir appelé [CAtlExeModuleT:: InitializeCom](#initializecom) pour définir le nombre de millisecondes utilisées comme valeur de délai d’attente pour l’arrêt du serveur. La valeur par défaut est 5 000 millisecondes. Pour plus d’informations, consultez la [vue d’ensemble de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) .

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

Analyse la ligne de commande et effectue l’inscription si nécessaire.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Paramètres

*lpCmdLine*<br/>
Ligne de commande transmise à l’application.

*pnRetCode*<br/>
HRESULT correspondant à l’inscription (si elle a eu lieu).

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’application doit continuer à s’exécuter, sinon false.

### <a name="remarks"></a>Notes

Cette méthode est appelée à partir de [CAtlExeModuleT:: WinMain](#winmain) et peut être substituée pour gérer les commutateurs de ligne de commande. L’implémentation par défaut recherche les arguments de ligne de commande **/regserver** et **commutateur/unregserver** et effectue l’inscription ou l’annulation de l’inscription.

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

Cette méthode est appelée immédiatement après la sortie de la boucle de message.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Substituez cette méthode pour effectuer un nettoyage d’application personnalisé. L’implémentation par défaut appelle [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects).

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

Cette méthode est appelée juste avant l’entrée dans la boucle de message.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Valeur transmise en tant que paramètre *nShowCmd* dans WinMain.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Substituez cette méthode pour ajouter du code d’initialisation personnalisé pour l’application. L’implémentation par défaut enregistre les objets de classe.

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

Inscrit l’objet de classe avec OLE pour permettre à d’autres applications de s’y connecter.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Paramètres

*dwClsContext*<br/>
Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, S_FALSE s’il n’y a aucune classe à inscrire, ou une erreur HRESULT en cas d’échec.

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

Supprime l’objet de classe.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, S_FALSE s’il n’y a aucune classe à inscrire, ou une erreur HRESULT en cas d’échec.

##  <a name="run"></a>  CAtlExeModuleT::Run

Cette méthode exécute le code dans le module EXE pour initialiser, exécuter la boucle de message et nettoyer.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Spécifie la façon dont la fenêtre doit être affichée. Ce paramètre peut être l’une des valeurs décrites dans la section [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . La valeur par défaut est SW_HIDE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode peut être substituée. Toutefois, dans la pratique, il est préférable de remplacer [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)ou [CAtlExeModuleT::P ostmessageloop](#postmessageloop) à la place.

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

Cette méthode exécute la boucle de message.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Notes

Cette méthode peut être substituée pour modifier le comportement de la boucle de message.

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

Réinitialise COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode appelle simplement [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) et est appelée à partir du destructeur. Substituez cette méthode si vous remplacez [CAtlExeModuleT:: InitializeCom](#initializecom).

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

Décrémente le nombre de verrous du module.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui peut être utile pour les diagnostics ou les tests.

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

Cette méthode implémente le code requis pour exécuter un EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd*<br/>
Spécifie la façon dont la fenêtre doit être affichée. Ce paramètre peut être l’une des valeurs décrites dans la section [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de retour de l’exécutable.

### <a name="remarks"></a>Notes

Cette méthode peut être substituée. Si le remplacement de [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT::P ostmessageloop](#postmessageloop)ou [CAtlExeModuleT:: RunMessageLoop](#runmessageloop) n’offre pas suffisamment de flexibilité, il est possible de substituer la `WinMain` fonction à l’aide de cette méthode.

## <a name="see-also"></a>Voir aussi

[ATLDuck, exemple](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT, classe](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT, classe](../../atl/reference/catldllmodulet-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
