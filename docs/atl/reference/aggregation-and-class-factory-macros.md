---
description: 'En savoir plus sur : agrégation et macros de fabrique de classes'
title: Agrégation et macros de fabrique de classes
ms.date: 08/12/2020
f1_keywords:
- ATLCOM/ATL::DECLARE_AGGREGATABLE
- ATLCOM/ATL::DECLARE_CLASSFACTORY
- ATLCOM/ATL::DECLARE_CLASSFACTORY_EX
- ATLCOM/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/ATL::DECLARE_NOT_AGGREGATABLE
- ATLCOM/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_POLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/ATL::DECLARE_VIEW_STATUS
- ATLDEF/ATL::DECLARE_AGGREGATABLE
- ATLDEF/ATL::DECLARE_CLASSFACTORY
- ATLDEF/ATL::DECLARE_CLASSFACTORY_EX
- ATLDEF/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLDEF/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLDEF/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLDEF/ATL::DECLARE_NOT_AGGREGATABLE
- ATLDEF/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_POLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLDEF/ATL::DECLARE_VIEW_STATUS
- ATLCOM/DECLARE_AGGREGATABLE
- ATLCOM/DECLARE_CLASSFACTORY
- ATLCOM/DECLARE_CLASSFACTORY_EX
- ATLCOM/DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/DECLARE_NOT_AGGREGATABLE
- ATLCOM/DECLARE_ONLY_AGGREGATABLE
- ATLCOM/DECLARE_POLY_AGGREGATABLE
- ATLCOM/DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/DECLARE_VIEW_STATUS
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
- DECLARE_AGGREGATABLE
- DECLARE_CLASSFACTORY
- DECLARE_CLASSFACTORY_EX
- DECLARE_CLASSFACTORY_AUTO_THREAD
- DECLARE_CLASSFACTORY_SINGLETON
- DECLARE_GET_CONTROLLING_UNKNOWN
- DECLARE_NOT_AGGREGATABLE
- DECLARE_ONLY_AGGREGATABLE
- DECLARE_POLY_AGGREGATABLE
- DECLARE_PROTECT_FINAL_CONSTRUCT
- DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 7aa62bfe8e87b9e7923dfe1de1f28b6acdba595e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158957"
---
# <a name="aggregation-and-class-factory-macros"></a>Agrégation et macros de fabrique de classes

Ces macros offrent des moyens de contrôler l’agrégation et de déclarer des fabriques de classes.

