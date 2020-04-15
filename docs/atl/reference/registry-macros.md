---
title: Macros de registre
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
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326046"
---
# <a name="registry-macros"></a>Macros de registre

Ces macros définissent les installations utiles de bibliothèque et d’enregistrement de type.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indique que vous voulez que le code d’enregistrement de votre objet soit dans l’objet pour éviter une dépendance à l’égard d’ATL. DLL.|
|[DECLARE_LIBID](#declare_libid)|Fournit un moyen pour ATL d’obtenir la *libidide* de la bibliothèque de type.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Évite l’enregistrement par défaut ATL.|
|[DECLARE_REGISTRY](#declare_registry)|Entre ou supprime l’entrée de l’objet principal dans le registre du système.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Spécifie les informations requises pour enregistrer automatiquement *l’appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Trouve la ressource nommée et exécute le script de registre en son sein.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Trouve la ressource identifiée par un numéro d’identification et exécute le script de registre en son sein.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Un symbole qui indique que vous voulez que le code d’enregistrement de votre objet soit dans l’objet pour éviter une dépendance à l’ATL. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Notes

Lorsque vous définissez ATL_STATIC_REGISTRY, vous devez utiliser le code suivant :

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

Fournit un moyen pour ATL d’obtenir la *libidide* de la bibliothèque de type.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Paramètres

*libid*<br/>
GUID de la bibliothèque de types.

### <a name="remarks"></a>Notes

Utilisez DECLARE_LIBID dans une `CAtlModuleT`classe dérivée.

### <a name="example"></a>Exemple

Les projets ATL non attribués générés par les sorciers auront un échantillon d’utilisation de cette macro.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Utilisez DECLARE_NO_REGISTRY si vous voulez éviter toute inscription PAR défaut ATL pour la classe dans laquelle cette macro apparaît.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

Entre l’enregistrement de classe standard dans le registre du système ou le retire du registre du système.

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
[dans] Inclus pour la compatibilité vers l’arrière.

*Pid*<br/>
[dans] Un LPCTSTR qui est un identifiant de programme spécifique à la version.

*cpid*<br/>
[dans] Un LPCTSTR qui est un identifiant de programme indépendant de version.

*nid*<br/>
[dans] Un UINT qui est un indice de la chaîne de ressources dans le registre à utiliser comme description du programme.

*Drapeaux*<br/>
[dans] Un DWORD contenant le modèle de threading du programme dans le registre. Doit être l’une des valeurs suivantes : THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="remarks"></a>Notes

L’enregistrement standard se compose du CLSID, de l’ID du programme, de l’ID de programme indépendant de la version, de la chaîne de description et du modèle de thread.

Lorsque vous créez un objet ou un contrôle à l’aide de l’assistant de classe ATL Add, l’assistant implémente automatiquement le support de registre basé sur le script et ajoute la [macro DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) à vos fichiers. Si vous ne voulez pas de support de registre basé sur le script, vous devez remplacer cette macro par DECLARE_REGISTRY. DECLARE_REGISTRY n’insère que les cinq clés de base décrites ci-dessus dans le registre. Vous devez écrire manuellement du code pour insérer d’autres clés dans le registre.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Spécifie les informations requises pour enregistrer automatiquement *l’appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Paramètres

*resid*<br/>
L’id de ressource du fichier .rgs qui contient des informations sur *l’appid*.

*Appid*<br/>
GUID.

### <a name="remarks"></a>Notes

Utilisez DECLARE_REGISTRY_APPID_RESOURCEID dans une `CAtlModuleT`classe dérivée.

### <a name="example"></a>Exemple

Les classes ajoutées aux projets ATL avec l’assistant de code De classe Add auront un échantillon d’utilisation de cette macro.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Obtient la ressource désignée contenant le fichier de registre et exécute le script pour soit entrer des objets dans le registre du système ou les supprimer du registre du système.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Identifiant de chaîne de votre ressource.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou un contrôle à l’aide de l’assistant de projet ATL, l’assistant implémente automatiquement le support de registre basé sur le script et ajoutera la macro [DECLARE_REGISTRY_RESOURCEID,](#declare_registry_resourceid) qui est similaire à DECLARE_REGISTRY_RESOURCE, à vos fichiers.

Vous pouvez établir un lien statique avec le composant du registre ATL (registraire) pour optimiser l’accès au registre. Pour lier statiquement au code registraire, ajoutez la ligne suivante à votre fichier *pch.h* *(stdafx.h* dans Visual Studio 2017 et plus tôt) :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez qu’ATL remplace les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID macro. Au lieu de `_ATL_REGMAP_ENTRIES` cela, créer un tableau de structures, où chaque entrée contient un espace variable avec une valeur pour remplacer le placeholder au moment de l’exécution. Puis appelez [CAtlModule::UpdateRegistryDeResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cela ajoute toutes les valeurs `_ATL_REGMAP_ENTRIES` de remplacement dans les structures à la carte de remplacement du registraire.

Pour plus d’informations sur les paramètres remplaçables et le script, voir l’article [The ATL Registry Component (registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Même chose que [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) sauf qu’il utilise un UINT généré par un sorcier pour identifier la ressource, plutôt qu’un nom de chaîne.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Identifiant généré par les sorciers de votre ressource.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet ou un contrôle à l’aide de l’assistant de projet ATL, l’assistant implémente automatiquement le support de registre basé sur le script et ajoute la macro DECLARE_REGISTRY_RESOURCEID à vos fichiers.

Vous pouvez établir un lien statique avec le composant du registre ATL (registraire) pour optimiser l’accès au registre. Pour lier statiquement au code registraire, ajoutez la ligne suivante à votre fichier *stdafx.h* *(pch.h* dans Visual Studio 2019 et plus tard) :

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si vous souhaitez qu’ATL remplace les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID macro. Au lieu de `_ATL_REGMAP_ENTRIES` cela, créer un tableau de structures, où chaque entrée contient un espace variable avec une valeur pour remplacer le placeholder au moment de l’exécution. Puis appelez [CAtlModule::UpdateRegistryDeResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cela ajoute toutes les valeurs `_ATL_REGMAP_ENTRIES` de remplacement dans les structures à la carte de remplacement du registraire.

Pour plus d’informations sur les paramètres remplaçables et le script, voir l’article [The ATL Registry Component (registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
