---
title: ATL classes et structs | Documents Microsoft
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e887f0adb7812664047fd30c3d9bb48368b9b564
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255751"
---
# <a name="atl-classes-and-structs"></a>Les structs et les classes ATL
La bibliothèque ATL (Active Template) inclut les classes et structs suivants. Pour rechercher une classe particulière par catégorie, consultez la [vue d’ensemble de la classe ATL](../../atl/atl-class-overview.md).  
  
|Classe / struct|Description|Fichier d'en-tête|  
|-----------|-----------------|-----------------|  
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Contient des informations utilisées pour le rendu à différentes cibles, comme une imprimante, un métafichier ou un contrôle ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Contient les données d’instance de classe dans le code de fenêtrage dans ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Utilisé par aucun projet qui utilise ATL.|atlbase.h|  
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Utilisé par le code relatif à COM dans ATL.| atlbase.h|  
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Contient des informations de type utilisées pour décrire une méthode ou propriété sur une dispinterface.|atlcom.h|  
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Contient les données utilisées par chaque module ATL.|atlbase.h|  
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Utilisé par le code de fenêtrage dans ATL.|atlbase.h|  
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CA2TEX` et `CT2AEX`et le typedef **CA2A**.|atlconv.h|  
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CA2CTEX` et `CT2CAEX`et le typedef **CA2CA**.|atlconv.h|  
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CA2TEX`, `CA2CTEX`, `CT2WEX`, et `CT2CWEX`et le typedef **CA2W**.|atlconv.h|  
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Cette classe est un wrapper pour un jeton d’accès.|ATLSecurity.h|  
|[CAcl](../../atl/reference/cacl-class.md)|Cette classe est un wrapper pour un **ACL** structure (liste de contrôle d’accès).|ATLSecurity.h|  
|[CAdapt](../../atl/reference/cadapt-class.md)|Ce modèle permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse afin de retourner un autre élément que l'adresse de l'objet.|atlcomcli.h|  
|[CAtlArray](../../atl/reference/catlarray-class.md)|Cette classe implémente un objet tableau.|atlcoll.h|  
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Cette classe implémente un serveur COM mis en pool de threads, le modèle de cloisonnement.|atlbase.h|  
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Cette classe fournit des méthodes pour implémenter un serveur COM mis en pool de threads, le modèle de cloisonnement.|atlbase.h|  
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Cette classe est instanciée dans chaque projet ATL.|atlcore.h|  
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Cette classe implémente un module COM de serveur.|atlbase.h|  
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Cette classe prend en charge pour les interfaces de débogage.|atlbase.h|  
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Cette classe représente le module d’une DLL.|atlbase.h|  
|[CAtlException](../../atl/reference/catlexception-class.md)|Cette classe définit une exception ATL.|atlexcept.h|  
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Cette classe représente le module d’une application.|atlbase.h|  
|[CAtlFile](../../atl/reference/catlfile-class.md)|Cette classe fournit un wrapper mince entourant les fenêtres des API de gestion de fichiers.|atlfile.h|  
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Cette classe représente un fichier mappé en mémoire, l’ajout d’un opérateur de conversion pour les méthodes de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|  
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Cette classe représente un fichier mappé en mémoire.|atlfile.h|  
|[CAtlList](../../atl/reference/catllist-class.md)|Cette classe fournit des méthodes pour créer et gérer un objet de liste.|atlcoll.h|  
|[CAtlMap](../../atl/reference/catlmap-class.md)|Cette classe fournit des méthodes pour créer et gérer un objet de mappage.|atlcoll.h|  
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Cette classe fournit des méthodes utilisées par plusieurs classes du module ATL.|atlbase.h|  
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Cette classe implémente un module ATL.|atlbase.h|  
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Cette classe est une implémentation d’une fenêtre qui est placée dans une fenêtre hôte fournie par l’interpréteur de commandes pour l’aperçu riche d’ATL.|atlpreviewctrlimpl.h|  
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Cette classe implémente un service.|atlbase.h|  
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Cette classe fournit des méthodes pour la création et l’utilisation d’un fichier temporaire.|atlfile.h|  
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Cette classe fournit un wrapper pour les fonctions de noyau Gestionnaire de transactions KTM (Kernel Transaction Manager).|atltransactionmanager.h|  
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Cette classe prend en charge pour les composants de fenêtrage ATL.|atlbase.h|  
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Cette classe représente un objet pointeur intelligent.|atlbase.h|  
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.|atlbase.h|  
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs intelligents.|atlcoll.h|  
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.|atlcoll.h|  
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Cette classe représente un objet pointeur intelligent à l’aide de nouveau vecteur et supprimer des opérateurs.|atlbase.h|  
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs intelligents à l’aide de nouveau vecteur et supprimer des opérateurs.|atlcoll.h|  
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Cette classe implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.|atlwin.h|  
|[Objet CAxWindow](../../atl/reference/caxwindow-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX.|atlwin.h|  
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge pour l’hébergement de contrôles ActiveX sous licence.|atlwin.h|  
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Cette classe implémente l'interface `IBindStatusCallback`.|atlctl.h|  
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Cette classe implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour un objet.|atlcom.h|  
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Cette classe fournit des méthodes pour la gestion de la mémoire à l’aide des routines de mémoire COM.|atlbase.h|  
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Cette classe prend en charge la gestion d’un thread cloisonné dans un module EXE mis en pool de threads.|atlbase.h|  
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Cette classe fournit des méthodes pour obtenir et de libérer la possession d’un objet de section critique.|atlcore.h|  
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [ATL Modules](../../atl/atl-module-classes.md) pour plus d’informations.|atlbase.h|  
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Cette classe est un wrapper pour `BSTR`s.|atlbase.h|  
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Cette classe implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour une interface détachable.|atlcom.h|  
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Cette classe implémente la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interface.|atlcom.h|  
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Cette classe implémente la [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interface.|atlcom.h|  
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Cette classe implémente la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interface et permet aux objets d’être créés dans des cloisonnements plusieurs.|atlcom.h|  
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Cette classe dérive [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.|atlcom.h|  
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Cette classe fournit des méthodes pour créer des instances d’une classe et d’obtention de ses propriétés.|atlcom.h|  
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Cette classe fournit les méthodes requises pour implémenter un contrôle composite.|atlctl.h|  
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Cette classe implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) par délégation à l’objet propriétaire **IUnknown**.|atlcom.h|  
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.|atlctl.h|  
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.|atlctl.h|  
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Cette classe fournit des méthodes pour obtenir et de libérer la possession d’un objet de section critique.|atlcore.h|  
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Cette classe fournit des méthodes de verrouillage et déverrouillage d’un objet de section critique.|atlbase.h|  
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Cette classe a des méthodes et des opérateurs pour créer et gérer un `CURRENCY` objet.|atlcur.h|  
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Cette classe stocke un tableau de **IUnknown** pointeurs.|atlcom.h|  
|[CComEnum](../../atl/reference/ccomenum-class.md)|Cette classe définit un objet d’énumérateur COM basé sur un tableau.|atlcom.h|  
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Cette classe fournit l’implémentation pour une interface d’énumérateur COM où les éléments en cours d’énumération sont stockées dans un tableau.|atlcom.h|  
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Cette classe définit un objet d’énumérateur COM basé sur une collection de la bibliothèque C++ Standard.|atlcom.h|  
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Cette classe fournit les mêmes méthodes que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) mais ne fournit ne pas une section critique.|atlcore.h|  
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Cette classe fournit des méthodes pour traiter les pointeurs d’interface et le tableau global d’interface (GIT).|atlbase.h|  
|[CComHeap](../../atl/reference/ccomheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation de mémoire COM.|ATLComMem.h|  
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Une classe de pointeur intelligent pour la gestion des pointeurs de segment de mémoire.|atlbase.h|  
|[CComModule](../../atl/reference/ccommodule-class.md)|À compter d’ATL 7.0, `CComModule` est obsolète : consultez [ATL Modules](../../atl/atl-module-classes.md) pour plus d’informations.|atlbase.h|  
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Cette classe fournit des méthodes thread-safe pour incrémenter et décrémenter la valeur d’une variable.|atlbase.h|  
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Cette classe fournit des méthodes thread-safe pour incrémenter et décrémenter la valeur d’une variable, sans verrouillage de section critique ou de la fonctionnalité de déverrouillage.|atlbase.h|  
|[CComObject](../../atl/reference/ccomobject-class.md)|Cette classe implémente **IUnknown** pour un objet brutes et non agrégée.|atlcom.h|  
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Cette classe gère un décompte de références sur le module contenant votre `Base` objet.|atlcom.h|  
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Cette classe implémente **IUnknown** pour un objet brutes et non agrégée, mais ne pas les incrément le module nombre de verrous dans le constructeur.|atlcom.h|  
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Ce typedef de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) est mise en modèle sur la valeur par défaut, le modèle du serveur de thread.|atlcom.h|  
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Cette classe fournit des méthodes pour gérer la gestion du nombre de référence objet pour les objets brutes et non agrégées et agrégées.|atlcom.h|  
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Cette classe crée un objet COM temporaire et lui fournit une implémentation squelette de **IUnknown**.|atlcom.h|  
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Cette classe implémente **IUnknown** pour un objet regroupé ou.|atlcom.h|  
|[CComPtr](../../atl/reference/ccomptr-class.md)|Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.|atlcomcli.h|  
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Cette classe fournit une base pour les classes de pointeur intelligent à l’aide des routines basé sur COM de mémoire.|atlcomcli.h|  
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.|atlcomcli.h|  
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs d’interface COM.|atlcoll.h|  
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Cette classe est un wrapper pour le `SAFEARRAY Data Type` structure.|atlsafe.h|  
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Cette classe est un wrapper pour un `SAFEARRAYBOUND` structure.|atlsafe.h|  
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Cette classe gère la sélection de thread pour la classe [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|  
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Cette classe fournit des méthodes pour incrémenter et décrémenter la valeur d’une variable.|atlbase.h|  
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Cette classe implémente une interface détachable.|atlcom.h|  
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Cette classe stocke **IUnknown** pointeurs et est conçu pour être utilisé en tant que paramètre à la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) classe de modèle.|atlcom.h|  
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Cette classe encapsule le type VARIANT, en fournissant un membre indiquant le type de données stockées.|atlcomcli.h|  
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Cette classe implémente une fenêtre contenue dans un autre objet.|atlwin.h|  
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Cette classe fournit des méthodes pour la gestion de la mémoire à l’aide des routines de mémoire CRT.|atlcore.h|  
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas CRT.|atlmem.h|  
|[CDacl](../../atl/reference/cdacl-class.md)|Cette classe est un wrapper pour une structure de la liste DACL (liste de contrôle d’accès discrétionnaire).|ATLSecurity.h|  
|[CDebugReportHook, classe](../../atl/reference/cdebugreporthook-class.md)|Cette classe permet d’envoyer des rapports de débogage à un canal nommé.|atlutil.h|  
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Cette classe fournit deux fonctions statiques pour la conversion de caractères entre majuscules et minuscules.|atlcoll.h|  
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Cette classe fournit des fonctions de comparaison élément par défaut.|atlcoll.h|  
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Cette classe fournit des fonctions et des méthodes par défaut pour une classe de collection.|atlcoll.h|  
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Cette classe fournit une fonction statique pour le calcul de valeurs de hachage.|atlcoll.h|  
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Cette classe fournit des méthodes pour la création d’une boîte de dialogue modale ou non.|atlwin.h|  
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Cette classe fournit des méthodes de prise en charge le chaînage dynamique des tables des messages.|atlwin.h|  
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Cette classe est utilisée par les classes de collection pour fournir des fonctions et méthodes pour déplacer, copier, de comparaison et opérations de hachage.|atlcoll.h|  
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Cette classe fournit la copie de la valeur par défaut et les méthodes d’une classe de collection de déplacement.|atlcoll.h|  
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Cette classe fournit des méthodes de notification du récepteur du conteneur en ce qui concerne les modifications apportées aux propriétés de contrôle.|atlctl.h|  
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas global Win32.|atlmem.h|  
|[CHandle](../../atl/reference/chandle-class.md)|Cette classe fournit des méthodes pour la création et à l’aide d’un handle d’objet.|atlbase.h|  
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Une classe de pointeur intelligent pour la gestion des pointeurs de segment de mémoire.|atlcore.h|  
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Cette classe constitue la base pour plusieurs classes de pointeur de segment de mémoire actives.|atlcore.h|  
|[CHeapPtrElementTraits, classe](../../atl/reference/cheapptrelementtraits-class.md)|Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs de tas.|atlcoll.h|  
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.|atlcoll.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Fournit une prise en charge améliorée des images bitmap, y compris la possibilité de charger et enregistrer des images dans les formats JPEG, GIF, BMP et PNG Portable Network Graphics ().|atlimage.h|  
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.|atlcoll.h|  
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.|atlcoll.h|  
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas local Win32.|atlmem.h|  
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Cette classe permet de que tables des messages d’un objet pour être accessible par un autre objet.|atlwin.h|  
|[CNonStatelessWorker, classe](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes à partir d’un pool de threads et les transmet à un objet de travail qui est créé et détruit à chaque demande.|atlutil.h|  
|[CNoWorkerThread, classe](../../atl/reference/cnoworkerthread-class.md)|Utilisez cette classe comme argument pour le `MonitorClass` classes de cache de paramètre de modèle si vous souhaitez désactiver la maintenance du cache dynamique.|atlutil.h|  
|[CPathT, classe](../../atl/reference/cpatht-class.md)|Cette classe représente un chemin d’accès.|atlpath.h|  
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Cette classe fournit des méthodes par défaut et des fonctions pour une classe de collection composée des types de données primitifs.|atlcoll.h|  
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Cette classe représente un objet de descripteur de sécurité objet privé.|ATLSecurity.h|  
|[CRBMap](../../atl/reference/crbmap-class.md)|Cette classe représente une structure de mappage à l’aide d’un arbre binaire rouge-noire.|atlcoll.h|  
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Cette classe représente une structure de mappage qui permet à chaque clé à associer à plusieurs valeurs, à l’aide d’un arbre binaire rouge-noire.|atlcoll.h|  
|[CRBTree](../../atl/reference/crbtree-class.md)|Cette classe fournit des méthodes pour la création et utilisation d’une arborescence rouge-noire.|atlcoll.h|  
|[CRegKey](../../atl/reference/cregkey-class.md)|Cette classe fournit des méthodes pour manipuler des entrées dans le Registre système.|atlbase.h|  
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Cette classe fournit la fonction de création d’un thread de CRT. Utilisez cette classe si le thread utilisent des fonctions CRT.|atlbase.h|  
|[CSacl](../../atl/reference/csacl-class.md)|Cette classe est un wrapper pour une structure SACL (liste de contrôle d’accès système).|ATLSecurity.h|  
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Cette classe est un wrapper mince pour le **SECURITY_ATTRIBUTES** structure.|ATLSecurity.h|  
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Cette classe est un wrapper pour le **SECURITY_DESCRIPTOR** structure.|ATLSecurity.h|  
|[CSid](../../atl/reference/csid-class.md)|Cette classe est un wrapper pour un `SID` structure de (l’identificateur de sécurité).|ATLSecurity.h|  
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Cette classe fournit des méthodes pour la gestion d’un simple tableau.|atlsimpcoll.h|  
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Cette classe est une application d’assistance pour le [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.|atlsimpcoll.h|  
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Cette classe est une application d’assistance pour le [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.|atlsimpcoll.h|  
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Cette classe implémente une boîte de dialogue modale base.|atlwin.h|  
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Cette classe prend en charge un tableau de mappage simple.|atlsimpcoll.h|  
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Cette classe est une application d’assistance pour le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe.|atlsimpcoll.h|  
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Cette classe est une application d’assistance pour le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe.|atlsimpcoll.h|  
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Cette classe fournit des méthodes pour implémenter un objet de nœud de composant logiciel enfichable.|atlsnap.h|  
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Cette classe fournit des méthodes pour implémenter un objet de page de propriétés du composant logiciel enfichable.|atlsnap.h|  
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Cette classe fournit des méthodes pour prendre en charge les valeurs de propriétés stock.|atlctl.h|  
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Cette classe fournit des fonctions statiques utilisées par le stockage des classes de collection `CString` objets.|CStringT.h|  
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Cette classe fournit des fonctions statiques relatives aux chaînes stockées dans les objets de classe de collection. Il est similaire à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), mais effectue des comparaisons sans respecter la casse.|atlcoll.h|  
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Cette classe fournit des fonctions statiques relatives aux chaînes stockées dans les objets de classe de collection. Les objets de chaîne sont traitées en tant que références.|atlcoll.h|  
|[CThreadPool, classe](../../atl/reference/cthreadpool-class.md)|Cette classe fournit un pool de threads de travail qui traitent d’une file d’attente d’éléments de travail.|atlutil.h|  
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Cette classe est un wrapper pour le **TOKEN_GROUPS** structure.|ATLSecurity.h|  
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Cette classe est un wrapper pour le **TOKEN_PRIVILEGES** structure.|ATLSecurity.h|  
|[CUrl, classe](../../atl/reference/curl-class.md)|Cette classe représente une URL. Il vous permet de manipuler chaque élément de l’URL indépendamment des autres si l’analyse des URL existante de chaîne ou de génération d’une chaîne à partir de zéro.|atlutil.h|  
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CT2AEX`, `CW2TEX`, `CW2CTEX`, et `CT2CAEX`et le typedef **CW2A**.|atlconv.h|  
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CW2CTEX` et `CT2CWEX`et le typedef **CW2CW**.|atlconv.h|  
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes `CW2TEX` et `CT2WEX`et le typedef `CW2W`.|atlconv.h|  
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation du tas Win32.|atlmem.h|  
|[CWindow](../../atl/reference/cwindow-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre.|atlwin.h|  
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Cette classe fournit des méthodes pour créer ou sous-classer une fenêtre.|atlwin.h|  
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Cette classe fournit une méthode pour standardiser les styles utilisés lors de la création d’un objet window.|atlwin.h|  
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Cette classe fournit une méthode pour standardiser les styles utilisés lors de la création d’un objet window.|atlwin.h|  
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Cette classe fournit des méthodes pour l’inscription des informations pour une classe de fenêtre.|atlwin.h|  
|[CWorkerThread, classe](../../atl/reference/cworkerthread-class.md)|Cette classe crée un thread de travail ou utilise un existant, attend sur un ou plusieurs handles d’objet noyau et exécute une fonction de client spécifié lors d’une des poignées est signalée.|atlutil.h|  
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Cette classe représente une interface pour un `CreateInstance` (méthode).|atlbase.h|  
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Cette classe représente l’interface pour un gestionnaire de mémoire.|atlmem.h|  
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Cette interface fournit des méthodes permettant de spécifier les caractéristiques du contrôle hébergé ou du conteneur.|atlbase.h, ATLIFace.h|  
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Cette interface implémente des propriétés ambiantes supplémentaires pour un contrôle hébergé.|atlbase.h, ATLIFace.h|  
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Cette interface fournit des méthodes pour manipuler un contrôle et son objet ordinateur hôte.|atlbase.h, ATLIFace.h|  
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet ordinateur hôte.|atlbase.h, ATLIFace.h|  
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Cette classe fournit des méthodes utilisées par une classe de collection.|atlcom.h|  
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Cette classe implémente un conteneur de point de connexion pour gérer une collection de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objets.|atlcom.h|  
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Cette classe implémente un point de connexion.|atlcom.h|  
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Cette classe fournit des méthodes pour prendre en charge le transfert de données uniforme et de gestion des connexions.|atlctl.h|  
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Cette classe fournit une implémentation par défaut pour le `IDispatch` partie d’une interface double.|atlcom.h|  
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Cette classe fournit des implémentations de la `IDispatch` méthodes.|atlcom.h|  
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Cette classe fournit des implémentations de la `IDispatch` méthodes, sans récupérer les informations de type à partir d’une bibliothèque de types.|atlcom.h|  
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Interface utilisée pour l’analyse Microsoft HTML et de moteur de rendu.|atlbase.h, ATLIFace.h|  
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Cette classe définit une interface d’énumérateur basée sur une collection de la bibliothèque C++ Standard.|atlcom.h|  
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Cette classe fournit une implémentation par défaut de la `IObjectSafety` interface pour permettre à un client récupérer et définir des niveaux de sécurité d’un objet.|atlctl.h|  
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Cette classe fournit des méthodes permettant d’un objet communiquer avec son site.|atlcom.h|  
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Cette classe fournit une implémentation par défaut de la **IOleControl** interface et implémente **IUnknown**.|atlctl.h|  
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Cette classe fournit des méthodes d’assistance de communication entre un contrôle sur place et son conteneur.|atlctl.h|  
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Cette classe implémente **IUnknown** et fournit des méthodes qui permettent un contrôle sans fenêtre pour recevoir des messages de fenêtre et participer aux opérations de glisser-déplacer.|atlctl.h|  
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Cette classe implémente **IUnknown** et est l’interface principale par le biais duquel un conteneur communique avec un contrôle.|atlctl.h|  
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Cette classe implémente **IUnknown** et permet au client d’accéder aux informations dans les pages de propriétés d’un objet.|atlctl.h|  
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Cette classe implémente **IUnknown** et permet à un objet enregistrer ses propriétés à un jeu de propriétés de fourni par le client.|atlcom.h|  
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Cette classe implémente la [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interface.|atlcom.h|  
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface.|atlcom.h|  
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Cette classe implémente **IUnknown** et [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) méthodes d’interface.|atlctl.h|  
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Cette classe expose le [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface comme une interface sortante sur un objet connectable.|atlctl.h|  
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Cette classe implémente **IUnknown** et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|  
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interface.|atlctl.h|  
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Cette classe fournit une implémentation par défaut de la [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) et [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) méthodes.|atlcom.h|  
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Cette classe combine l’initialisation du contrôle de conteneurs en un seul appel.|atlctl.h|  
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interface.|atlctl.h|  
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Cette classe fournit une implémentation par défaut de la `IServiceProvider` interface.|atlcom.h|  
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interface.|atlcom.h|  
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Cette classe fournit une implémentation par défaut de la `ISupportErrorInfo Interface` de l’interface et peut être utilisé lorsque seulement une seule interface génère des erreurs sur un objet.|atlcom.h|  
|[IThreadPoolConfig, interface](../../atl/reference/ithreadpoolconfig-interface.md)|Cette interface fournit des méthodes pour la configuration d’un pool de threads.|atlutil.h|  
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Cette classe implémente **IUnknown** et fournit des implémentations par défaut de la [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), et [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)interfaces.|atlctl.h|  
|[IWorkerThreadClient, interface](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` est l’interface implémentée par les clients de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) classe.|atlutil.h|  
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Cette classe fournit des wrappers pour **CreateWindow** et **CreateWindowEx**.|atlwin.h|  
|[_U_RECT](../../atl/reference/u-rect-class.md)|Cette classe d’argument d’adaptateur permet soit `RECT` pointeurs ou références à passer à une fonction qui est implémentée en termes de pointeurs.|atlwin.h|  
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Cette classe d’argument d’adaptateur permet à deux noms de ressources (`LPCTSTR`s) ou l’ID de ressource (**UINT**s) à passer à une fonction sans nécessiter de l’appelant convertir une chaîne à l’aide de l’ID du **MAKEINTRESOURCE** (macro).|atlwin.h|  
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Cette classe fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread ne doit pas utiliser de fonctions CRT.|atlbase.h|  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)   
 [Fonctions](../../atl/reference/atl-functions.md)   
 [Variables globales](../../atl/reference/atl-global-variables.md)   
 [Typedefs](../../atl/reference/atl-typedefs.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)


