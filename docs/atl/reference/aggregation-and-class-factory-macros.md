---
title: Macros d’agrégation et d’usine de classe
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319334"
---
# <a name="aggregation-and-class-factory-macros"></a>Macros d’agrégation et d’usine de classe

Ces macros fournissent des moyens de contrôler l’agrégation et de déclarer les usines de classe.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Déclare que votre objet peut être agrégé (la valeur par défaut).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Déclare l’usine de classe pour être [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), l’usine de classe par défaut ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Déclare votre objet d’usine de classe pour être l’usine de classe.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Déclare [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) comme l’usine de classe.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Déclare [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) pour être l’usine de classe.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Déclare [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) comme l’usine de classe.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Déclare une `GetControllingUnknown` fonction virtuelle.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Déclare que votre objet ne peut pas être agrégé.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Déclare que votre objet doit être agrégé.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Vérifie la valeur de l’inconnu extérieur et déclare votre objet aggregatable ou non aggregatable, le cas échéant.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Protège l’objet extérieur contre la suppression lors de la construction d’un objet intérieur.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Spécifie les drapeaux VIEWSTATUS au conteneur.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Spécifie que votre objet peut être agrégé.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de la classe que vous définissez comme aggregatable.

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) contient cette macro pour spécifier le modèle d’agrégation par défaut. Pour remplacer cette valeur par défaut, spécifiez le [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) ou [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) macro dans votre définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) utilise cette macro pour déclarer l’usine de classe par défaut pour votre objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>Classe CComClassFactory

Cette classe implémente l’interface [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Notes

`CComClassFactory`implémente l’interface [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) qui contient des méthodes pour créer un objet d’un CLSID particulier, ainsi que le verrouillage de l’usine de classe dans la mémoire pour permettre de nouveaux objets à créer plus rapidement. `IClassFactory`doit être mis en œuvre pour chaque classe que vous vous inscrivez dans le registre du système et à laquelle vous attribuez un CLSID.

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) `CComClassFactory` , qui déclare que l’usine de classe par défaut. Pour remplacer cette valeur par défaut, spécifiez l’une des macros*XXX* DECLARE_CLASSFACTORY dans votre définition de classe. Par exemple, la [macro DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) utilise la classe spécifiée pour l’usine de classe :

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

La définition de classe `CMyClassFactory` ci-dessus spécifie qui sera utilisée comme usine de classe par défaut de l’objet. `CMyClassFactory`doit dériver `CComClassFactory` et `CreateInstance`passer outre .

ATL fournit trois autres macros qui déclarent une usine de classe:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Utilise [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), qui contrôle la création par le biais d’une licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Utilise [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), qui crée des objets dans plusieurs appartements.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Utilise [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), qui construit un seul objet [CComObjectGlobal.](../../atl/reference/ccomobjectglobal-class.md)

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Déclare `cf` être l’usine de classe.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
[dans] Le nom de la classe qui met en œuvre votre objet d’usine de classe.

### <a name="remarks"></a>Notes

Le paramètre *cf* doit dériver de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et remplacer la `CreateInstance` méthode.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) qui `CComClassFactory` s’asspé de l’usine de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_EX dans la définition de classe de votre objet, vous l’emportez sur ce défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Déclare [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) comme l’usine de classe.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Paramètres

*Lic*<br/>
[dans] Une classe qui `VerifyLicenseKey` `GetLicenseKey`met `IsLicenseValid`en œuvre , , et .

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY2 dans la définition de classe de votre objet, vous l’emportez sur ce défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Classe CComClassFactory2

