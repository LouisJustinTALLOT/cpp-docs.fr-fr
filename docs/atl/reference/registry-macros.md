---
title: Macros de Registre
ms.date: 08/19/2019
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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417501"
---
# <a name="registry-macros"></a>Macros de Registre

Ces macros définissent une bibliothèque de types et des fonctions de registre utiles.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indique que vous souhaitez que le code d’inscription de votre objet se trouve dans l’objet afin d’éviter une dépendance sur ATL. DLL.|
|[DECLARE_LIBID](#declare_libid)|Fournit un moyen pour ATL d’obtenir le *LIBID* de la bibliothèque de types.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Évite l’inscription ATL par défaut.|
|[DECLARE_REGISTRY](#declare_registry)|Entre ou supprime l’entrée de l’objet principal dans le registre système.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Spécifie les informations requises pour inscrire automatiquement l' *AppID*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Recherche la ressource nommée et y exécute le script de registre.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Recherche la ressource identifiée par un numéro d’identification et y exécute le script de registre.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Symbole qui indique que vous souhaitez que le code d’inscription de votre objet se trouve dans l’objet afin d’éviter une dépendance sur ATL. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Notes

Lorsque vous définissez ATL_STATIC_REGISTRY, vous devez utiliser le code suivant :

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>DECLARE_LIBID

Fournit un moyen pour ATL d’obtenir le *LIBID* de la bibliothèque de types.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Paramètres

*LIBID*<br/>
GUID de la bibliothèque de types.

### <a name="remarks"></a>Notes

Utilisez DECLARE_LIBID dans une classe dérivée de `CAtlModuleT`.

### <a name="example"></a>Exemple

Les projets ATL de l’Assistant non attribués auront un exemple d’utilisation de cette macro.

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Utilisez DECLARE_NO_REGISTRY si vous souhaitez éviter toute inscription ATL par défaut pour la classe dans laquelle cette macro apparaît.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

Entre l’inscription de la classe standard dans le registre système ou le supprime du Registre système.

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
dans Inclus pour la compatibilité descendante.

*pid*<br/>
dans LPCTSTR qui est un identificateur de programme spécifique à la version.

*vpid*<br/>
dans LPCTSTR qui est un identificateur de programme indépendant de la version.

*NID*<br/>
dans UINT qui est un index de la chaîne de ressource dans le registre à utiliser comme description du programme.

*flags*<br/>
dans Valeur DWORD contenant le modèle de thread du programme dans le registre. Doit avoir l’une des valeurs suivantes : THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="remarks"></a>Notes

L’inscription standard se compose du CLSID, de l’ID de programme, de l’ID de programme indépendant de la version, de la chaîne de description et du modèle de thread.

Lorsque vous créez un objet ou un contrôle à l’aide de l’Assistant Ajout de classes ATL, l’Assistant implémente automatiquement la prise en charge de Registre basée sur les scripts et ajoute la macro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) à vos fichiers. Si vous ne souhaitez pas prendre en charge le registre basé sur un script, vous devez remplacer cette macro par DECLARE_REGISTRY. DECLARE_REGISTRY insère uniquement les cinq clés de base décrites ci-dessus dans le registre. Vous devez écrire manuellement du code pour insérer d’autres clés dans le registre.

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Spécifie les informations requises pour inscrire automatiquement l' *AppID*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Paramètres

*Resid*<br/>
ID de ressource du fichier. RGS qui contient des informations sur l' *AppID*.

*AppID*<br/>
GUID.

### <a name="remarks"></a>Notes

Utilisez DECLARE_REGISTRY_APPID_RESOURCEID dans une classe dérivée de `CAtlModuleT`.

### <a name="example"></a>Exemple

Les classes ajoutées aux projets ATL avec l’Assistant Ajouter un code de classe auront un exemple d’utilisation de cette macro.

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Obtient la ressource nommée contenant le fichier de Registre, puis exécute le script pour entrer des objets dans le registre système ou les supprimer du Registre système.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Identificateur de chaîne de votre ressource.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou un contrôle à l’aide de l’Assistant Projet ATL, l’Assistant implémente automatiquement la prise en charge de Registre basée sur les scripts et ajoute la macro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) , qui est similaire à DECLARE_REGISTRY_RESOURCE, à vos fichiers.

Vous pouvez établir une liaison statique avec le composant de Registre ATL pour l’accès optimisé au registre. Pour établir une liaison statique avec le code d’inscription, ajoutez la ligne suivante à votre fichier *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez qu’ATL remplace les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de structures `_ATL_REGMAP_ENTRIES`, où chaque entrée contient un espace réservé de variable associé à une valeur pour remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule :: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule :: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cela ajoute toutes les valeurs de remplacement dans les structures de `_ATL_REGMAP_ENTRIES` à la carte de remplacement du Bureau d’enregistrement.

Pour plus d’informations sur les paramètres et les scripts remplaçables, consultez l’article [composant du Registre ATL (Registrar)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Identique à [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) , sauf qu’elle utilise un uint créé par un Assistant pour identifier la ressource, plutôt qu’un nom de chaîne.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Identificateur généré par l’Assistant de votre ressource.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou un contrôle à l’aide de l’Assistant Projet ATL, l’Assistant implémente automatiquement la prise en charge de Registre basée sur les scripts et ajoute la macro DECLARE_REGISTRY_RESOURCEID à vos fichiers.

Vous pouvez établir une liaison statique avec le composant de Registre ATL pour l’accès optimisé au registre. Pour établir une liaison statique avec le code d’inscription, ajoutez la ligne suivante à votre fichier *stdafx. h* (*pch. h* dans Visual Studio 2019 et versions ultérieures) :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez qu’ATL remplace les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de structures `_ATL_REGMAP_ENTRIES`, où chaque entrée contient un espace réservé de variable associé à une valeur pour remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule :: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule :: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cela ajoute toutes les valeurs de remplacement dans les structures de `_ATL_REGMAP_ENTRIES` à la carte de remplacement du Bureau d’enregistrement.

Pour plus d’informations sur les paramètres et les scripts remplaçables, consultez l’article [composant du Registre ATL (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
