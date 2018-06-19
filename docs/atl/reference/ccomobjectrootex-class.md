---
title: Classe de CComObjectRootEx | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b147f0ad3f1a54c2ae640b6bf2426bcddf060b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365979"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx (classe)
Cette classe fournit des méthodes pour gérer la gestion du nombre de référence objet pour les objets brutes et non agrégées et agrégées.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>Paramètres  
 `ThreadModel`  
 La classe dont les méthodes implémentent le modèle de thread. Vous pouvez choisir explicitement le modèle de thread en définissant `ThreadModel` à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Vous pouvez accepter le modèle de thread du serveur par défaut en définissant `ThreadModel` à [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|Constructeur.|  
|[InternalAddRef](#internaladdref)|Incrémente le décompte de références pour un objet brutes et non agrégée.|  
|[InternalRelease](#internalrelease)|Décrémente le décompte de références pour un objet brutes et non agrégée.|  
|[verrou](#lock)|Si le modèle de thread est multithread, obtienne la propriété d’un objet de section critique.|  
|[déverrouiller](#unlock)|Si le modèle de thread est multithread, mises à jour de la propriété d’un objet de section critique.|  
  
### <a name="ccomobjectrootbase-methods"></a>Méthodes CComObjectRootBase  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|Remplacer dans votre classe pour effectuer toute initialisation requise par votre objet.|  
|[FinalRelease](#finalrelease)|Remplacer dans votre classe d’effectuer tout nettoyage requis par votre objet.|  
|[OuterAddRef](#outeraddref)|Incrémente le décompte de références pour un objet.|  
|[OuterQueryInterface](#outerqueryinterface)|Délégués à l’extérieur **IUnknown** d’un objet.|  
|[OuterRelease](#outerrelease)|Décrémente le décompte de références pour un objet.|  
  
### <a name="static-functions"></a>Fonctions statiques  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|Délègue à la **IUnknown** d’un objet brutes et non agrégée.|  
|[ObjectMain](#objectmain)|Appelée pendant l’initialisation du module et l’arrêt pour les classes dérivées répertorié dans le mappage de l’objet.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|Avec `m_pOuterUnknown`dans le cadre d’une union. Utilisé lors de l’objet n’est pas agrégée pour contenir le nombre de référence `AddRef` et **version**.|  
|[m_pOuterUnknown](#m_pouterunknown)|Avec `m_dwRef`dans le cadre d’une union. Utilisé lors de l’objet est agrégée pour contenir un pointeur vers l’inconnu extérieur.|  
  
## <a name="remarks"></a>Notes  
 `CComObjectRootEx` gère la gestion du nombre de référence objet pour les objets brutes et non agrégées et agrégées. Il conserve le décompte de références d’objet si votre objet n’est pas agrégée et maintient le pointeur vers l’inconnu extérieur si votre objet est en cours d’agrégation. Pour les objets agrégées, `CComObjectRootEx` méthodes peuvent être utilisées pour gérer l’échec de l’objet interne pour construire et à protéger l’objet externe d’une suppression lors de la publication des interfaces internes ou de l’objet interne est supprimé.  
  
 Une classe qui implémente un serveur COM doit hériter de `CComObjectRootEx` ou [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Si votre définition de classe spécifie les [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) macro, ATL crée une instance de **CComPolyObject\<CYourClass >** lorsque **IClassFactory :: CreateInstance** est appelée. Lors de la création, la valeur de l’inconnu extérieur est vérifiée. S’il s’agit **NULL**, **IUnknown** est implémenté pour un objet brutes et non agrégée. Si l’inconnu extérieur n’est pas **NULL**, **IUnknown** est implémenté pour un objet.  
  
 Si votre classe ne spécifie pas le `DECLARE_POLY_AGGREGATABLE` macro, ATL crée une instance de **CAggComObject\<CYourClass >** pour les objets regroupés en agrégats ou une instance de **CComObject\<CYourClass >** pour les objets brutes et non agrégées.  
  
 L’avantage d’utiliser `CComPolyObject` est que vous n’avez pas à la fois `CComAggObject` et `CComObject` dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Par conséquent, qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car il n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.  
  
 Si votre objet est agrégée, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) est implémentée par `CComAggObject` ou `CComPolyObject`. Ces classes déléguer `QueryInterface`, `AddRef`, et **version** appelle à `CComObjectRootEx`de `OuterQueryInterface`, `OuterAddRef`, et `OuterRelease` à inconnu externe. En règle générale, vous substituez `CComObjectRootEx::FinalConstruct` dans votre classe pour créer des objets agrégées et remplacer `CComObjectRootEx::FinalRelease` pour libérer les agrégées des objets.  
  
 Si votre objet n’est pas agrégée, **IUnknown** est implémentée par `CComObject` ou `CComPolyObject`. Dans ce cas, les appels à `QueryInterface`, `AddRef`, et **version** sont déléguées à `CComObjectRootEx`de `InternalQueryInterface`, `InternalAddRef`, et `InternalRelease` pour effectuer les opérations réelles.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx  
 Le constructeur initialise le décompte de références à 0.  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct  
 Vous pouvez substituer cette méthode dans votre classe dérivée pour effectuer toute initialisation requise pour votre objet.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourner `S_OK` sur la réussite ou l’un de l’erreur standard `HRESULT` valeurs.  
  
### <a name="remarks"></a>Notes  
 Par défaut, `CComObjectRootEx::FinalConstruct` retourne simplement `S_OK`.  
  
 Présente des avantages pour effectuer l’initialisation dans `FinalConstruct` plutôt que le constructeur de la classe :  
  
-   Vous ne peut pas retourner un code d’état à partir d’un constructeur, mais vous pouvez retourner une `HRESULT` au moyen de `FinalConstruct`de valeur de retour. Lors de votre classe d’objets sont créés à l’aide de la fabrique de classe standard fournie par ATL, cette valeur de retour est propagée vers le client COM qui vous permet de leur fournir des informations d’erreur détaillées.  
  
-   Vous ne pouvez pas appeler des fonctions virtuelles via le mécanisme de fonction virtuelle à partir du constructeur d’une classe. Appel de fonction virtuelle à partir du constructeur d’une classe provoque l’appel à la fonction résolu statiquement qu’elle est définie à ce stade dans la hiérarchie d’héritage. Les appels aux fonctions virtuelles pures entraînent des erreurs de l’éditeur de liens.  
  
     Votre classe n’est pas la classe la plus dérivée dans la hiérarchie d’héritage, il s’appuie sur une classe dérivée fournie par ATL pour fournir certaines de ses fonctionnalités. Il est probable que l’initialisation de votre devrez utiliser les fonctionnalités fournies par cette classe (il s’agit certainement true lorsque les objets de votre classe doivent regrouper d’autres objets), mais le constructeur dans votre classe n’a aucun moyen pour accéder à ces fonctionnalités. Le code de construction pour votre classe est exécuté avant que la classe la plus dérivée est entièrement construite.  
  
     Toutefois, `FinalConstruct` est appelée immédiatement après le plus dérivé classe est entièrement construit, ce qui vous permet d’appeler des fonctions virtuelles et d’utiliser l’implémentation de comptage de références fournie par ATL.  
  
### <a name="example"></a>Exemple  
 En règle générale, substituez cette méthode dans la classe dérivée de `CComObjectRootEx` créer n’importe lequel agrégées des objets. Par exemple :  
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 Si la construction échoue, vous pouvez retourner une erreur. Vous pouvez également utiliser la macro [macro DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) pour protéger votre objet externe d’être supprimé si, lors de la création, l’objet d’agrégation interne incrémente le décompte de références puis le décrémente le nombre de 0.  
  
 Voici le moyen le plus simple de créer un agrégat :  
  
-   Ajouter un **IUnknown** pointeur à votre classe de l’objet et l’initialiser à **NULL** dans le constructeur.  
  
-   Substituer `FinalConstruct` pour créer l’agrégat.  
  
-   Utilisez le **IUnknown** pointeur que vous avez défini en tant que paramètre à la [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) (macro).  
  
-   Substituer `FinalRelease` pour libérer le **IUnknown** pointeur.  
  
##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease  
 Vous pouvez substituer cette méthode dans votre classe dérivée pour effectuer tout nettoyage nécessaire pour votre objet.  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, `CComObjectRootEx::FinalRelease` n’exécute aucune opération.  
  
 Effectuer un nettoyage dans `FinalRelease` est préférable à l’ajout de code pour le destructeur de votre classe, car l’objet est toujours entièrement construit au point auquel `FinalRelease` est appelée. Cela vous permet de vous permet d’accéder en toute sécurité les méthodes fournies par la classe la plus dérivée. Cela est particulièrement important pour la libération de tous les objets agrégées avant la suppression.  
  
##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef  
 Incrémente le décompte de références d’un objet non regroupées en agrégats de 1.  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic et de test.  
  
### <a name="remarks"></a>Notes  
 Si le modèle de thread est multithread, **InterlockedIncrement** est utilisé pour empêcher plusieurs threads de modifier le nombre de références en même temps.  
  
##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `pThis`  
 [in] Un pointeur vers l’objet qui contient le mappage COM des interfaces exposées à `QueryInterface`.  
  
 `pEntries`  
 [in] Un pointeur vers le **_ATL_INTMAP_ENTRY** structure qui accède à un mappage des interfaces disponibles.  
  
 `iid`  
 [in] Le GUID de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface spécifié dans `iid`, ou **NULL** si l’interface est introuvable.  
  
### <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
### <a name="remarks"></a>Notes  
 `InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégée, `InternalQueryInterface` ne délègue pas à inconnu externe. Vous pouvez entrer des interfaces dans la table de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou une de ses variantes.  
  
##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease  
 Décrémente le décompte de références d’un objet brutes et non agrégée par 1.  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les deux sans débogage et les versions debug, cette fonction retourne une valeur qui peut être utile pour les tests de diagnostic ou de test. La valeur exacte retournée dépend de nombreux facteurs tels que le système d’exploitation utilisé et peut ou non, être le décompte de références.  
  
### <a name="remarks"></a>Notes  
 Si le modèle de thread est multithread, **InterlockedDecrement** est utilisé pour empêcher plusieurs threads de modifier le nombre de références en même temps.  
  
##  <a name="lock"></a>  CComObjectRootEx::Lock  
 Si le modèle de thread est multithread, cette méthode appelle la fonction API Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), qui attend jusqu'à ce que le thread peut prendre possession de l’objet de section critique obtenues via une donnée membre privée.  
  
```
void Lock();
```  
  
### <a name="remarks"></a>Notes  
 Le code protégé après l’exécution, le thread doit appeler `Unlock` pour libérer la possession de la section critique.  
  
 Si le modèle de thread est monothread, cette méthode ne fait rien.  
  
##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef  
 Partie d’une union qui accède à quatre octets de mémoire.  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>Notes  
 Avec `m_pOuterUnknown`dans le cadre d’une union :  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Si l’objet n’est pas agrégée, le nombre de références accessibles par `AddRef` et **version** est stocké dans `m_dwRef`. Si l’objet est agrégée, le pointeur vers l’inconnu extérieur est stocké dans [m_pOuterUnknown](#m_pouterunknown).  
  
##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown  
 Partie d’une union qui accède à quatre octets de mémoire.  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>Notes  
 Avec `m_dwRef`dans le cadre d’une union :  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Si l’objet est agrégée, le pointeur vers l’inconnu extérieur est stocké dans `m_pOuterUnknown`. Si l’objet n’est pas agrégée, le nombre de références accessibles par `AddRef` et **version** est stocké dans [m_dwRef](#m_dwref).  
  
##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain  
 Pour chaque classe répertoriée dans le [de mappage des objets](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f), cette fonction est appelée une fois lorsque le module est initialisé, et à nouveau une fois celui-ci est terminé.  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>Paramètres  
 `bStarting`  
 [out] La valeur est **true** si la classe est initialisé ; sinon **false**.  
  
### <a name="remarks"></a>Notes  
 La valeur de le `bStarting` paramètre indique si le module est initialisé ou arrêtée. L’implémentation par défaut de `ObjectMain` ne fait rien, mais vous pouvez remplacer cette fonction dans votre classe d’initialiser ou de nettoyer les ressources que vous souhaitez allouer pour la classe. Notez que `ObjectMain` est appelée avant que toutes les instances de la classe sont demandées.  
  
 `ObjectMain` est appelé à partir du point d’entrée de la DLL, par conséquent, le type d’opération que la fonction de point d’entrée peut effectuer est restreint. Pour plus d’informations sur ces restrictions, consultez [DLL et Visual C++ comportement de la bibliothèque Runtime](../../build/run-time-library-behavior.md) et [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef  
 Incrémente le décompte de références d’inconnu externe d’une agrégation.  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic et de test.  
  
##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface  
 Récupère un pointeur indirect vers l’interface demandée.  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface spécifié dans `iid`, ou **NULL** si celle-ci ne prend pas en charge l’interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease  
 Décrémente le décompte de références inconnu externe d’une agrégation.  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions non debug, retourne toujours 0. Dans les versions debug, retourne une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
##  <a name="unlock"></a>  CComObjectRootEx::Unlock  
 Si le modèle de thread est multithread, cette méthode appelle la fonction API Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), l’approprier les versions de l’objet de section critique obtenues via une donnée membre privée.  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>Notes  
 Pour obtenir la propriété, le thread doit appeler `Lock`. Chaque appel à `Lock` nécessite un appel correspondant à `Unlock` pour libérer la possession de la section critique.  
  
 Si le modèle de thread est monothread, cette méthode ne fait rien.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Classe de CComObject](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject (classe)](../../atl/reference/ccompolyobject-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