Cette classe implémente l’interface [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Paramètres

*Licence*<br/>
Une classe qui met en œuvre les fonctions statiques suivantes :

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Notes

`CComClassFactory2`implémente l’interface [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) qui est une extension [d’IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`contrôle la création d’objets par le biais d’une licence. Une usine de classe exécutant sur une machine sous licence peut fournir une clé de licence de temps d’exécution. Cette clé de licence permet à une application d’instantané des objets lorsqu’une licence de machine complète n’existe pas.

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Pour `CComClassFactory2`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY2](#declare_classfactory2) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, le paramètre de modèle `CComClassFactory2`pour `VerifyLicenseKey` `GetLicenseKey`, `IsLicenseValid`doit implémenter les fonctions statiques , , et . Voici un exemple de classe de licence simple :

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`dérive des `CComClassFactory2Base` deux et *de la licence*. `CComClassFactory2Base`, à son tour, dérive de `IClassFactory2` et **CComObjectRootEx\< CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Déclare [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) pour être l’usine de classe.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_AUTO_THREAD dans la définition de classe de votre objet, vous l’emportez sur ce défaut.

Lorsque vous créez des objets dans plusieurs appartements (dans un serveur hors-proc), ajoutez DECLARE_CLASSFACTORY_AUTO_THREAD à votre classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Classe CComClassFactoryAutoThread

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) et permet de créer des objets dans plusieurs appartements.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Notes

`CComClassFactoryAutoThread`est similaire à [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), mais permet de créer des objets dans plusieurs appartements. Pour profiter de ce support, dérivez votre module EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Pour `CComClassFactoryAutoThread`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Déclare [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) comme l’usine de classe.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
[dans] Le nom de votre objet de classe.

### <a name="remarks"></a>Notes

[CComCoClass](../../atl/reference/ccomcoclass-class.md) comprend la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) qui spécifie [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Toutefois, en incluant la macro DECLARE_CLASSFACTORY_SINGLETON dans la définition de classe de votre objet, vous l’emportez sur ce défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Classe CComClassFactorySingleton

Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un seul objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe.

`CComClassFactorySingleton`dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un seul objet. Chaque appel `CreateInstance` à la méthode interroge simplement cet objet pour un pointeur d’interface.

### <a name="remarks"></a>Notes

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](#declare_classfactory) `CComClassFactory` , qui déclare que l’usine de classe par défaut. Pour `CComClassFactorySingleton`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Déclare une fonction `GetControllingUnknown`virtuelle .

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Notes

Ajoutez cette macro à votre objet si vous `GetControllingUnknown` obtenez le message d’erreur `CComAggregateCreator`de compilateur qui n’est pas défini (par exemple, dans ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Spécifie que votre objet ne peut pas être agrégé.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de l’objet de classe que vous définissez comme non aggregatable.

### <a name="remarks"></a>Notes

DECLARE_NOT_AGGREGATABLE provoque le `CreateInstance` retour d’une erreur (CLASS_E_NOAGGREGATION) si une tentative est faite d’agrégater sur votre objet.

Par défaut, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contient la [macro DECLARE_AGGREGATABLE,](#declare_aggregatable) qui précise que votre objet peut être agrégé. Pour remplacer ce comportement par défaut, incluez DECLARE_NOT_AGGREGATABLE dans votre définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Spécifie que votre objet doit être agrégé.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de l’objet de classe que vous définissez comme seulement aggregatable.

### <a name="remarks"></a>Notes

DECLARE_ONLY_AGGREGATABLE provoque une erreur (E_FAIL) si une tentative est `CoCreate` faite à votre objet comme objet non agrégaté.

Par défaut, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contient la [macro DECLARE_AGGREGATABLE,](#declare_aggregatable) qui précise que votre objet peut être agrégé. Pour remplacer ce comportement par défaut, incluez DECLARE_ONLY_AGGREGATABLE dans votre définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Précise qu’une instance de **CComPolyObject \< ** *x* **>** est créée lors de la création de votre objet.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de l’objet de classe que vous définissez comme aggregatable ou non aggregatable.

### <a name="remarks"></a>Notes

Pendant la création, la valeur de l’inconnu extérieur est vérifiée. S’il est `IUnknown` NULL, est implémenté pour un objet non agrégaté. Si l’inconnu externe `IUnknown` n’est pas NULL, est implémenté pour un objet agrégé.

L’avantage d’utiliser DECLARE_POLY_AGGREGATABLE est que `CComAggObject` vous `CComObject` évitez d’avoir les deux et dans votre module pour traiter les cas agrégés et non-agrégatés. Un `CComPolyObject` seul objet gère les deux cas. Cela signifie qu’une seule copie de la table v et une copie des fonctions existent dans votre module. Si votre vtable est grand, cela peut diminuer considérablement la taille de votre module. Cependant, si votre vtable `CComPolyObject` est petite, l’utilisation peut entraîner une taille de module légèrement plus grande `CComAggObject` parce `CComObject`qu’elle n’est pas optimisée pour un objet agrégé ou non agrégat, comme le sont et .

La macro DECLARE_POLY_AGGREGATABLE est automatiquement déclarée dans votre objet si vous utilisez le assistant de contrôle ATL pour créer un contrôle complet.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Protège votre objet d’être supprimé si (pendant [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) l’objet agrégé interne incrémente le nombre de références puis décrète le nombre à 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Placez cette macro dans la classe de contrôle d’un contrôle ATL ActiveX pour spécifier les drapeaux VIEWSTATUS au conteneur.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Paramètres

*statusFlags*<br/>
[dans] Les drapeaux VIEWSTATUS. Voir [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) pour une liste de drapeaux.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
