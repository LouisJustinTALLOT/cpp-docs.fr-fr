---
title: Classe CAtlExeModuleT
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
ms.openlocfilehash: 33edd8f2483bc21ea6cf8b68f80a2501c37d1a40
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748747"
---
# <a name="catlexemodulet-class"></a>Classe CAtlExeModuleT

Cette classe représente le module pour une application.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe `CAtlExeModuleT`dérivée de .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Constructeur.|
|[CAtlExeModuleT::CAtlExeModuleT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Initialise COM.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Parse la ligne de commande et effectue l’enregistrement si nécessaire.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Cette méthode est appelée immédiatement après la sortie de la boucle de message.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Cette méthode est appelée immédiatement avant d’entrer la boucle de message.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Enregistre l’objet de classe.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Révoque l’objet de classe.|
|[CAtlExeModuleT::Run](#run)|Cette méthode exécute le code dans le module EXE pour initialiser, exécuter la boucle de message et nettoyer.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Cette méthode exécute la boucle de message.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Uninitialise COM.|
|[CAtlExeModuleT::Unlock](#unlock)|Décrément le nombre de serrures du module.|
|[CAtlExeModuleT::WinMain](#winmain)|Cette méthode implémente le code requis pour exécuter un EXE.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Un drapeau indiquant qu’il devrait y avoir un retard pour arrêter le module.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Une valeur de pause utilisée pour s’assurer que tous les objets sont libérés avant l’arrêt.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Une valeur d’ines-temps utilisée pour retarder le déchargement du module.|

## <a name="remarks"></a>Notes

`CAtlExeModuleT`représente le module d’une application (EXE) et contient du code qui prend en charge la création d’un EXE, le traitement de la ligne de commande, l’enregistrement des objets de classe, l’exécution de la boucle de message et le nettoyage à la sortie.

Cette classe est conçue pour améliorer les performances lorsque les objets COM dans le serveur EXE sont continuellement créés et détruits. Après la sortie du dernier objet COM, l’EXE attend une durée spécifiée par le [CAtlExeModuleT ::m_dwTimeOut](#m_dwtimeout) membre des données. S’il n’y a pas d’activité pendant cette période (c’est-à-dire qu’aucun objet COM n’est créé), le processus d’arrêt est lancé.

Le [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) membre des données est un drapeau utilisé pour déterminer si l’EXE doit utiliser le mécanisme défini ci-dessus. S’il est réglé à faux, alors le module se termine immédiatement.

Pour plus d’informations sur les modules dans ATL, voir [atL Module Classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Constructeur.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Notes

Si le module EXE n’a pas pu être paraséminé, WinMain reviendra immédiatement sans autre traitement.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT::CAtlExeModuleT

Destructeur.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Initialise COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode est appelée à partir du constructeur et peut être remplacée pour initialiser COM d’une manière différente de la mise en œuvre par défaut. La implémentation par défaut appelle `CoInitializeEx(NULL, COINIT_MULTITHREADED)` ou `CoInitialize(NULL)` selon la configuration du projet.

L’emporter sur cette méthode nécessite normalement de prélever [CAtlExeModuleT::UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown

Un drapeau indiquant qu’il devrait y avoir un retard pour arrêter le module.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Notes

Voir le [aperçu CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) pour plus de détails.

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause

Une valeur de pause utilisée pour s’assurer que tous les objets sont partis avant l’arrêt.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Notes

Changez cette valeur après avoir appelé [CAtlExeModuleT::InitializeCom](#initializecom) pour définir le nombre de millisecondes utilisées comme valeur de pause pour l’arrêt du serveur. La valeur par défaut est de 1000 millisecondes.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut

Une valeur d’ines-temps utilisée pour retarder le déchargement du module.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Notes

Modifier cette valeur après avoir appelé [CAtlExeModuleT::InitializeCom](#initializecom) pour définir le nombre de millisecondes utilisées comme valeur d’arrêt pour arrêter le serveur. La valeur par défaut est 5 000 millisecondes. Voir le [aperçu CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) pour plus de détails.

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine

Parse la ligne de commande et effectue l’enregistrement si nécessaire.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Paramètres

*lpCmdLine (en)*<br/>
La ligne de commande est passée à la demande.

*code pnRet*<br/>
Le HRESULT correspondant à l’enregistrement (si elle a eu lieu).

### <a name="return-value"></a>Valeur de retour

Rendement vrai si l’application doit continuer à s’exécuter, autrement faux.

### <a name="remarks"></a>Notes

Cette méthode est appelée de [CAtlExeModuleT::WinMain](#winmain) et peut être remplacé pour gérer les commutateurs de ligne de commande. Les contrôles de mise en œuvre par défaut pour **/RegServer** et **/UnRegServer** commande-ligne arguments et effectue l’enregistrement ou l’enregistrement.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

Cette méthode est appelée immédiatement après la sortie de la boucle de message.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour effectuer le nettoyage des applications personnalisées. La implémentation par défaut appelle [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop

Cette méthode est appelée immédiatement avant d’entrer la boucle de message.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
La valeur est passée sous le titre *nShowCmd* paramètre dans WinMain.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour ajouter du code d’initialisation personnalisé pour l’application. La mise en œuvre par défaut enregistre les objets de classe.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Enregistre l’objet de classe avec OLE afin que d’autres applications puissent se connecter à elle.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Paramètres

*dwClsContexte*<br/>
Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, S_FALSE s’il n’y avait pas de classes à enregistrer, ou une erreur HRESULT sur l’échec.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Enlève l’objet de classe.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, S_FALSE s’il n’y avait pas de classes à enregistrer, ou une erreur HRESULT sur l’échec.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Run

Cette méthode exécute le code dans le module EXE pour initialiser, exécuter la boucle de message et nettoyer.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Précise comment la fenêtre doit être montrée. Ce paramètre peut être l’une des valeurs discutées dans la section [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) Par défaut pour SW_HIDE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode peut être remplacée. Cependant, dans la pratique est-il préférable de passer outre [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), ou [CAtlExeModuleT::PostMessageLoop](#postmessageloop) à la place.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Cette méthode exécute la boucle de message.

```cpp
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Notes

Cette méthode peut être remplacée pour changer le comportement de la boucle de message.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Uninitialise COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode appelle simplement [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) et est appelée à partir du destructeur. Remplacer cette méthode si vous [remplacez CAtlExeModuleT::InitializeCom](#initializecom).

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Unlock

Décrément le nombre de serrures du module.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain

Cette méthode implémente le code requis pour exécuter un EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Paramètres

*nShowCmd (en)*<br/>
Précise comment la fenêtre doit être montrée. Ce paramètre peut être l’une des valeurs discutées dans la section [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de retour de l’exécutable.

### <a name="remarks"></a>Notes

Cette méthode peut être remplacée. Si [c’est primordial CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), ou [CAtlExeModuleT::RunMessageLoop](#runmessageloop) ne fournit pas assez de `WinMain` flexibilité, il est possible de remplacer la fonction en utilisant cette méthode.

## <a name="see-also"></a>Voir aussi

[Échantillon ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[Classe CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Classe CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