| Macro | Description |
|--|--|
| [DECLARE_AGGREGATABLE](#declare_aggregatable) | Déclare que votre objet peut être agrégé (valeur par défaut). |
| [DECLARE_CLASSFACTORY](#declare_classfactory) | Déclare que la fabrique de classe est [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), la fabrique de classe ATL par défaut. |
| [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) | Déclare votre objet de fabrique de classe en tant que fabrique de classe. |
| [DECLARE_CLASSFACTORY2](#declare_classfactory2) | Déclare [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) comme fabrique de classe. |
| [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) | Déclare [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) comme fabrique de classe. |
| [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) | Déclare [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) comme fabrique de classe. |
| [DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown) | Déclare une fonction virtuelle `GetControllingUnknown` . |
| [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) | Déclare que votre objet ne peut pas être agrégé. |
| [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) | Déclare que votre objet doit être agrégé. |
| [DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable) | Vérifie la valeur de l’externe inconnu et déclare votre objet pouvant être agrégé ou non agrégé, selon le cas. |
| [DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct) | Empêche la suppression de l’objet externe pendant la construction d’un objet interne. |
| [DECLARE_VIEW_STATUS](#declare_view_status) | Spécifie les indicateurs VIEWSTATUS pour le conteneur. |

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a> DECLARE_AGGREGATABLE

Spécifie que votre objet peut être agrégé.

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de la classe que vous définissez comme pouvant être agrégée.

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) contient cette macro pour spécifier le modèle d’agrégation par défaut. Pour remplacer cette valeur par défaut, spécifiez la macro [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) ou [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) dans la définition de votre classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a> DECLARE_CLASSFACTORY

Déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe.

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) utilise cette macro pour déclarer la fabrique de classe par défaut pour votre objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a> CComClassFactory, classe

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Notes

`CComClassFactory` implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , qui contient des méthodes pour créer un objet d’un CLSID particulier, ainsi que le verrouillage de la fabrique de classe en mémoire pour permettre la création plus rapide de nouveaux objets. `IClassFactory` doit être implémentée pour chaque classe que vous inscrivez dans le registre système et pour laquelle vous affectez un CLSID.

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare `CComClassFactory` comme fabrique de classe par défaut. Pour remplacer cette valeur par défaut, spécifiez l’une des macros DECLARE_CLASSFACTORY *xxx* dans votre définition de classe. Par exemple, la macro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) utilise la classe spécifiée pour la fabrique de classe :

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

La définition de classe ci-dessus spécifie que `CMyClassFactory` sera utilisé comme fabrique de classe par défaut de l’objet. `CMyClassFactory` doit dériver de `CComClassFactory` et substituer `CreateInstance` .

ATL fournit trois autres macros qui déclarent une fabrique de classes :

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Utilise [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), qui contrôle la création via une licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Utilise [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), qui crée des objets dans plusieurs cloisonnements.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Utilise [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), qui construit un objet [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) unique.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a> DECLARE_CLASSFACTORY_EX

Déclare `cf` comme fabrique de classe.

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Paramètres

*Trésor*<br/>
dans Nom de la classe qui implémente votre objet de fabrique de classes.

### <a name="remarks"></a>Notes

Le paramètre *CF* doit dériver de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et substituer la `CreateInstance` méthode.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , qui spécifie `CComClassFactory` comme fabrique de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_EX dans la définition de classe de votre objet, vous remplacez cette valeur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a> DECLARE_CLASSFACTORY2

Déclare [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) comme fabrique de classe.

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Paramètres

*Profil*<br/>
dans Classe qui implémente `VerifyLicenseKey` , `GetLicenseKey` et `IsLicenseValid` .

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY2 dans la définition de classe de votre objet, vous remplacez cette valeur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a> CComClassFactory2, classe

Cette classe implémente l’interface [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Paramètres

*licence*<br/>
Classe qui implémente les fonctions statiques suivantes :

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Notes

`CComClassFactory2` implémente l’interface [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , qui est une extension de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` contrôle la création d’objets via une licence. Une fabrique de classes s’exécutant sur un ordinateur sous licence peut fournir une clé de licence d’exécution. Cette clé de licence permet à une application d’instancier des objets lorsqu’une licence d’ordinateur complet n’existe pas.

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Pour utiliser `CComClassFactory2` , spécifiez la macro [DECLARE_CLASSFACTORY2](#declare_classfactory2) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, le paramètre de modèle de `CComClassFactory2` , doit implémenter les fonctions statiques `VerifyLicenseKey` , `GetLicenseKey` et `IsLicenseValid` . Voici un exemple de classe de licence simple :

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` dérive de et de la `CComClassFactory2Base` *licence*. `CComClassFactory2Base`, à son tour, dérive `IClassFactory2` de **et \< CComGlobalsThreadModel > CComObjectRootEx**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a> DECLARE_CLASSFACTORY_AUTO_THREAD

Déclare [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) comme fabrique de classe.

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_AUTO_THREAD dans la définition de classe de votre objet, vous remplacez cette valeur par défaut.

Lorsque vous créez des objets dans plusieurs cloisonnements (dans un serveur hors processus), ajoutez DECLARE_CLASSFACTORY_AUTO_THREAD à votre classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a> CComClassFactoryAutoThread, classe

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) et permet la création d’objets dans plusieurs cloisonnements.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Notes

`CComClassFactoryAutoThread` est semblable à [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), mais permet la création d’objets dans plusieurs cloisonnements. Pour tirer parti de cette prise en charge, dérivez votre module EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Pour utiliser `CComClassFactoryAutoThread` , spécifiez la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a> DECLARE_CLASSFACTORY_SINGLETON

Déclare [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) comme fabrique de classe.

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
dans Nom de votre objet de classe.

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_SINGLETON dans la définition de classe de votre objet, vous remplacez cette valeur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a> CComClassFactorySingleton, classe

Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe.

`CComClassFactorySingleton` dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique. Chaque appel à la `CreateInstance` méthode interroge simplement cet objet pour obtenir un pointeur d’interface.

### <a name="remarks"></a>Notes

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare `CComClassFactory` comme fabrique de classe par défaut. Pour utiliser `CComClassFactorySingleton` , spécifiez la macro [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a> DECLARE_GET_CONTROLLING_UNKNOWN

Déclare une fonction virtuelle `GetControllingUnknown` .

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Notes

Ajoutez cette macro à votre objet si vous recevez le message d’erreur du compilateur qui `GetControllingUnknown` n’est pas défini (par exemple, dans `CComAggregateCreator` ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a> DECLARE_NOT_AGGREGATABLE

Spécifie que votre objet ne peut pas être agrégé.

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de l’objet de classe que vous définissez comme ne pouvant pas être agrégé.

### <a name="remarks"></a>Notes

DECLARE_NOT_AGGREGATABLE entraîne `CreateInstance` le renvoi d’une erreur (CLASS_E_NOAGGREGATION) si une tentative d’agrégation est effectuée sur votre objet.

Par défaut, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contient la macro [DECLARE_AGGREGATABLE](#declare_aggregatable) , qui spécifie que votre objet peut être agrégé. Pour remplacer ce comportement par défaut, incluez DECLARE_NOT_AGGREGATABLE dans votre définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a> DECLARE_ONLY_AGGREGATABLE

Spécifie que votre objet doit être agrégé.

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de l’objet de classe que vous définissez comme pouvant être agrégé uniquement.

### <a name="remarks"></a>Notes

DECLARE_ONLY_AGGREGATABLE provoque une erreur (E_FAIL) si une tentative est effectuée pour `CoCreate` votre objet en tant qu’objet non agrégé.

Par défaut, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contient la macro [DECLARE_AGGREGATABLE](#declare_aggregatable) , qui spécifie que votre objet peut être agrégé. Pour remplacer ce comportement par défaut, incluez DECLARE_ONLY_AGGREGATABLE dans votre définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a> DECLARE_POLY_AGGREGATABLE

Spécifie qu’une instance **de \<** *x* **> CComPolyObject** est créée lors de la création de votre objet.

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de l’objet de classe que vous définissez comme pouvant être agrégé ou non agrégé.

### <a name="remarks"></a>Notes

Pendant la création, la valeur de l’externe Unknown est vérifiée. Si la valeur est NULL, `IUnknown` est implémenté pour un objet non agrégé. Si le inconnu externe n’est pas NULL, `IUnknown` est implémenté pour un objet agrégé.

L’avantage d’utiliser DECLARE_POLY_AGGREGATABLE est que vous évitez que `CComAggObject` et `CComObject` dans votre module ne gèrent les cas agrégés et non agrégés. Un seul `CComPolyObject` objet gère les deux cas. Cela signifie qu’une seule copie de la vtable et une copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, l’utilisation de `CComPolyObject` peut entraîner une taille de module légèrement supérieure, car elle n’est pas optimisée pour un objet agrégé ou non agrégé, comme c’est le cas `CComAggObject` et `CComObject` .

La macro DECLARE_POLY_AGGREGATABLE est automatiquement déclarée dans votre objet si vous utilisez l’Assistant contrôle ATL pour créer un contrôle total.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a> DECLARE_PROTECT_FINAL_CONSTRUCT

Empêche la suppression de votre objet si (pendant [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) l’objet agrégé interne incrémente le nombre de références, puis décrémente le nombre à 0.

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a> DECLARE_VIEW_STATUS

Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL pour spécifier les indicateurs VIEWSTATUS au conteneur.

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Paramètres

*statusFlags*<br/>
dans Indicateurs VIEWSTATUS. Pour obtenir la liste des indicateurs, consultez [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
