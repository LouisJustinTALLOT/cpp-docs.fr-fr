---
title: Macros d’entrée d’interface COM
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326677"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY Macros

Ces macros entrent les interfaces d’un objet dans sa `QueryInterface`carte COM afin qu’ils puissent être consultés par . L’ordre des entrées dans la carte COM est que les `QueryInterface`interfaces de commande seront vérifiées pour un IID correspondant pendant .

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Entre les interfaces dans la carte d’interface COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilisez cette macro pour désambiguer deux branches de l’héritage.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Utilisez cette macro pour entrer l’interface dans la carte COM et spécifier son IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Même que [COM_INTERFACE_ENTRY2](#com_interface_entry2), sauf que vous pouvez spécifier un IID différent.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Lorsque l’interface identifiée par *iid* `COM_INTERFACE_ENTRY_AGGREGATE` est interrogée `punk`pour, transmet à .|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Même que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que la requête pour tout IID entraîne le pas de transmettre la requête au *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Même que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si *le punk* est NULL, il crée automatiquement l’agrégat décrit par le *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Même que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), sauf que la requête pour tout IID entraîne le transfert de la requête au *punk*, et si *le punk* est NULL, la création automatique de l’agrégat décrit par le *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Provoque votre programme d’appeler [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) lorsque l’interface spécifiée est interrogée pour.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Enregistre les données spécifiques à l’interface pour chaque instance.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expose vos interfaces déchirantes.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Traite la carte COM de la classe de base lorsque le traitement atteint cette entrée dans la carte COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Un mécanisme général pour s’accrocher `QueryInterface` à la logique d’ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Même que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que la requête pour tout IID se traduit par un appel à *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Retourne E_NOINTERFACE et met fin au traitement de la carte COM lorsque l’interface spécifiée est demandée.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Entre les interfaces dans la carte d’interface COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom d’une interface de votre objet de classe dérive directement.

### <a name="remarks"></a>Notes

Typiquement, c’est le type d’entrée que vous utilisez le plus souvent.

### <a name="example"></a>Exemple

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Utilisez cette macro pour désambiguer deux branches de l’héritage.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom d’une interface que vous souhaitez exposer à partir de votre objet.

*x2*<br/>
[dans] Le nom de la branche d’héritage à partir de laquelle *x* est exposé.

### <a name="remarks"></a>Notes

Par exemple, si vous dérivez votre objet de `IDispatch` classe à partir `IDispatch` de deux interfaces doubles, vous exposez à l’aide d’COM_INTERFACE_ENTRY2 puisque vous pouvez être obtenu à partir de l’une ou l’autre des interfaces.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Utilisez cette macro pour entrer l’interface dans la carte COM et spécifier son IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface exposé.

*X*<br/>
[dans] Le nom de la classe dont le vtable sera exposé comme l’interface identifiée par *iid*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Même que [COM_INTERFACE_ENTRY2](#com_interface_entry2), sauf que vous pouvez spécifier un IID différent.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID que vous spécifiez pour l’interface.

*X*<br/>
[dans] Le nom d’une interface dont votre objet de classe dérive directement.

*x2*<br/>
[dans] Le nom d’une deuxième interface dont votre objet de classe dérive directement.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Lorsque l’interface identifiée par *iid* est interrogée pour, COM_INTERFACE_ENTRY_AGGREGATE en avant au *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandé.

*Punk*<br/>
[dans] Le nom `IUnknown` d’un pointeur.

### <a name="remarks"></a>Notes

Le paramètre *punk* est supposé indiquer l’inconnue intérieure d’un agrégat ou de NULL, auquel cas l’entrée est ignorée. Typiquement, vous `CoCreate` le `FinalConstruct`serait l’agrégat en .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Même que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que la requête pour tout IID entraîne le pas de transmettre la requête au *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Le nom `IUnknown` d’un pointeur.

### <a name="remarks"></a>Notes

Si la requête de l’interface échoue, le traitement de la carte COM se poursuit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Même que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si *le punk* est NULL, il crée automatiquement l’agrégat décrit par le *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandé.

*Punk*<br/>
[dans] Le nom `IUnknown` d’un pointeur. Doit être membre de la classe contenant la carte COM.

*clsid*<br/>
[dans] L’identifiant de l’agrégat qui sera créé si *le punk* est NULL.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Même que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), sauf que la requête pour tout IID entraîne le transfert de la requête au *punk*, et si *le punk* est NULL, la création automatique de l’agrégat décrit par le *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Le nom `IUnknown` d’un pointeur. Doit être membre de la classe contenant la carte COM.

*clsid*<br/>
[dans] L’identifiant de l’agrégat qui sera créé si *le punk* est NULL.

### <a name="remarks"></a>Notes

Si la requête de l’interface échoue, le traitement de la carte COM se poursuit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Provoque votre programme d’appeler [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) lorsque l’interface spécifiée est interrogée pour.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Texte utilisé pour construire l’identifiant d’interface.

### <a name="remarks"></a>Notes

L’interface IID sera construit *x* par `IID_`appending x à . Par exemple, *x* si `IPersistStorage`x est , `IID_IPersistStorage`l’IID sera .

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Enregistre les données spécifiques à l’interface pour chaque instance.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface déchirante.

*X*<br/>
[dans] Le nom de la classe implémentant l’interface.

*Punk*<br/>
[dans] Le nom `IUnknown` d’un pointeur. Doit être membre de la classe contenant la carte COM. Devrait être parasité à NULL dans le constructeur de l’objet de classe.

### <a name="remarks"></a>Notes

Si l’interface n’est pas utilisée, cela abaisse la taille globale de l’instance de votre objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Expose vos interfaces déchirantes.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface déchirante.

*X*<br/>
[dans] Le nom de la classe implémentant l’interface.

### <a name="remarks"></a>Notes

Une interface déchirante est implémentée comme un objet séparé qui est instantané chaque fois que l’interface qu’il représente est demandée. Typiquement, vous construisez votre interface comme une déchirure si l’interface est rarement utilisée, car cela enregistre un pointeur vtable dans chaque cas de votre objet principal. La déchirure est supprimée lorsque son nombre de références devient nul. La classe implémentant la déchirure `CComTearOffObjectBase` doit être dérivée et avoir sa propre carte COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Traite la carte COM de la classe de base lorsque le traitement atteint cette entrée dans la carte COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Paramètres

*Classname*<br/>
[dans] Une classe de base de l’objet actuel.

### <a name="remarks"></a>Notes

Par exemple, dans le code suivant :

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Notez que la première entrée dans la carte COM doit être une interface sur l’objet contenant la carte COM. Ainsi, vous ne pouvez pas démarrer vos entrées de carte COM avec COM_INTERFACE_ENTRY_CHAIN, ce qui provoque la recherche de la carte COM d’un autre objet au point où`COtherObject`**COM_INTERFACE_ENTRY_CHAIN)** apparaît dans la carte COM de votre objet. **COM_INTERFACE_ENTRY_CHAIN(** Si vous souhaitez d’abord rechercher la carte COM `IUnknown` d’un autre objet, ajoutez une entrée d’interface pour votre carte COM, puis enchaînez la carte COM de l’autre objet. Par exemple :

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Un mécanisme général pour s’accrocher `QueryInterface` à la logique d’ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface exposé.

*dw*<br/>
[dans] Un paramètre passé à la *func*.

*Func*<br/>
[dans] Le pointeur de fonction qui reviendra *iid*.

### <a name="remarks"></a>Notes

Si *iid* correspond à l’IID de l’interface demandée, alors la fonction spécifiée par *func* est appelée. La déclaration pour la fonction doit être la suivante:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Lorsque votre fonction `pv` est appelée, indique votre objet de classe. Le *paramètre riid* se réfère à l’interface demandée, `ppv` est le pointeur à l’endroit où la fonction doit stocker le pointeur à l’interface, et *dw* est le paramètre que vous avez spécifié dans l’entrée. La fonction \* `ppv` doit être définie à NULL et retourner E_NOINTERFACE ou S_FALSE si elle choisit de ne pas retourner une interface. Avec E_NOINTERFACE, le traitement de carte COM se termine. Avec S_FALSE, le traitement de carte COM continue, même si aucun pointeur d’interface n’a été retourné. Si la fonction renvoie un pointeur d’interface, elle doit retourner S_OK.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Même que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que la requête pour tout IID se traduit par un appel à *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Paramètres

*dw*<br/>
[dans] Un paramètre passé à la *func*.

*Func*<br/>
[dans] La fonction qui est appelée lorsque cette entrée dans la carte COM est traitée.

### <a name="remarks"></a>Notes

Toute défaillance entraînera la poursuite du traitement sur la carte COM. Si la fonction renvoie un pointeur d’interface, elle doit retourner S_OK.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Retourne E_NOINTERFACE et met fin au traitement de la carte COM lorsque l’interface spécifiée est demandée.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Texte utilisé pour construire l’identifiant d’interface.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette macro pour empêcher une interface d’être utilisée dans un cas particulier. Par exemple, vous pouvez insérer cette macro dans votre carte COM juste avant COM_INTERFACE_ENTRY_AGGREGATE_BLIND pour empêcher qu’une requête pour l’interface ne soit transmise à l’inconnu interne de l’agrégat.

L’interface IID sera construit *x* par `IID_`appending x à . Par exemple, *x* si `IPersistStorage`x est , `IID_IPersistStorage`l’IID sera .
