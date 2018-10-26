---
title: CComObjectRootEx, classe | Microsoft Docs
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
ms.openlocfilehash: 413485bc7675fbc68f2c224ceefdd0f552538eb9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076982"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx, classe

Cette classe fournit des méthodes pour gérer la gestion du nombre de référence objet pour les objets non regroupées en agrégats et agrégées.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Paramètres

*ThreadModel*<br/>
La classe dont les méthodes implémentent le modèle de thread souhaité. Vous pouvez choisir explicitement le modèle de thread en définissant *ThreadModel* à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), ou [ CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Vous pouvez accepter le modèle de thread du serveur par défaut en définissant *ThreadModel* à [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Constructeur.|
|[InternalAddRef](#internaladdref)|Incrémente le décompte de références pour un objet non regroupées en agrégats.|
|[InternalRelease](#internalrelease)|Décrémente le décompte de références pour un objet non regroupées en agrégats.|
|[Verrou](#lock)|Si le modèle de thread est multithread, obtienne la propriété d’un objet de section critique.|
|[Déverrouiller](#unlock)|Si le modèle de thread est multithread, libère la propriété d’un objet de section critique.|

### <a name="ccomobjectrootbase-methods"></a>Méthodes CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Remplacer dans votre classe pour effectuer toute initialisation requise par votre objet.|
|[FinalRelease](#finalrelease)|Remplacer dans votre classe pour effectuer tout nettoyage requis par votre objet.|
|[OuterAddRef](#outeraddref)|Incrémente le décompte de références pour un objet agrégé.|
|[OuterQueryInterface](#outerqueryinterface)|Les délégués à l’extérieur `IUnknown` d’un objet agrégé.|
|[OuterRelease](#outerrelease)|Décrémente le décompte de références pour un objet agrégé.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Délègue à la `IUnknown` d’un objet non regroupées en agrégats.|
|[ObjectMain](#objectmain)|Appelée pendant l’initialisation du module et l’arrêt pour les classes dérivées répertoriées dans le plan de l’objet.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_dwRef](#m_dwref)|Avec `m_pOuterUnknown`, qui fait partie d’une union. Utilisé lors de l’objet n’est pas agrégée pour contenir le décompte de références `AddRef` et `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|Avec `m_dwRef`, qui fait partie d’une union. Utilisé lors de l’objet est agrégée pour contenir un pointeur vers l’inconnu extérieur.|

## <a name="remarks"></a>Notes

`CComObjectRootEx` gère la gestion du nombre de référence objet pour les objets non regroupées en agrégats et agrégées. Elle contient le nombre de références d’objet si votre objet n’est pas agrégée et conserve le pointeur vers l’inconnu externe si votre objet est en cours d’agrégation. Pour les objets agrégées, `CComObjectRootEx` méthodes peuvent être utilisées pour gérer l’échec de l’objet interne pour construire et à protéger l’objet externe à partir de suppression lors de la publication des interfaces internes ou l’objet interne est supprimé.

Une classe qui implémente un serveur COM doit hériter de `CComObjectRootEx` ou [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Si votre définition de classe spécifie les [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) macro, ATL crée une instance de `CComPolyObject<CYourClass>` lorsque `IClassFactory::CreateInstance` est appelée. Lors de la création, la valeur de l’inconnu extérieur est vérifiée. Si sa valeur est NULL, `IUnknown` est implémentée pour un objet non regroupées en agrégats. Si l’inconnu extérieur n’est pas NULL, `IUnknown` est implémentée pour un objet agrégé.

Si votre classe ne spécifie pas de la macro DECLARE_POLY_AGGREGATABLE, ATL crée une instance de `CAggComObject<CYourClass>` pour objets agrégées ou d’une instance de `CComObject<CYourClass>` pour les objets non regroupées en agrégats.

L’avantage d’utiliser `CComPolyObject` est d’éviter d’avoir à la fois `CComAggObject` et `CComObject` dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Par conséquent, qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car elle n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.

Si votre objet est agrégée, [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) est implémentée par `CComAggObject` ou `CComPolyObject`. Ces classes déléguer `QueryInterface`, `AddRef`, et `Release` appelle à `CComObjectRootEx`de `OuterQueryInterface`, `OuterAddRef`, et `OuterRelease` pour transférer vers inconnu externe. En règle générale, vous substituez `CComObjectRootEx::FinalConstruct` dans votre classe pour créer des objets agrégées et remplacer `CComObjectRootEx::FinalRelease` libère aucune agrégé des objets.

Si votre objet n’est pas agrégée, `IUnknown` est implémentée par `CComObject` ou `CComPolyObject`. Dans ce cas, les appels à `QueryInterface`, `AddRef`, et `Release` sont déléguées à `CComObjectRootEx`de `InternalQueryInterface`, `InternalAddRef`, et `InternalRelease` pour effectuer les opérations réelles.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

Le constructeur initialise le décompte de références à 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

Vous pouvez remplacer cette méthode dans votre classe dérivée pour effectuer toute initialisation nécessaire pour votre objet.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur la réussite ou un de l’erreur standard de valeurs HRESULT.

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalConstruct` simplement retourne S_OK.

Il existe des avantages à l’exécution de l’initialisation dans `FinalConstruct` plutôt que le constructeur de votre classe :

- Vous ne pouvez pas retourner un code d’état à partir d’un constructeur, mais vous pouvez retourner une valeur HRESULT au moyen de `FinalConstruct`de valeur de retour. Lors de votre classe d’objets sont créés à l’aide de la fabrique de classe standard fournie par ATL, cette valeur de retour est propagée au client COM, ce qui vous permet de fournir les informations d’erreur détaillé.

- Vous ne pouvez pas appeler des fonctions virtuelles via le mécanisme de fonction virtuelle à partir du constructeur d’une classe. Appel de fonction virtuelle à partir du constructeur d’une classe entraîne un appel résolu statiquement à la fonction car il est défini à ce stade dans la hiérarchie d’héritage. Les appels aux fonctions virtuelles pures entraînent des erreurs de l’éditeur de liens.

   Votre classe n’est pas la classe la plus dérivée dans la hiérarchie d’héritage, il s’appuie sur une classe dérivée, fournie par ATL pour fournir certaines de ses fonctionnalités. Il est probable que l’initialisation de votre devrez utiliser les fonctionnalités fournies par cette classe (il s’agit certainement true lorsque les objets de votre classe doivent regrouper d’autres objets), mais le constructeur dans votre classe n’a aucun moyen d’accéder à ces fonctionnalités. Le code de construction pour votre classe est exécuté avant que la classe la plus dérivée est entièrement construite.

   Toutefois, `FinalConstruct` est appelée immédiatement après les plus dérivées classe est entièrement construite, ce qui vous permet d’appeler des fonctions virtuelles et d’utiliser l’implémentation de comptage de références fournie par ATL.

### <a name="example"></a>Exemple

En règle générale, substituez cette méthode dans la classe dérivée de `CComObjectRootEx` permettant de créer des agrégées des objets. Exemple :

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Si la construction échoue, vous pouvez retourner une erreur. Vous pouvez également utiliser la macro [macro DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) pour protéger votre objet externe d’être supprimé si, lors de la création, l’objet interne agrégée incrémente le décompte de références puis décrémente le nombre de 0.

Voici une manière classique pour créer un agrégat :

- Ajouter un `IUnknown` pointeur à votre classe d’objet et l’initialiser avec la valeur NULL dans le constructeur.

- Substituer `FinalConstruct` pour créer l’agrégat.

- Utilisez le `IUnknown` pointeur que vous avez défini en tant que paramètre à la [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) macro.

- Substituer `FinalRelease` pour libérer le `IUnknown` pointeur.

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

Vous pouvez remplacer cette méthode dans votre classe dérivée pour effectuer tout nettoyage requis pour votre objet.

```
void FinalRelease();
```

### <a name="remarks"></a>Notes

Par défaut, `CComObjectRootEx::FinalRelease` n’a aucun effet.

Nettoyage dans `FinalRelease` est préférable à l’ajout de code pour le destructeur de votre classe dans la mesure où l’objet est toujours entièrement construit au point auquel `FinalRelease` est appelée. Cela vous permet d’accéder en toute sécurité les méthodes fournies par la classe la plus dérivée à. Cela est particulièrement important de libérer tous les objets agrégées avant la suppression.

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

Incrémente le décompte de références d’un objet non regroupées en agrégats de 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour les diagnostics et de test.

### <a name="remarks"></a>Notes

Si le modèle de thread est multithread, `InterlockedIncrement` est utilisé pour empêcher la modification du nombre de référence en même temps plusieurs threads.

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

*pThis*<br/>
[in] Un pointeur vers l’objet qui contient le mappage COM des interfaces exposées à `QueryInterface`.

*pEntries*<br/>
[in] Un pointeur vers le `_ATL_INTMAP_ENTRY` structure qui accède à une carte des interfaces disponibles.

*IID*<br/>
[in] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface spécifié dans *iid*, ou NULL si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

`InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégée, `InternalQueryInterface` ne pas déléguer à inconnu externe. Vous pouvez entrer des interfaces dans la table de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou une de ses variantes.

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

Décrémente le décompte de références d’un objet non regroupées en agrégats par 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les deux sans débogage et les versions debug, cette fonction retourne une valeur qui peut être utile pour les diagnostics ou de test. La valeur exacte retournée dépend de nombreux facteurs tels que le système d’exploitation utilisé et peut ou non, être le décompte de références.

### <a name="remarks"></a>Notes

Si le modèle de thread est multithread, `InterlockedDecrement` est utilisé pour empêcher la modification du nombre de référence en même temps plusieurs threads.

##  <a name="lock"></a>  CComObjectRootEx::Lock

Si le modèle de thread est multithread, cette méthode appelle la fonction API Win32 [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread peut prendre possession de l’objet de section critique obtenu via une donnée membre privée.

```
void Lock();
```

### <a name="remarks"></a>Notes

Le code protégé fin de l’exécution, le thread doit appeler `Unlock` libère la propriété de la section critique.

Si le modèle de thread est monothread, cette méthode ne fait rien.

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

Partie d’une union qui accède à quatre octets de mémoire.

```
long m_dwRef;
```

### <a name="remarks"></a>Notes

Avec `m_pOuterUnknown`, qui fait partie d’une union :

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet n’est pas agrégée, le décompte de références accessibles `AddRef` et `Release` est stocké dans `m_dwRef`. Si l’objet est agrégée, le pointeur vers l’inconnu extérieur est stocké dans [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

Partie d’une union qui accède à quatre octets de mémoire.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Notes

Avec `m_dwRef`, qui fait partie d’une union :

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si l’objet est agrégée, le pointeur vers l’inconnu extérieur est stocké dans `m_pOuterUnknown`. Si l’objet n’est pas agrégée, le décompte de références accessibles `AddRef` et `Release` est stocké dans [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

Pour chaque classe répertorié dans la table d’objets, cette fonction est appelée une fois que lorsque le module est initialisé, et à nouveau lorsqu’elle est arrêtée.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Paramètres

*bStarting*<br/>
[out] La valeur est TRUE si l’initialisation de la classe ; Sinon, FALSE.

### <a name="remarks"></a>Notes

La valeur de la *bStarting* paramètre indique si le module est initialisé ou s’est arrêté. L’implémentation par défaut de `ObjectMain` ne fait rien, mais vous pouvez remplacer cette fonction dans votre classe pour initialiser ou de nettoyer les ressources que vous souhaitez allouer pour la classe. Notez que `ObjectMain` est appelée avant que toutes les instances de la classe sont demandés.

`ObjectMain` est appelée à partir du point d’entrée de la DLL, par conséquent, le type d’opération que la fonction de point d’entrée peut effectuer est restreint. Pour plus d’informations sur ces restrictions, consultez [DLL et Visual C++ comportement de la bibliothèque du run-time](../../build/run-time-library-behavior.md) et [DllMain](/windows/desktop/Dlls/dllmain).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

Incrémente le décompte de références de l’inconnu externe d’une agrégation.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour les diagnostics et de test.

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

Récupère un pointeur indirect vers l’interface demandée.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
[in] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface spécifié dans *iid*, ou NULL si l’agrégation ne prend pas en charge l’interface.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

Décrémente le décompte de références inconnu externe d’une agrégation.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions non debug retourne toujours 0. Dans les versions debug, retourne une valeur qui peut-être être utiles pour le diagnostic ou de test.

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

Si le modèle de thread est multithread, cette méthode appelle la fonction API Win32 [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), qui libère la propriété de l’objet de section critique obtenu via une donnée membre privée.

```
void Unlock();
```

### <a name="remarks"></a>Notes

Pour obtenir la propriété, le thread doit appeler `Lock`. Chaque appel à `Lock` nécessite un appel correspondant à `Unlock` libère la propriété de la section critique.

Si le modèle de thread est monothread, cette méthode ne fait rien.

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
