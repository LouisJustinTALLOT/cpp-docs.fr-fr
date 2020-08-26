---
title: Macros d’entrée de l’interface COM
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
ms.openlocfilehash: 1358a51f6bcb65f9c54c2006a6a467cf96593b5f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834698"
---
# <a name="com_interface_entry-macros"></a>Macros COM_INTERFACE_ENTRY

Ces macros entrent les interfaces d’un objet dans sa carte COM afin qu’elles soient accessibles par `QueryInterface` . L’ordre des entrées dans la table COM est l’ordre dans lequel les interfaces sont vérifiées pour obtenir un IID correspondant pendant `QueryInterface` .

|Macro|Description|
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Entre des interfaces dans le mappage d’interface COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilisez cette macro pour lever l’ambiguïté entre deux branches d’héritage.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Utilisez cette macro pour entrer l’interface dans le mappage COM et spécifier son IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Identique à [COM_INTERFACE_ENTRY2](#com_interface_entry2), sauf que vous pouvez spécifier un autre IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Lorsque l’interface identifiée par *IID* est interrogée, est `COM_INTERFACE_ENTRY_AGGREGATE` transféré à `punk` .|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que l’interrogation de tout IID entraîne le transfert de la requête vers *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Comme [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si *punk* a la valeur null, il crée automatiquement l’agrégat décrit par le *CLSID*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Identique à [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), à l’exception du fait que l’interrogation de tous les IID entraîne le transfert de la requête vers *punk*, et si *punk* a la valeur null, crée automatiquement l’agrégat décrit par le *CLSID*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Fait en sorte que votre programme appelle [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) lorsque l’interface spécifiée est interrogée.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Enregistre les données spécifiques à l’interface pour chaque instance.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expose vos interfaces détachables.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Traite le mappage COM de la classe de base lorsque le traitement atteint cette entrée dans le mappage COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Mécanisme général de raccordement à la logique d’ATL `QueryInterface` .|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Identique à [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que l’interrogation de tout IID entraîne un appel à *Func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Retourne E_NOINTERFACE et met fin au traitement de la carte COM lors de l’interrogation de l’interface spécifiée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

Entre des interfaces dans le mappage d’interface COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom d’une interface que dérive directement de votre objet de classe.

### <a name="remarks"></a>Notes

En règle générale, il s’agit du type d’entrée que vous utilisez le plus souvent.

### <a name="example"></a>Exemple

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a> COM_INTERFACE_ENTRY2

Utilisez cette macro pour lever l’ambiguïté entre deux branches d’héritage.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom d’une interface que vous souhaitez exposer à partir de votre objet.

*x2*<br/>
dans Nom de la branche d’héritage à partir de laquelle *x* est exposé.

### <a name="remarks"></a>Notes

Par exemple, si vous dérivez votre objet de classe de deux interfaces doubles, vous exposez `IDispatch` à l’aide de COM_INTERFACE_ENTRY2, car `IDispatch` peut être obtenu à partir de l’une des interfaces.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a> COM_INTERFACE_ENTRY_IID

Utilisez cette macro pour entrer l’interface dans le mappage COM et spécifier son IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface exposée.

*x*<br/>
dans Nom de la classe dont la vtable sera exposée en tant qu’interface identifiée par *IID*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a> COM_INTERFACE_ENTRY2_IID

Identique à [COM_INTERFACE_ENTRY2](#com_interface_entry2), sauf que vous pouvez spécifier un autre IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID que vous spécifiez pour l’interface.

*x*<br/>
dans Nom d’une interface directement dérivée de votre objet de classe.

*x2*<br/>
dans Nom de la deuxième interface directement dérivée de votre objet de classe.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a> COM_INTERFACE_ENTRY_AGGREGATE

Lorsque l’interface identifiée par l' *IID* est interrogée, COM_INTERFACE_ENTRY_AGGREGATE est transféré à *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface interrogée pour.

*Punk*<br/>
dans Nom d’un `IUnknown` pointeur.

### <a name="remarks"></a>Notes

Le paramètre *punk* est supposé pointer vers l’élément interne inconnu d’un agrégat ou vers la valeur null, auquel cas l’entrée est ignorée. En général, il s’agit `CoCreate` de l’agrégat dans `FinalConstruct` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a> COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que l’interrogation de tout IID entraîne le transfert de la requête vers *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
dans Nom d’un `IUnknown` pointeur.

### <a name="remarks"></a>Notes

En cas d’échec de la requête d’interface, le traitement de la table COM continue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a> COM_INTERFACE_ENTRY_AUTOAGGREGATE

Comme [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si *punk* a la valeur null, il crée automatiquement l’agrégat décrit par le *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface interrogée pour.

*Punk*<br/>
dans Nom d’un `IUnknown` pointeur. Doit être un membre de la classe qui contient le mappage COM.

*clsid*<br/>
dans Identificateur de l’agrégat qui sera créé si *punk* a la valeur null.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a> COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Identique à [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), à l’exception du fait que l’interrogation de tous les IID entraîne le transfert de la requête vers *punk*, et si *punk* a la valeur null, crée automatiquement l’agrégat décrit par le *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
dans Nom d’un `IUnknown` pointeur. Doit être un membre de la classe qui contient le mappage COM.

*clsid*<br/>
dans Identificateur de l’agrégat qui sera créé si *punk* a la valeur null.

### <a name="remarks"></a>Notes

En cas d’échec de la requête d’interface, le traitement de la table COM continue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a> COM_INTERFACE_ENTRY_BREAK

Fait en sorte que votre programme appelle [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) lorsque l’interface spécifiée est interrogée.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Texte utilisé pour construire l’identificateur d’interface.

### <a name="remarks"></a>Notes

L’IID d’interface est construit en ajoutant *x* à `IID_` . Par exemple, si *x* est `IPersistStorage` , l’IID sera `IID_IPersistStorage` .

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a> COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Enregistre les données spécifiques à l’interface pour chaque instance.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface détachée.

*x*<br/>
dans Nom de la classe qui implémente l’interface.

*Punk*<br/>
dans Nom d’un `IUnknown` pointeur. Doit être un membre de la classe qui contient le mappage COM. Doit être initialisé avec la valeur NULL dans le constructeur de l’objet de classe.

### <a name="remarks"></a>Notes

Si l’interface n’est pas utilisée, cela réduit la taille globale de l’instance de votre objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a> COM_INTERFACE_ENTRY_TEAR_OFF

Expose vos interfaces détachables.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface détachée.

*x*<br/>
dans Nom de la classe qui implémente l’interface.

### <a name="remarks"></a>Notes

Une interface détachée est implémentée sous la forme d’un objet distinct qui est instancié chaque fois que l’interface qu’elle représente est interrogée. En règle générale, vous générez votre interface en tant que déchirement si l’interface est rarement utilisée, car cela enregistre un pointeur vtable dans chaque instance de votre objet principal. La destruction est supprimée lorsque son nombre de références est égal à zéro. La classe qui implémente le déchirement doit être dérivée de `CComTearOffObjectBase` et avoir sa propre carte com.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a> COM_INTERFACE_ENTRY_CHAIN

Traite le mappage COM de la classe de base lorsque le traitement atteint cette entrée dans le mappage COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Paramètres

*NomClasse*<br/>
dans Classe de base de l’objet actuel.

### <a name="remarks"></a>Notes

Par exemple, dans le code suivant :

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Notez que la première entrée de la table COM doit être une interface sur l’objet contenant le mappage COM. Par conséquent, vous ne pouvez pas démarrer vos entrées de mappage com avec COM_INTERFACE_ENTRY_CHAIN, ce qui entraîne la recherche de la table com d’un autre objet au point où **COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` **)** apparaît dans la carte com de votre objet. Si vous souhaitez rechercher d’abord le mappage COM d’un autre objet, ajoutez une entrée d’interface pour `IUnknown` à votre mappage com, puis chaînez le mappage com de l’autre objet. Par exemple :

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a> COM_INTERFACE_ENTRY_FUNC

Mécanisme général de raccordement à la logique d’ATL `QueryInterface` .

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface exposée.

*dw*<br/>
dans Paramètre passé à la fonction *Func*.

*func*<br/>
dans Pointeur de fonction qui retourne *IID*.

### <a name="remarks"></a>Notes

Si *IID* correspond à l’IID de l’interface interrogée pour, la fonction spécifiée par *Func* est appelée. La déclaration de la fonction doit être :

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Lorsque votre fonction est appelée, `pv` pointe vers votre objet de classe. Le paramètre *riid* fait référence à l’interface interrogée, `ppv` est le pointeur vers l’emplacement où la fonction doit stocker le pointeur vers l’interface, et *DW* est le paramètre que vous avez spécifié dans l’entrée. La fonction doit avoir la valeur \* `ppv` null et retourner E_NOINTERFACE ou S_FALSE si elle choisit de ne pas retourner une interface. Avec E_NOINTERFACE, le traitement de la carte COM se termine. Avec S_FALSE, le traitement de la carte COM se poursuit, même si aucun pointeur d’interface n’a été retourné. Si la fonction retourne un pointeur d’interface, elle doit retourner S_OK.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a> COM_INTERFACE_ENTRY_FUNC_BLIND

Identique à [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que l’interrogation de tout IID entraîne un appel à *Func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Paramètres

*dw*<br/>
dans Paramètre passé à la fonction *Func*.

*func*<br/>
dans Fonction appelée lors du traitement de cette entrée dans le mappage COM.

### <a name="remarks"></a>Notes

Tout échec entraîne la poursuite du traitement sur le mappage COM. Si la fonction retourne un pointeur d’interface, elle doit retourner S_OK.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a> COM_INTERFACE_ENTRY_NOINTERFACE

Retourne E_NOINTERFACE et met fin au traitement de la carte COM lors de l’interrogation de l’interface spécifiée.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Texte utilisé pour construire l’identificateur d’interface.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette macro pour empêcher l’utilisation d’une interface dans un cas particulier. Par exemple, vous pouvez insérer cette macro dans votre mappage COM juste avant COM_INTERFACE_ENTRY_AGGREGATE_BLIND pour empêcher la transmission d’une requête de l’interface à l’objet interne inconnu de l’agrégat.

L’IID d’interface est construit en ajoutant *x* à `IID_` . Par exemple, si *x* est `IPersistStorage` , l’IID sera `IID_IPersistStorage` .
