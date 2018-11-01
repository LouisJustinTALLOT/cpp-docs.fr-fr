---
title: Macros de Registre
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: bced900cd7bac666daf415d91a4540828c769025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660380"
---
# <a name="registry-macros"></a>Macros de Registre

Ces macros définissent les fonctionnalités de bibliothèque et du Registre de type utile.

|||
|-|-|
|[_ATL_STATIC_REGISTRY À](#_atl_static_registry)|Indique que vous souhaitez que le code d’inscription pour votre objet se trouve dans l’objet afin d’éviter une dépendance sur ATL. DLL.|
|[DECLARE_LIBID](#declare_libid)|Fournit un moyen pour ATL obtenir le *libid* de la bibliothèque de types.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Permet d’éviter l’inscription ATL par défaut.|
|[DECLARE_REGISTRY](#declare_registry)|Insère ou supprime l’entrée de l’objet principal dans le Registre système.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Spécifie les informations requises pour inscrire automatiquement le *appid*.|
|[MACRO DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Recherche de la ressource nommée et exécute le script de Registre qu’il contient.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Recherche de la ressource identifiée par un numéro d’identification et exécute le script de Registre qu’il contient.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY À

Un symbole indiquant que vous souhaitez que le code d’inscription pour votre objet se trouve dans l’objet afin d’éviter une dépendance sur ATL. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Notes

Lorsque vous définissez ATL_STATIC_REGISTRY, vous devez utiliser le code suivant :

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

Fournit un moyen pour ATL obtenir le *libid* de la bibliothèque de types.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Paramètres

*LIBID*<br/>
GUID de la bibliothèque de types.

### <a name="remarks"></a>Notes

Utiliser DECLARE_LIBID dans un `CAtlModuleT`-classe dérivée.

### <a name="example"></a>Exemple

Avec attributs des projets générés par l’Assistant ATL aura un exemple d’utilisation de cette macro.

##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY

Utilisez DECLARE_NO_REGISTRY si vous souhaitez éviter tout enregistrement d’ATL par défaut pour la classe dans laquelle cette macro apparaît.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>  DECLARE_REGISTRY

Entre l’inscription de classe standard dans le Registre système, ou il supprime du Registre système.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Paramètres

*class*<br/>
[in] Inclus pour la compatibilité descendante.

*pid*<br/>
[in] LPCTSTR qui est un identificateur de programme de spécifique à la version.

*vpid*<br/>
[in] LPCTSTR qui est un identificateur de programme indépendant de la version.

*NID*<br/>
[in] UINT qui est un index de la chaîne de ressource dans le Registre à utiliser comme la description du programme.

*flags*<br/>
[in] Un valeur DWORD contenant le modèle de thread du programme dans le Registre. Doit être une des valeurs suivantes : THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="remarks"></a>Notes

L’inscription standard se compose des CLSID, ID de programme, ID de programme indépendant de la version, chaîne de description, modèle de thread.

Lorsque vous créez un objet ou contrôler à l’aide de l’Assistant Ajout de classes ATL, l’Assistant implémente la prise en charge du Registre basée sur le script automatiquement et ajoute le [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro à vos fichiers. Si vous ne souhaitez pas de prise en charge du Registre basée sur un script, vous devez remplacer cette macro avec DECLARE_REGISTRY. DECLARE_REGISTRY insère uniquement les cinq clés de base décrits ci-dessus dans le Registre. Vous devez écrire manuellement le code pour insérer d’autres clés dans le Registre.

##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID

Spécifie les informations requises pour inscrire automatiquement le *appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Paramètres

*RESID*<br/>
L’id de ressource du fichier .rgs qui contient des informations sur le *appid*.

*ID d’application*<br/>
GUID.

### <a name="remarks"></a>Notes

Utiliser DECLARE_REGISTRY_APPID_RESOURCEID dans un `CAtlModuleT`-classe dérivée.

### <a name="example"></a>Exemple

Les classes ajoutées à des projets ATL avec l’Assistant code ajouter une classe aura un exemple d’utilisation de cette macro.

##  <a name="declare_registry_resource"></a>  MACRO DECLARE_REGISTRY_RESOURCE

Obtient la ressource nommée contenant le fichier de Registre et exécute le script pour entrer des objets dans le Registre système ou les supprimer à partir du Registre système.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Identificateur de votre ressource de chaîne.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou contrôler à l’aide de l’Assistant Projet ATL, l’Assistant implémenter la prise en charge basée sur un script de Registre et automatiquement ajouter le [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro, ce qui revient à DECLARE_REGISTRY_ RESSOURCE, à vos fichiers.

Vous pouvez lier statiquement avec le composant de Registre ATL (inscription) pour accéder au Registre optimisé. Pour lier statiquement pour le code d’inscription, ajoutez la ligne suivante à votre fichier stdafx.h :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez ATL pour remplacer les valeurs de remplacement en cours d’exécution, ne spécifiez pas la macro macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en transmettant le tableau. Cette opération ajoute toutes les valeurs de remplacement dans le `_ATL_REGMAP_ENTRIES` structures au mappage de remplacement du bureau d’enregistrement.

Pour plus d’informations sur les paramètres remplaçables et l’écriture de scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID

Identique à [macro DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) sauf qu’elle utilise un UINT générées par l’Assistant pour identifier la ressource, plutôt qu’un nom de chaîne.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Identificateur généré par l’Assistant de votre ressource.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou le contrôle à l’aide de l’Assistant Projet ATL, l’Assistant sera automatiquement implémenter la prise en charge basée sur un script de Registre et ajouter la macro DECLARE_REGISTRY_RESOURCEID à vos fichiers.

Vous pouvez lier statiquement avec le composant de Registre ATL (inscription) pour accéder au Registre optimisé. Pour lier statiquement pour le code d’inscription, ajoutez la ligne suivante à votre fichier stdafx.h :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez ATL pour remplacer les valeurs de remplacement en cours d’exécution, ne spécifiez pas la macro macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en transmettant le tableau. Cette opération ajoute toutes les valeurs de remplacement dans le `_ATL_REGMAP_ENTRIES` structures au mappage de remplacement du bureau d’enregistrement.

Pour plus d’informations sur les paramètres remplaçables et l’écriture de scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
