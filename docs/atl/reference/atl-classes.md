---
title: Classes et structs ATL | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498052"
---
# <a name="atl-classes-and-structs"></a>Classes et structs ATL

La Active Template Library (ATL) comprend les classes et structs suivants. Pour rechercher une classe particulière par catégorie, consultez la [vue d’ensemble de la classe ATL](../../atl/atl-class-overview.md).

|Class/struct|Description|Fichier d’en-tête|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Contient des informations utilisées pour le rendu de différentes cibles, telles qu’une imprimante, un métafichier ou un contrôle ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Contient des données d’instance de classe dans le code de fenêtrage dans ATL.|atlbase. h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Utilisé par n’importe quel projet qui utilise ATL.|atlbase. h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Utilisé par le code COM dans ATL.| atlbase. h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Contient les informations de type utilisées pour décrire une méthode ou une propriété sur une dispinterface.|atlcom. h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Contient les données utilisées par chaque module ATL.|atlbase. h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Utilisé par le code de fenêtrage dans ATL.|atlbase. h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CA2TEX et CT2AEX, ainsi que par le CA2A typedef.|atlconv. h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CA2CTEX et CT2CAEX, ainsi que par le CA2CA typedef.|atlconv. h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CA2TEX, CA2CTEX, CT2WEX et CT2CWEX, ainsi que les CA2W typedef.|atlconv. h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Cette classe est un wrapper pour un jeton d’accès.|ATLSecurity. h|
|[CAcl](../../atl/reference/cacl-class.md)|Cette classe est un wrapper pour une structure ACL (liste de contrôle d’accès).|ATLSecurity. h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Ce modèle permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse afin de retourner un autre élément que l'adresse de l'objet.|atlcomcli. h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Cette classe implémente un objet de tableau.|atlcoll. h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Cette classe implémente un serveur COM de modèle cloisonné et à pool de threads.|atlbase. h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Cette classe fournit des méthodes pour implémenter un serveur COM à pool de threads et de modèle Apartment.|atlbase. h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Cette classe est instanciée dans chaque projet ATL.|atlcore. h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Cette classe implémente un module serveur COM.|atlbase. h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Cette classe fournit la prise en charge pour le débogage des interfaces.|atlbase. h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Cette classe représente le module pour une DLL.|atlbase. h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Cette classe définit une exception ATL.|atlexcept. h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Cette classe représente le module pour une application.|atlbase. h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Cette classe fournit un wrapper fin autour de l’API de gestion des fichiers Windows.|atlfile. h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Cette classe représente un fichier mappé en mémoire, en ajoutant un opérateur de cast aux méthodes de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile. h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Cette classe représente un fichier mappé en mémoire.|atlfile. h|
|[CAtlList](../../atl/reference/catllist-class.md)|Cette classe fournit des méthodes pour créer et gérer un objet de liste.|atlcoll. h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Cette classe fournit des méthodes pour créer et gérer un objet Map.|atlcoll. h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Cette classe fournit des méthodes utilisées par plusieurs classes de module ATL.|atlbase. h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Cette classe implémente un module ATL.|atlbase. h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Cette classe est une implémentation ATL d’une fenêtre qui est placée dans une fenêtre hôte fournie par le Shell pour l’aperçu riche.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Cette classe implémente un service.|atlbase. h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Cette classe fournit des méthodes pour la création et l’utilisation d’un fichier temporaire.|atlfile. h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Cette classe fournit un wrapper aux fonctions du gestionnaire de transactions KTM (Kernel Transaction Manager).|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Cette classe fournit la prise en charge des composants de fenêtrage ATL.|atlbase. h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Cette classe représente un objet pointeur intelligent.|atlbase. h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.|atlbase. h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs intelligents.|atlcoll. h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.|atlcoll. h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Cette classe représente un objet pointeur intelligent à l’aide d’opérateurs Vector New et DELETE.|atlbase. h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs intelligents à l’aide d’opérateurs Vector New et DELETE.|atlcoll. h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Cette classe implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.|atlwin. h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX.|atlwin. h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge l’hébergement de contrôles ActiveX sous licence.|atlwin. h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Cette classe implémente l'interface `IBindStatusCallback` .|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Cette classe implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé.|atlcom. h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines de mémoire COM.|atlbase. h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Cette classe fournit la prise en charge de la gestion d’un cloisonnement dans un module EXE mis en pool de threads.|atlbase. h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.|atlcore. h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|À partir de ATL 7,0 `CComAutoThreadModule` , est obsolète: pour plus d’informations, consultez [modules ATL](../../atl/atl-module-classes.md) .|atlbase. h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Cette classe est un wrapper pour les BSTR.|atlbase. h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Cette classe implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface détachée.|atlcom. h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .|atlcom. h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Cette classe implémente l’interface [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .|atlcom. h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) et permet la création d’objets dans plusieurs cloisonnements.|atlcom. h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.|atlcom. h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Cette classe fournit des méthodes pour la création d’instances d’une classe et l’obtention de ses propriétés.|atlcom. h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Cette classe fournit les méthodes requises pour implémenter un contrôle composite.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Cette classe implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en déléguant au de `IUnknown`l’objet propriétaire.|atlcom. h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.|atlcore. h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Cette classe fournit des méthodes pour le verrouillage et le déverrouillage d’un objet de section critique.|atlbase. h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Cette classe possède des méthodes et des opérateurs pour la création et la gestion d’un objet CURRENCY.|atlcur. h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Cette classe stocke un tableau `IUnknown` de pointeurs.|atlcom. h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Cette classe définit un objet énumérateur COM basé sur un tableau.|atlcom. h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Cette classe fournit l’implémentation pour une interface d’énumérateur COM où les éléments qui sont énumérés sont stockés dans un tableau.|atlcom. h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Cette classe définit un objet énumérateur COM basé sur une C++ collection de bibliothèques standard.|atlcom. h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Cette classe fournit les mêmes méthodes que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , mais ne fournit pas de section critique.|atlcore. h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Cette classe fournit des méthodes pour traiter les pointeurs d’interface et la table d’interface globale (GIT).|atlbase. h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation de mémoire com.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Classe de pointeur intelligent pour la gestion des pointeurs de tas.|atlbase. h|
|[CComModule](../../atl/reference/ccommodule-class.md)|À partir de ATL 7,0 `CComModule` , est obsolète: pour plus d’informations, consultez [modules ATL](../../atl/atl-module-classes.md) .|atlbase. h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Cette classe fournit des méthodes thread-safe pour l’incrémentation et la décrémentation de la valeur d’une variable.|atlbase. h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Cette classe fournit des méthodes thread-safe pour l’incrémentation et la décrémentation de la valeur d’une variable, sans verrouillage de section critique ou fonctionnalité de déverrouillage.|atlbase. h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Cette classe implémente `IUnknown` pour un objet non agrégé.|atlcom. h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Cette classe gère un décompte de références sur le module `Base` contenant votre objet.|atlcom. h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Cette classe implémente `IUnknown` pour un objet non agrégé, mais n’incrémente pas le nombre de verrous de module dans le constructeur.|atlcom. h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Ce typedef de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) est mis en modèle sur le modèle de thread par défaut du serveur.|atlcom. h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Cette classe fournit des méthodes pour gérer la gestion du nombre de références d’objet pour les objets non agrégés et agrégés.|atlcom. h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Cette classe crée un objet COM temporaire et lui fournit une implémentation squelettique de `IUnknown`.|atlcom. h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Cette classe implémente `IUnknown` pour un objet agrégé ou non agrégé.|atlcom. h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.|atlcomcli. h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Cette classe fournit une base pour les classes de pointeurs intelligents utilisant des routines de mémoire basées sur COM.|atlcomcli. h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.|atlcomcli. h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs d’interface COM.|atlcoll. h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Cette classe est un wrapper pour la `SAFEARRAY Data Type` structure.|atlsafe. h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Cette classe est un wrapper pour une `SAFEARRAYBOUND` structure.|atlsafe. h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Cette classe gère la sélection des threads pour la classe [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase. h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Cette classe fournit des méthodes pour incrémenter et décrémenter la valeur d’une variable.|atlbase. h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Cette classe implémente une interface détachée.|atlcom. h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Cette classe stocke `IUnknown` des pointeurs et est conçue pour être utilisée comme paramètre de la classe de modèle [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom. h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Cette classe encapsule le type VARIANT, en fournissant un membre indiquant le type de données stockées.|atlcomcli. h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Cette classe implémente une fenêtre contenue dans un autre objet.|atlwin. h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines de mémoire CRT.|atlcore. h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas CRT.|atlmem. h|
|[CDacl](../../atl/reference/cdacl-class.md)|Cette classe est un wrapper pour une structure DACL (liste de contrôle d’accès discrétionnaire).|ATLSecurity. h|
|[CDebugReportHook, classe](../../atl/reference/cdebugreporthook-class.md)|Utilisez cette classe pour envoyer des rapports de débogage à un canal nommé.|atlutil. h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Cette classe fournit deux fonctions statiques pour la conversion de caractères entre majuscules et minuscules.|atlcoll. h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Cette classe fournit des fonctions de comparaison d’éléments par défaut.|atlcoll. h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Cette classe fournit des méthodes et des fonctions par défaut pour une classe de collection.|atlcoll. h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Cette classe fournit une fonction statique pour le calcul des valeurs de hachage.|atlcoll. h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Cette classe fournit des méthodes pour créer une boîte de dialogue modale ou non modale.|atlwin. h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Cette classe fournit des méthodes qui prennent en charge le chaînage dynamique des tables des messages.|atlwin. h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Cette classe est utilisée par les classes de collection pour fournir des méthodes et des fonctions pour les opérations de déplacement, de copie, de comparaison et de hachage.|atlcoll. h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Cette classe fournit des méthodes de copie et de déplacement par défaut pour une classe de collection.|atlcoll. h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Cette classe fournit des méthodes pour notifier le récepteur du conteneur en ce qui concerne les modifications des propriétés de contrôle.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas global Win32.|atlmem. h|
|[CHandle](../../atl/reference/chandle-class.md)|Cette classe fournit des méthodes pour créer et utiliser un objet descripteur.|atlbase. h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Classe de pointeur intelligent pour la gestion des pointeurs de tas.|atlcore. h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Cette classe constitue la base de plusieurs classes de pointeur Smart Heap.|atlcore. h|
|[CHeapPtrElementTraits, classe](../../atl/reference/cheapptrelementtraits-class.md)|Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs de tas.|atlcoll. h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.|atlcoll. h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Offre une prise en charge améliorée des bitmaps, notamment la possibilité de charger et d’enregistrer des images au format JPEG, GIF, BMP et PNG (Portable Network Graphics).|atlimage. h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.|atlcoll. h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.|atlcoll. h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas locales Win32.|atlmem. h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Cette classe permet d’accéder aux tables des messages d’un objet par un autre objet.|atlwin. h|
|[CNonStatelessWorker, classe](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes d’un pool de threads et les passe à un objet de travail créé et détruit à chaque requête.|atlutil. h|
|[CNoWorkerThread, classe](../../atl/reference/cnoworkerthread-class.md)|Utilisez cette classe comme argument pour les classes `MonitorClass` de cache de paramètres de modèle si vous souhaitez désactiver la maintenance de cache dynamique.|atlutil. h|
|[CPathT, classe](../../atl/reference/cpatht-class.md)|Cette classe représente un chemin d’accès.|atlpath. h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Cette classe fournit des méthodes et des fonctions par défaut pour une classe de collection composée de types de données primitifs.|atlcoll. h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Cette classe représente un objet de descripteur de sécurité d’objet privé.|ATLSecurity. h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Cette classe représente une structure de mappage à l’aide d’une arborescence binaire rouge-noir.|atlcoll. h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Cette classe représente une structure de mappage qui permet à chaque clé d’être associée à plusieurs valeurs, à l’aide d’une arborescence binaire rouge-noir.|atlcoll. h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Cette classe fournit des méthodes pour créer et utiliser une arborescence rouge-noir.|atlcoll. h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Cette classe fournit des méthodes pour manipuler des entrées dans le registre système.|atlbase. h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Cette classe fournit la fonction de création d’un thread CRT. Utilisez cette classe si le thread utilise des fonctions CRT.|atlbase. h|
|[CSacl](../../atl/reference/csacl-class.md)|Cette classe est un wrapper pour une structure SACL (liste de contrôle d’accès système).|ATLSecurity. h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Cette classe est un wrapper léger pour la `SECURITY_ATTRIBUTES` structure.|ATLSecurity. h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Cette classe est un wrapper pour la `SECURITY_DESCRIPTOR` structure.|ATLSecurity. h|
|[CSid](../../atl/reference/csid-class.md)|Cette classe est un wrapper pour une `SID` structure (identificateur de sécurité).|ATLSecurity. h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Cette classe fournit des méthodes pour gérer un tableau simple.|atlsimpcoll. h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Cette classe est une application d’assistance pour la classe [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Cette classe est une application d’assistance pour la classe [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Cette classe implémente une boîte de dialogue modale de base.|atlwin. h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Cette classe fournit la prise en charge d’un tableau de mappage simple.|atlsimpcoll. h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Cette classe est une application d’assistance pour la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Cette classe est une application d’assistance pour la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Cette classe fournit des méthodes pour implémenter un objet de nœud de composant logiciel enfichable.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Cette classe fournit des méthodes pour implémenter un objet de page de propriétés de composant logiciel enfichable.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Cette classe fournit des méthodes pour la prise en charge des valeurs de propriété stock.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Cette classe fournit des fonctions statiques utilisées par les `CString` classes de collection qui stockent des objets.|CStringT. h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Cette classe fournit des fonctions statiques liées aux chaînes stockées dans des objets de classe de collection. Elle est similaire à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), mais effectue des comparaisons qui ne respectent pas la casse.|atlcoll. h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Cette classe fournit des fonctions statiques liées aux chaînes stockées dans des objets de classe de collection. Les objets String sont traités comme des références.|atlcoll. h|
|[CThreadPool, classe](../../atl/reference/cthreadpool-class.md)|Cette classe fournit un pool de threads de travail qui traitent une file d’attente d’éléments de travail.|atlutil. h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Cette classe est un wrapper pour la `TOKEN_GROUPS` structure.|ATLSecurity. h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Cette classe est un wrapper pour la `TOKEN_PRIVILEGES` structure.|ATLSecurity. h|
|[CUrl, classe](../../atl/reference/curl-class.md)|Cette classe représente une URL. Elle vous permet de manipuler chaque élément de l’URL indépendamment des autres, si l’analyse d’une chaîne d’URL existante ou la génération d’une chaîne à partir de zéro.|atlutil. h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CT2AEX, CW2TEX, CW2CTEX et CT2CAEX, ainsi que les CW2A typedef.|atlconv. h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CW2CTEX et CT2CWEX, ainsi que par le CW2CW typedef.|atlconv. h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Cette classe est utilisée par les macros de conversion de chaînes CW2TEX et CT2WEX, ainsi que par le CW2W typedef.|atlconv. h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation du tas Win32.|atlmem. h|
|[CWindow](../../atl/reference/cwindow-class.md)|Cette classe fournit des méthodes pour manipuler une fenêtre.|atlwin. h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Cette classe fournit des méthodes pour la création ou la sous-classe d’une fenêtre.|atlwin. h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Cette classe fournit une méthode permettant de standardiser les styles utilisés lors de la création d’un objet Window.|atlwin. h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Cette classe fournit une méthode permettant de standardiser les styles utilisés lors de la création d’un objet Window.|atlwin. h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Cette classe fournit des méthodes pour inscrire des informations pour une classe de fenêtre.|atlwin. h|
|[CWorkerThread, classe](../../atl/reference/cworkerthread-class.md)|Cette classe crée un thread de travail ou en utilise un, attend un ou plusieurs handles d’objet de noyau et exécute une fonction cliente spécifiée lorsque l’un des descripteurs est signalé.|atlutil. h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Cette classe représente une interface à une `CreateInstance` méthode.|atlbase. h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Cette classe représente l’interface pour un gestionnaire de mémoire.|atlmem. h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Cette interface fournit des méthodes pour spécifier les caractéristiques du conteneur ou du contrôle hébergé.|atlbase. h, ATLIFace. h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Cette interface implémente des propriétés ambiantes supplémentaires pour un contrôle hébergé.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Cette interface fournit des méthodes pour manipuler un contrôle et son objet hôte.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet hôte.|atlbase. h, ATLIFace. h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Cette classe fournit des méthodes utilisées par une classe de collection.|atlcom. h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Cette classe implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom. h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Cette classe implémente un point de connexion.|atlcom. h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Cette classe fournit des méthodes pour la prise en charge de la Uniform Data Transfer et de la gestion des connexions.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Cette classe fournit une implémentation par défaut pour `IDispatch` la partie d’une interface double.|atlcom. h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Cette classe fournit des implémentations des `IDispatch` méthodes.|atlcom. h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Cette classe fournit des implémentations des `IDispatch` méthodes, sans obtenir les informations de type d’une bibliothèque de types.|atlcom. h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Interface au moteur d’analyse et de rendu HTML de Microsoft.|atlbase. h, ATLIFace. h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Cette classe définit une interface d’énumérateur basée sur C++ une collection de bibliothèques standard.|atlcom. h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Cette classe fournit une implémentation par défaut de `IObjectSafety` l’interface pour permettre à un client de récupérer et de définir les niveaux de sécurité d’un objet.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Cette classe fournit des méthodes qui permettent à un objet de communiquer avec son site.|atlcom. h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Cette classe fournit une implémentation par défaut de `IOleControl` l’interface et `IUnknown`implémente.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Cette classe fournit des méthodes pour aider à la communication entre un contrôle sur place et son conteneur.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Cette classe implémente `IUnknown` et fournit des méthodes qui permettent à un contrôle sans fenêtre de recevoir des messages de fenêtre et de participer à des opérations de glisser-déplacer.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Cette classe implémente `IUnknown` et est l’interface principale par le biais de laquelle un conteneur communique avec un contrôle.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Cette classe implémente `IUnknown` et permet à un client d’accéder aux informations contenues dans les pages de propriétés d’un objet.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Cette classe implémente `IUnknown` et permet à un objet d’enregistrer ses propriétés dans un conteneur de propriétés fourni par le client.|atlcom. h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Cette classe implémente l’interface [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .|atlcom. h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .|atlcom. h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Cette classe implémente `IUnknown` et les méthodes de l’interface [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Cette classe expose l’interface [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) comme une interface sortante sur un objet connectable.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Cette classe implémente `IUnknown` et hérite de l’implémentation par défaut de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Cette classe fournit une implémentation par défaut des méthodes [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) et [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .|atlcom. h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Cette classe combine l’initialisation des contrôles des conteneurs en un seul appel.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Cette classe fournit une implémentation par défaut de `IServiceProvider` l’interface.|atlcom. h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .|atlcom. h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Cette classe fournit une implémentation par défaut de `ISupportErrorInfo Interface` l’interface et peut être utilisée quand une seule interface génère des erreurs sur un objet.|atlcom. h|
|[IThreadPoolConfig, interface](../../atl/reference/ithreadpoolconfig-interface.md)|Cette interface fournit des méthodes pour configurer un pool de threads.|atlutil. h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Cette classe implémente `IUnknown` et fournit des implémentations par défaut des interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)et [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .|atlctl.h|
|[IWorkerThreadClient, interface](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`est l’interface implémentée par les clients de la classe [CWorkerThread](../../atl/reference/cworkerthread-class.md) .|atlutil. h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Cette classe fournit des wrappers `CreateWindow` pour `CreateWindowEx`et.|atlwin. h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Cette classe d’adaptateur d’arguments `RECT` permet de passer des pointeurs ou des références à une fonction implémentée en termes de pointeurs.|atlwin. h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Cette classe d’adaptateur d’arguments permet de passer des noms de ressource (LPCTSTRs) ou des ID de ressource (UINT) à une fonction sans obliger l’appelant à convertir l’ID en une chaîne à l’aide de la macro MAKEINTRESOURCE.|atlwin. h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Cette classe fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread n’utilise pas de fonctions CRT.|atlbase. h|

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Typedef](../../atl/reference/atl-typedefs.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
