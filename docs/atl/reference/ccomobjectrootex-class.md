---
title: CComObjectRootEx (classe)
ms.date: 11/04/2016
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
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417928"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx (classe)

Cette classe fournit des méthodes pour gérer la gestion du nombre de références d’objet pour les objets non agrégés et agrégés.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Paramètres

*ThreadModel*<br/>
Classe dont les méthodes implémentent le modèle de thread souhaité. Vous pouvez choisir explicitement le modèle de thread en affectant à *ThreadModel* la valeur [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Vous pouvez accepter le modèle de thread par défaut du serveur en définissant *ThreadModel* sur [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Constructeur.|
|[Internaladdref,](#internaladdref)|Incrémente le décompte de références pour un objet non agrégé.|
|[InternalRelease,](#internalrelease)|Décrémente le décompte de références pour un objet non agrégé.|
|[Verrouiller](#lock)|Si le modèle de thread est multithread, obtient la propriété d’un objet de section critique.|
|[Bloquer](#unlock)|Si le modèle de thread est multithread, libère la propriété d’un objet de section critique.|

### <a name="ccomobjectrootbase-methods"></a>Méthodes CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Substituez dans votre classe pour effectuer toute initialisation requise par votre objet.|
|[FinalRelease](#finalrelease)|Substituez dans votre classe pour effectuer tout nettoyage requis par votre objet.|
|[OuterAddRef](#outeraddref)|Incrémente le décompte de références pour un objet agrégé.|
|[OuterQueryInterface](#outerqueryinterface)|Délègue au `IUnknown` externe d’un objet agrégé.|
|[OuterRelease](#outerrelease)|Décrémente le décompte de références pour un objet agrégé.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Délègue à la `IUnknown` d’un objet qui n’est pas agrégé.|
|[ObjectMain](#objectmain)|Appelé pendant l’initialisation et l’arrêt du module pour les classes dérivées listées dans la table des objets.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_dwRef](#m_dwref)|Avec `m_pOuterUnknown`, partie d’une Union. Utilisé lorsque l’objet n’est pas agrégé pour contenir le nombre de références de `AddRef` et `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|Avec `m_dwRef`, partie d’une Union. Utilisé lorsque l’objet est agrégé pour contenir un pointeur vers le externe inconnu.|

## <a name="remarks"></a>Notes

`CComObjectRootEx` gère la gestion du décompte des références d’objet pour les objets non agrégés et agrégés. Il contient le nombre de références de l’objet si votre objet n’est pas agrégé et contient le pointeur vers le externe inconnu si votre objet est en cours d’agrégation. Pour les objets agrégés, `CComObjectRootEx` méthodes peuvent être utilisées pour gérer l’échec de la construction de l’objet interne, et pour protéger l’objet externe de la suppression lorsque des interfaces internes sont libérées ou que l’objet interne est supprimé.

Une classe qui implémente un serveur COM doit hériter de `CComObjectRootEx` ou [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Si votre définition de classe spécifie la macro [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) , ATL crée une instance de `CComPolyObject<CYourClass>` lors de l’appel de `IClassFactory::CreateInstance`. Pendant la création, la valeur de l’externe Unknown est vérifiée. Si la valeur est NULL, `IUnknown` est implémentée pour un objet non agrégé. Si la valeur inconnue externe n’est pas NULL, `IUnknown` est implémentée pour un objet agrégé.

Si votre classe ne spécifie pas la macro DECLARE_POLY_AGGREGATABLE, ATL crée une instance de `CAggComObject<CYourClass>` pour les objets agrégés ou une instance de `CComObject<CYourClass>` pour les objets non agrégés.

L’avantage d’utiliser `CComPolyObject` est que vous ne pouvez pas avoir à la fois `CComAggObject` et `CComObject` dans votre module pour gérer les cas agrégés et non agrégés. Un objet `CComPolyObject` unique gère les deux cas. Par conséquent, une seule copie de la vtable et une copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, l’utilisation de `CComPolyObject` peut entraîner une taille de module légèrement supérieure, car elle n’est pas optimisée pour un objet agrégé ou non agrégé, comme c’est le cas `CComAggObject` et `CComObject`.

Si votre objet est agrégé, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est implémenté par `CComAggObject` ou `CComPolyObject`. Ces classes délèguent les appels `QueryInterface`, `AddRef`et `Release` aux `OuterQueryInterface`, `OuterAddRef`et `OuterRelease` de `CComObjectRootEx`pour les transférer vers l’extérieur inconnu. En règle générale, vous substituez `CComObjectRootEx::FinalConstruct` dans votre classe pour créer des objets agrégés et substituez `CComObjectRootEx::FinalRelease` pour libérer des objets agrégés.

Si votre objet n’est pas agrégé, `IUnknown` est implémenté par `CComObject` ou `CComPolyObject`. Dans ce cas, les appels à `QueryInterface`, `AddRef`et `Release` sont délégués à la `InternalQueryInterface`, `InternalAddRef`et `InternalRelease` de `CComObjectRootEx`pour effectuer les opérations réelles.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx :: CComObjectRootEx

Le constructeur initialise le décompte de références à 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>CComObjectRootEx :: FinalConstruct

Vous pouvez substituer cette méthode dans votre classe dérivée pour effectuer toute initialisation requise pour votre objet.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ou l’une des valeurs HRESULT de l’erreur standard.

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalConstruct` retourne simplement S_OK.

L’initialisation dans `FinalConstruct` plutôt que le constructeur de votre classe présente des avantages :

- Vous ne pouvez pas retourner de code d’État à partir d’un constructeur, mais vous pouvez retourner un HRESULT au moyen de la valeur de retour de `FinalConstruct`. Lorsque des objets de votre classe sont créés à l’aide de la fabrique de classes standard fournie par ATL, cette valeur de retour est propagée vers le client COM, ce qui vous permet de fournir des informations d’erreur détaillées.

- Vous ne pouvez pas appeler des fonctions virtuelles via le mécanisme de fonction virtuelle à partir du constructeur d’une classe. L’appel d’une fonction virtuelle à partir du constructeur d’une classe entraîne un appel résolu statiquement à la fonction, tel qu’il est défini à ce stade dans la hiérarchie d’héritage. Les appels aux fonctions virtuelles pures génèrent des erreurs de l’éditeur de liens.

   Votre classe n’est pas la classe la plus dérivée dans la hiérarchie d’héritage ; elle s’appuie sur une classe dérivée fournie par ATL pour fournir certaines de ses fonctionnalités. Il y a de bonnes chances que votre initialisation doive utiliser les fonctionnalités fournies par cette classe (cela est certainement vrai lorsque les objets de votre classe doivent agréger d’autres objets), mais que le constructeur de votre classe n’a aucun moyen d’accéder à ces fonctionnalités. Le code de construction de votre classe est exécuté avant la construction complète de la classe la plus dérivée.

   Toutefois, `FinalConstruct` est appelée immédiatement après la construction complète de la classe la plus dérivée, ce qui vous permet d’appeler des fonctions virtuelles et d’utiliser l’implémentation de comptage de références fournie par ATL.

### <a name="example"></a>Exemple

En règle générale, substituez cette méthode dans la classe dérivée de `CComObjectRootEx` pour créer des objets agrégés. Par exemple :

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Si la construction échoue, vous pouvez retourner une erreur. Vous pouvez également utiliser la macro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) pour empêcher la suppression de votre objet externe si, lors de la création, l’objet agrégé interne incrémente le nombre de références, puis décrémente le nombre à 0.

Voici un moyen classique de créer un agrégat :

- Ajoutez un pointeur `IUnknown` à votre objet de classe et initialisez-le sur la valeur NULL dans le constructeur.

- Remplacez `FinalConstruct` pour créer l’agrégat.

- Utilisez le pointeur de `IUnknown` que vous avez défini comme paramètre pour la macro [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) .

- Substituez `FinalRelease` pour libérer le pointeur `IUnknown`.

##  <a name="finalrelease"></a>CComObjectRootEx :: FinalRelease

Vous pouvez substituer cette méthode dans votre classe dérivée pour effectuer tout nettoyage requis pour votre objet.

```
void FinalRelease();
```

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalRelease` ne fait rien.

Il est préférable d’effectuer un nettoyage dans `FinalRelease` plutôt que d’ajouter du code au destructeur de votre classe, étant donné que l’objet est toujours entièrement construit au point auquel `FinalRelease` est appelé. Cela vous permet d’accéder en toute sécurité aux méthodes fournies par la classe la plus dérivée. Ceci est particulièrement important pour libérer des objets agrégés avant la suppression.

##  <a name="internaladdref"></a>CComObjectRootEx :: Internaladdref,

Incrémente de 1 le décompte de références d’un objet non agrégé.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics et les tests.

### <a name="remarks"></a>Notes

Si le modèle de thread est multithread, `InterlockedIncrement` est utilisé pour empêcher plusieurs threads de modifier le décompte de références en même temps.

##  <a name="internalqueryinterface"></a>CComObjectRootEx :: InternalQueryInterface

Récupère un pointeur vers l'interface demandée.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*pThis*<br/>
dans Pointeur vers l’objet qui contient la table COM des interfaces exposées à `QueryInterface`.

*pEntries*<br/>
dans Pointeur vers la structure `_ATL_INTMAP_ENTRY` qui accède à une carte des interfaces disponibles.

*vaut*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface spécifié dans *IID*, ou null si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégé, `InternalQueryInterface` ne délègue pas à l’objet externe inconnu. Vous pouvez entrer des interfaces dans le tableau de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes.

##  <a name="internalrelease"></a>CComObjectRootEx :: InternalRelease,

Décrémente de 1 le décompte de références d’un objet non agrégé.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions sans débogage et débogage, cette fonction retourne une valeur qui peut être utile pour les diagnostics ou les tests. La valeur exacte retournée dépend de nombreux facteurs, tels que le système d’exploitation utilisé, et peuvent, ou non, être le nombre de références.

### <a name="remarks"></a>Notes

Si le modèle de thread est multithread, `InterlockedDecrement` est utilisé pour empêcher plusieurs threads de modifier le décompte de références en même temps.

##  <a name="lock"></a>CComObjectRootEx :: Lock

Si le modèle de thread est multithread, cette méthode appelle la fonction d’API Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread puisse prendre possession de l’objet de section critique obtenu par le biais d’un membre de données privé.

```
void Lock();
```

### <a name="remarks"></a>Notes

Une fois l’exécution du code protégé terminée, le thread doit appeler `Unlock` pour libérer la propriété de la section critique.

Si le modèle de thread est à thread unique, cette méthode n’a aucun effet.

##  <a name="m_dwref"></a>CComObjectRootEx :: m_dwRef

Partie d’une Union qui accède à quatre octets de mémoire.

```
long m_dwRef;
```

### <a name="remarks"></a>Notes

Avec `m_pOuterUnknown`, partie d’une Union :

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet n’est pas agrégé, le nombre de références accessibles par `AddRef` et `Release` est stocké dans `m_dwRef`. Si l’objet est agrégé, le pointeur vers l’objet Unknown externe est stocké dans [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>CComObjectRootEx :: m_pOuterUnknown

Partie d’une Union qui accède à quatre octets de mémoire.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Notes

Avec `m_dwRef`, partie d’une Union :

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet est agrégé, le pointeur vers l’objet Unknown externe est stocké dans `m_pOuterUnknown`. Si l’objet n’est pas agrégé, le nombre de références accessibles par `AddRef` et `Release` est stocké dans [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>CComObjectRootEx :: ObjectMain

Pour chaque classe figurant dans le mappage d’objets, cette fonction est appelée une fois lorsque le module est initialisé, et à nouveau lorsqu’elle est terminée.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Paramètres

*bStarting*<br/>
à La valeur est TRUE si la classe est en cours d’initialisation ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La valeur du paramètre *bStarting* indique si le module est en cours d’initialisation ou de fin. L’implémentation par défaut de `ObjectMain` ne fait rien, mais vous pouvez remplacer cette fonction dans votre classe pour initialiser ou nettoyer les ressources que vous souhaitez allouer pour la classe. Notez que `ObjectMain` est appelé avant qu’une instance de la classe ne soit demandée.

`ObjectMain` est appelée à partir du point d’entrée de la DLL, le type d’opération que la fonction de point d’entrée peut exécuter est donc restreint. Pour plus d’informations sur ces restrictions, consultez [dll et C++ comportement de la bibliothèque Runtime](../../build/run-time-library-behavior.md) et [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>CComObjectRootEx :: OuterAddRef

Incrémente le décompte de références de l’externe inconnu d’une agrégation.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics et les tests.

##  <a name="outerqueryinterface"></a>CComObjectRootEx :: OuterQueryInterface

Récupère un pointeur indirect vers l’interface demandée.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface spécifié dans *IID*, ou null si l’agrégation ne prend pas en charge l’interface.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="outerrelease"></a>CComObjectRootEx :: OuterRelease

Décrémente le décompte de références de l’externe inconnu d’une agrégation.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions sans débogage, retourne toujours 0. Dans les versions Debug, retourne une valeur qui peut être utile pour les diagnostics ou les tests.

##  <a name="unlock"></a>CComObjectRootEx :: Unlock

Si le modèle de thread est multithread, cette méthode appelle la fonction d’API Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), qui libère la propriété de l’objet de section critique obtenu par le biais d’un membre de données privé.

```
void Unlock();
```

### <a name="remarks"></a>Notes

Pour obtenir la propriété, le thread doit appeler `Lock`. Chaque appel à `Lock` nécessite un appel correspondant à `Unlock` pour libérer la propriété de la section critique.

Si le modèle de thread est à thread unique, cette méthode n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
