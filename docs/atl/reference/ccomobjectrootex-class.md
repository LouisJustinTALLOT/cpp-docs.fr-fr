---
title: Classe CComObjectRootEx
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
ms.openlocfilehash: 87e2d7dca81221f4fac2a5189ecb0effbdceddc2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747904"
---
# <a name="ccomobjectrootex-class"></a>Classe CComObjectRootEx

Cette classe fournit des méthodes pour gérer la gestion du nombre de références d’objets pour les objets non agrégatés et agrégés.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Paramètres

*ThreadModel (en)*<br/>
La classe dont les méthodes implémentent le modèle de threading souhaité. Vous pouvez explicitement choisir le modèle de threading en définissant *ThreadModel* à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Vous pouvez accepter le modèle de thread par défaut du serveur en définissant *ThreadModel* sur [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Constructeur.|
|[InternalAddRef (en)](#internaladdref)|Incréments le nombre de références pour un objet non agrégaté.|
|[InternalRelease (en)](#internalrelease)|Décrément le nombre de références pour un objet non agrégaté.|
|[Verrouiller](#lock)|Si le modèle de thread est relu plusieurs fois, obtient la propriété d’un objet de section critique.|
|[Déverrouiller](#unlock)|Si le modèle de thread est relu plusieurs fois, libère la propriété d’un objet de section critique.|

### <a name="ccomobjectrootbase-methods"></a>Méthodes CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Remplacer votre classe pour effectuer toute initialisation requise par votre objet.|
|[FinalRelease (finalRelease)](#finalrelease)|Remplacer votre classe pour effectuer tout nettoyage requis par votre objet.|
|[OuterAddRef (en)](#outeraddref)|Incréments le nombre de références pour un objet agrégé.|
|[ExtérieureQueryInterface](#outerqueryinterface)|Délégués à `IUnknown` l’extérieur d’un objet agrégé.|
|[OuterRelease (Ensease)](#outerrelease)|Décrément le nombre de références pour un objet agrégé.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[InterneQueryInterface](#internalqueryinterface)|Délégués à `IUnknown` l’objet non-agrégaté.|
|[ObjectMain](#objectmain)|Appelé lors de l’initialisation du module et la terminaison pour les classes dérivées énumérées dans la carte de l’objet.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_dwRef](#m_dwref)|Avec `m_pOuterUnknown`, une partie d’un syndicat. Utilisé lorsque l’objet n’est pas `AddRef` agrégé `Release`pour tenir le nombre de références de et .|
|[m_pOuterUnknown](#m_pouterunknown)|Avec `m_dwRef`, une partie d’un syndicat. Utilisé lorsque l’objet est agrégé pour tenir un pointeur à l’inconnu externe.|

## <a name="remarks"></a>Notes

`CComObjectRootEx`gère la gestion du compte de référence des objets pour les objets non agrégés et agrégés. Il détient le nombre de références d’objet si votre objet n’est pas agrégé, et tient le pointeur à l’inconnu externe si votre objet est agrégé. Pour les objets `CComObjectRootEx` agrégés, des méthodes peuvent être utilisées pour gérer l’échec de l’objet intérieur à construire, et pour protéger l’objet extérieur contre la suppression lorsque les interfaces intérieures sont libérées ou l’objet intérieur est supprimé.

Une classe qui implémente `CComObjectRootEx` un serveur COM doit hériter de [ou CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Si votre définition de classe spécifie la macro `CComPolyObject<CYourClass>` `IClassFactory::CreateInstance` [DECLARE_POLY_AGGREGATABLE,](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) ATL crée un exemple de quand est appelé. Pendant la création, la valeur de l’inconnu extérieur est vérifiée. S’il est `IUnknown` NULL, est implémenté pour un objet non agrégaté. Si l’inconnu externe `IUnknown` n’est pas NULL, est implémenté pour un objet agrégé.

Si votre classe ne spécifie pas la DECLARE_POLY_AGGREGATABLE `CAggComObject<CYourClass>` macro, ATL crée `CComObject<CYourClass>` un exemple d’objets agrégés ou d’une instance d’objets non agrégatés.

L’avantage `CComPolyObject` de l’utilisation `CComAggObject` est `CComObject` que vous évitez d’avoir les deux et dans votre module pour gérer les cas agrégés et non-agrégatés. Un `CComPolyObject` seul objet gère les deux cas. Par conséquent, une seule copie de la table v et une copie des fonctions existent dans votre module. Si votre vtable est grand, cela peut diminuer considérablement la taille de votre module. Cependant, si votre vtable `CComPolyObject` est petite, l’utilisation peut entraîner une taille de module légèrement plus grande `CComAggObject` parce `CComObject`qu’elle n’est pas optimisée pour un objet agrégé ou non agrégat, comme le sont et .

Si votre objet est agrégé, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est implémenté par `CComAggObject` ou `CComPolyObject`. Ces classes `QueryInterface` `AddRef`déléguent `CComObjectRootEx`, `OuterQueryInterface` `OuterAddRef`et `Release` `OuterRelease` appelle à 's , , et de transmettre à l’inconnu extérieur. En règle générale, vous remplacez `CComObjectRootEx::FinalConstruct` dans votre classe `CComObjectRootEx::FinalRelease` pour créer des objets agrégés, et remplacez-vous pour libérer tous les objets agrégés.

Si votre objet n’est pas agrégé, `IUnknown` est implémenté par `CComObject` ou `CComPolyObject`. Dans ce cas, `QueryInterface` `AddRef`les `Release` appels à `CComObjectRootEx`, `InternalQueryInterface`et `InternalAddRef`sont `InternalRelease` délégués à 's , , et d’effectuer les opérations réelles.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx

Le constructeur initialise le nombre de références à 0.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct

Vous pouvez remplacer cette méthode dans votre classe dérivée pour effectuer toute initialisation requise pour votre objet.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Retour S_OK sur le succès ou l’une des valeurs HRESULT erreur standard.

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalConstruct` il suffit de retourner S_OK.

Il y a des avantages `FinalConstruct` à effectuer l’initialisation dans plutôt que le constructeur de votre classe :

- Vous ne pouvez pas retourner un code de statut à partir `FinalConstruct`d’un constructeur, mais vous pouvez retourner un HRESULT au moyen de la valeur de retour de '. Lorsque des objets de votre classe sont créés à l’aide de l’usine de classe standard fournie par ATL, cette valeur de retour est propagée au client COM vous permettant de leur fournir des informations détaillées sur les erreurs.

- Vous ne pouvez pas appeler des fonctions virtuelles à travers le mécanisme de fonction virtuelle à partir du constructeur d’une classe. Appeler une fonction virtuelle du constructeur d’une classe se traduit par un appel statiquement résolu à la fonction telle qu’elle est définie à ce moment-là dans la hiérarchie successorale. Les appels vers des fonctions virtuelles pures entraînent des erreurs de liaison.

   Votre classe n’est pas la classe la plus dérivée dans la hiérarchie de l’héritage — elle s’appuie sur une classe dérivée fournie par ATL pour fournir une partie de sa fonctionnalité. Il y a de fortes chances que votre initialisation ait besoin d’utiliser les fonctionnalités fournies par cette classe (c’est certainement vrai lorsque les objets de votre classe ont besoin d’agréger d’autres objets), mais le constructeur de votre classe n’a aucun moyen d’accéder à ces fonctionnalités. Le code de construction de votre classe est exécuté avant que la classe la plus dérivée ne soit entièrement construite.

   Cependant, `FinalConstruct` est appelé immédiatement après la classe la plus dérivée est entièrement construit vous permettant d’appeler des fonctions virtuelles et d’utiliser la mise en œuvre de comptage de référence fournie par ATL.

### <a name="example"></a>Exemple

Typiquement, remplacer cette méthode dans `CComObjectRootEx` la classe dérivée de créer des objets agrégés. Par exemple :

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Si la construction échoue, vous pouvez retourner une erreur. Vous pouvez également utiliser la macro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) pour protéger votre objet externe d’être supprimé si, pendant la création, l’objet agrégé interne incrémente le nombre de références puis décrète le nombre à 0.

Voici une façon typique de créer un agrégat :

- Ajoutez `IUnknown` un pointeur à votre objet de classe et initialisez-le à NULL dans le constructeur.

- Remplacer `FinalConstruct` pour créer l’agrégat.

- Utilisez `IUnknown` le pointeur que vous définissez comme le paramètre de la [macro COM_INTERFACE_ENTRY_AGGREGATE.](com-interface-entry-macros.md#com_interface_entry_aggregate)

- Remplacement `FinalRelease` pour libérer `IUnknown` le pointeur.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease

Vous pouvez remplacer cette méthode dans votre classe dérivée pour effectuer tout nettoyage requis pour votre objet.

```cpp
void FinalRelease();
```

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalRelease` ne fait rien.

Effectuer le `FinalRelease` nettoyage est préférable à l’ajout de code au destructeur de votre classe `FinalRelease` puisque l’objet est encore entièrement construit au point auquel est appelé. Cela vous permet d’accéder en toute sécurité aux méthodes fournies par la classe la plus dérivée. Ceci est particulièrement important pour libérer tous les objets agrégés avant la suppression.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef

Incréments le nombre de références d’un objet non agrégaté par 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic et les tests.

### <a name="remarks"></a>Notes

Si le modèle de thread `InterlockedIncrement` est relu multithreaded, est utilisé pour empêcher plus d’un thread de changer le nombre de références en même temps.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface

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
[dans] Un pointeur à l’objet qui contient `QueryInterface`la carte COM des interfaces exposées à .

*pEntries (en)*<br/>
[dans] Un pointeur `_ATL_INTMAP_ENTRY` vers la structure qui accède à une carte des interfaces disponibles.

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface spécifié en *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est `InternalQueryInterface` agrégé, ne délégue pas à l’inconnu extérieur. Vous pouvez entrer des interfaces dans la table de carte COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease

Décrète le nombre de références d’un objet non agrégaté par 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions non-debug et de débog, cette fonction retourne une valeur qui peut être utile pour le diagnostic ou les tests. La valeur exacte retournée dépend de nombreux facteurs tels que le système d’exploitation utilisé, et peut, ou peut ne pas, être le nombre de référence.

### <a name="remarks"></a>Notes

Si le modèle de thread `InterlockedDecrement` est relu multithreaded, est utilisé pour empêcher plus d’un thread de changer le nombre de références en même temps.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Lock

Si le modèle de thread est relu multithreaded, cette méthode appelle la fonction Win32 API [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread puisse prendre possession de l’objet de section critique obtenu par l’intermédiaire d’un membre de données privé.

```cpp
void Lock();
```

### <a name="remarks"></a>Notes

Lorsque le code protégé termine l’exécution, le thread doit appeler `Unlock` pour libérer la propriété de la section critique.

Si le modèle de thread est à thread unique, cette méthode ne fait rien.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx:m_dwRef

Partie d’un syndicat qui accède à quatre octets de mémoire.

```
long m_dwRef;
```

### <a name="remarks"></a>Notes

Avec `m_pOuterUnknown`, partie d’un syndicat:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet n’est pas agrégé, `AddRef` `Release` le nombre `m_dwRef`de références consulté par et est stocké dans . Si l’objet est agrégé, le pointeur de l’inconnu externe est stocké dans [m_pOuterUnknown](#m_pouterunknown).

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx:m_pOuterUnknown

Partie d’un syndicat qui accède à quatre octets de mémoire.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Notes

Avec `m_dwRef`, partie d’un syndicat:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet est agrégé, le pointeur `m_pOuterUnknown`de l’inconnu externe est stocké dans . Si l’objet n’est pas agrégé, `AddRef` `Release` le nombre de références consulté par et est stocké dans [m_dwRef](#m_dwref).

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain

Pour chaque classe répertoriée dans la carte de l’objet, cette fonction est appelée une fois lorsque le module est initialisé, et encore une fois quand il est terminé.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Paramètres

*b Démarrage*<br/>
[out] La valeur est VRAI si la classe est en cours d’initialisation; autrement FALSE.

### <a name="remarks"></a>Notes

La valeur du *paramètre bStarting* indique si le module est en cours d’initialisation ou de résiliation. La mise `ObjectMain` en œuvre par défaut de ne fait rien, mais vous pouvez remplacer cette fonction dans votre classe pour initialiser ou nettoyer les ressources que vous souhaitez allouer pour la classe. Notez `ObjectMain` que c’est appelé avant tout cas de la classe sont demandés.

`ObjectMain`est appelé à partir du point d’entrée de la DLL, de sorte que le type d’opération que la fonction d’entrée-point peut effectuer est limitée. Pour plus d’informations sur ces restrictions, voir [DLLs et Visual C 'run-time comportement de bibliothèque](../../build/run-time-library-behavior.md) et [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::OuterAddRef

Incréments le nombre de références de l’inconnu extérieur d’une agrégation.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic et les tests.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface

Récupère un pointeur indirect sur l’interface demandée.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface spécifié en *iid*, ou NULL si l’agrégation ne prend pas en charge l’interface.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::OuterRelease

Décrément le compte de référence de l’inconnu extérieur d’une agrégation.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions non-debug, retourne toujours 0. Dans les constructions de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Unlock

Si le modèle de thread est relu multithreaded, cette méthode appelle la fonction Win32 API [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), qui libère la propriété de l’objet de section critique obtenu par l’intermédiaire d’un membre de données privé.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Pour obtenir la propriété, `Lock`le fil doit appeler . Chaque appel `Lock` nécessite un `Unlock` appel correspondant pour libérer la propriété de la section critique.

Si le modèle de thread est à thread unique, cette méthode ne fait rien.

## <a name="see-also"></a>Voir aussi

[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Classe CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
