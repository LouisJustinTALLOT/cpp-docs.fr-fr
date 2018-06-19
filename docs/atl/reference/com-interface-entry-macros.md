---
title: Macros d’entrées d’Interface COM | Documents Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c3ba41a05813c4112c1e5dd51bfe447d2c8debf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366586"
---
# <a name="cominterfaceentry-macros"></a>Macros COM_INTERFACE_ENTRY  
 Ces macros entrer des interfaces d’un objet dans son mappage COM afin qu’ils peuvent être accessibles par `QueryInterface`. L’ordre des entrées dans le mappage COM est que les interfaces de commande ne fonctionnera pas une correspondance **IID** pendant `QueryInterface`.  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY](#com_interface_entry)|Insère des interfaces dans la table d’interface COM.|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilisez cette macro pour lever l’ambiguïté des deux branches de l’héritage.|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Utilisez cette macro pour entrer dans l’interface dans le mappage COM et spécifier son IID.|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Identique à [COM_INTERFACE_ENTRY2](#com_interface_entry2), mais vous pouvez spécifier un IID différents.|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Lorsque l’interface identifiée par `iid` est interrogée, `COM_INTERFACE_ENTRY_AGGREGATE` transfère à `punk`.|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que l’interrogation de n’importe quel IID entraîne la requête de transfert `punk`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si `punk` est **NULL**, il crée automatiquement l’agrégat décrite par le `clsid`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Identique à [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), sauf que l’interrogation de n’importe quel IID entraîne la requête de transfert `punk`et si `punk` est **NULL**, en créant automatiquement le agrégat décrite par le `clsid`.|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Entraîne l’appel de votre programme [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) lorsque l’interface spécifiée est demandé.|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Enregistre les données spécifiques à l’interface pour chaque instance.|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expose les interfaces détachables.|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Traite le mappage COM de la classe de base lorsque le traitement atteint cette entrée dans le mappage COM.|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Un mécanisme général pour se connecter à ATL `QueryInterface` logique.|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Identique à [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que l’interrogation de n’importe quel IID entraîne un appel à `func`.|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Retourne **E_NOINTERFACE** et s’arrête COM carte le traitement lorsque l’interface spécifiée est interrogée pour.|  

## <a name="requirements"></a>Spécifications
**En-tête :** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY
Insère des interfaces dans la table d’interface COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>Paramètres

x [in] nom d’une interface votre objet de classe dérive directement.

### <a name="remarks"></a>Notes
Il s’agit en général, le type d’entrée que vous utilisez le plus souvent.

### <a name="example"></a>Exemple
```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```
### <a name="requirements"></a>Spécifications
**En-tête :** atlcom.h
  
##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2  
 Utilisez cette macro pour lever l’ambiguïté des deux branches de l’héritage.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Le nom d’une interface que vous voulez exposer à partir de votre objet.  
  
 `x2`  
 [in] Le nom de la branche de l’héritage à partir de laquelle *x* est exposé.  
  
### <a name="remarks"></a>Notes  
 Par exemple, si vous dérivez votre objet de classe à partir de deux interfaces doubles, exposer `IDispatch` à l’aide de `COM_INTERFACE_ENTRY2` depuis `IDispatch` peut être obtenu à partir de l’une des interfaces.  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID  
 Utilisez cette macro pour entrer dans l’interface dans le mappage COM et spécifier son IID.  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface exposée.  
  
 *x*  
 [in] Le nom de la classe dont vtable est exposée en tant que l’interface identifiée par `iid`.  
  
 
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID  
 Identique à [COM_INTERFACE_ENTRY2](#com_interface_entry2), mais vous pouvez spécifier un IID différents.  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID que vous spécifiez pour l’interface.  
  
 *x*  
 [in] Le nom d’une interface qui dérive directement de votre objet de classe.  
  
 `x2`  
 [in] Le nom d’une deuxième interface qui dérive directement de votre objet de classe.  
  
##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE  
 Lorsque l’interface identifiée par `iid` est interrogée, `COM_INTERFACE_ENTRY_AGGREGATE` transfère à `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface demandé.  
  
 `punk`  
 [in] Le nom d’un **IUnknown** pointeur.  
  
### <a name="remarks"></a>Notes  
 Le `punk` paramètre est censé pour pointer vers l’inconnu intérieur d’un agrégat ou à **NULL**, auquel cas l’entrée est ignorée. En règle générale, vous le feriez **CoCreate** l’agrégat dans `FinalConstruct`.  
  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf que l’interrogation de n’importe quel IID entraîne la requête de transfert `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>Paramètres  
 `punk`  
 [in] Le nom d’un **IUnknown** pointeur.  
  
### <a name="remarks"></a>Notes  
 Si l’interface de requête échoue, le traitement du mappage COM se poursuit.  
  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Identique à [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), sauf si `punk` est **NULL**, il crée automatiquement l’agrégat décrite par le `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface demandé.  
  
 `punk`  
 [in] Le nom d’un **IUnknown** pointeur. Doit être un membre de la classe contenant le mappage COM.  
  
 `clsid`  
 [in] L’identificateur de l’agrégat qui sera créée si `punk` est **NULL**.  
  
### <a name="remarks"></a>Notes  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 Identique à [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), sauf que l’interrogation de n’importe quel IID entraîne la requête de transfert `punk`et si `punk` est **NULL**, en créant automatiquement le agrégat décrite par le `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>Paramètres  
 `punk`  
 [in] Le nom d’un **IUnknown** pointeur. Doit être un membre de la classe contenant le mappage COM.  
  
 `clsid`  
 [in] L’identificateur de l’agrégat qui sera créée si `punk` est **NULL**.  
  
### <a name="remarks"></a>Notes  
 Si l’interface de requête échoue, le traitement du mappage COM se poursuit.  
  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK  
 Entraîne l’appel de votre programme [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) lorsque l’interface spécifiée est demandé.  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Texte utilisé pour construire l’identificateur d’interface.  
  
### <a name="remarks"></a>Notes  
 L’interface IID sera construite en ajoutant *x* à `IID_`. Par exemple, si *x* est `IPersistStorage`, l’IID sera `IID_IPersistStorage`.  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 Enregistre les données spécifiques à l’interface pour chaque instance.  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface détachable.  
  
 *x*  
 [in] Le nom de la classe qui implémente l’interface.  
  
 `punk`  
 [in] Le nom d’un **IUnknown** pointeur. Doit être un membre de la classe contenant le mappage COM. Doit être initialisé à **NULL** dans le constructeur de l’objet de classe.  
  
### <a name="remarks"></a>Notes  
 Si l’interface n’est pas utilisé, cela réduit la taille d’instance globale de votre objet.  
  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF  
 Expose les interfaces détachables.  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface détachable.  
  
 *x*  
 [in] Le nom de la classe qui implémente l’interface.  
  
### <a name="remarks"></a>Notes  
 Une interface détachable est implémentée comme un objet distinct est instancié chaque fois que l’interface qu’il représente est interrogé pour. En règle générale, vous générez votre interface comme une détachable si l’interface est rarement utilisé, car cela permet d’économiser un pointeur vtable dans chaque instance de votre objet principal. Le détachable est supprimé lorsque son décompte de références devient égal à zéro. La classe qui implémente le détachable doit être dérivée de `CComTearOffObjectBase` et avoir sa propre table COM.  
  
  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN  
 Traite le mappage COM de la classe de base lorsque le traitement atteint cette entrée dans le mappage COM.  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>Paramètres  
 *classname*  
 [in] Classe de base de l’objet actuel.  
  
### <a name="remarks"></a>Notes  
 Par exemple, dans le code suivant :  
  
 [!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 Notez que la première entrée dans le mappage COM doit être une interface sur l’objet contenant le mappage COM. Par conséquent, vous ne peut pas démarrer vos entrées de mappage COM avec `COM_INTERFACE_ENTRY_CHAIN`, ce qui entraîne le mappage COM d’un autre objet à rechercher au point où **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** s’affiche dans le mappage COM de l’objet. Si vous souhaitez rechercher d’abord le mappage COM d’un autre objet, ajoutez une entrée de l’interface pour **IUnknown** à votre mappage COM, puis chaîne mappage COM de l’autre objet. Par exemple :  
  
 [!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC  
 Un mécanisme général pour se connecter à ATL `QueryInterface` logique.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface exposée.  
  
 `dw`  
 [in] Un paramètre transmis à la `func`.  
  
 `func`  
 [in] Le pointeur de fonction qui retourne `iid`.  
  
### <a name="remarks"></a>Notes  
 Si *iid* correspond à l’IID de l’interface de recherchés, puis la fonction spécifiée par `func` est appelée. La déclaration de la fonction doit être :  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Lorsque votre fonction est appelée, `pv` pointe vers l’objet de classe. Le `riid` paramètre fait référence à l’interface qui est interrogée, `ppv` est le pointeur vers l’emplacement dans lequel la fonction doit stocker le pointeur vers l’interface, et `dw` est le paramètre que vous avez spécifié dans l’entrée. La fonction doit définir \* `ppv` à **NULL** et retourner **E_NOINTERFACE** ou **S_FALSE** si elle choisit de ne pas renvoyer une interface. Avec **E_NOINTERFACE**, le traitement de mappage COM se termine. Avec **S_FALSE**, traitement de mappage COM se poursuit, même si aucun pointeur d’interface a été retournée. Si la fonction retourne un pointeur d’interface, elle doit retourner `S_OK`.  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND  
 Identique à [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), sauf que l’interrogation de n’importe quel IID entraîne un appel à `func`.  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>Paramètres  
 `dw`  
 [in] Un paramètre transmis à la `func`.  
  
 `func`  
 [in] La fonction est appelée lors du traitement de cette entrée dans le mappage COM.  
  
### <a name="remarks"></a>Notes  
 Tout échec entraînera le traitement de continuer sur le mappage COM. Si la fonction retourne un pointeur d’interface, elle doit retourner `S_OK`.  
  
  
##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE  
 Retourne **E_NOINTERFACE** et s’arrête COM carte le traitement lorsque l’interface spécifiée est interrogée pour.  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Texte utilisé pour construire l’identificateur d’interface.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser cette macro pour empêcher une interface d’être utilisés dans un cas particulier. Par exemple, vous pouvez insérer cette macro dans votre COM juste avant de mapper `COM_INTERFACE_ENTRY_AGGREGATE_BLIND` pour empêcher le transfert en clé inconnue interne de l’agrégat une requête pour l’interface.  
  
 L’interface IID sera construite en ajoutant *x* à `IID_`. Par exemple, si *x* est `IPersistStorage`, l’IID sera `IID_IPersistStorage`.  
  
  