---
title: component, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220475"
---
# <a name="component-pragma"></a>component, pragma

Contrôle la collection d’informations de navigation ou d’informations de dépendance à partir de fichiers sources.

## <a name="syntax"></a>Syntaxe

> **composant #pragma (navigateur,** { **on** | **off** } [ **,** **References** [ **,** *Name* ]] **)**  \
> **composant #pragma (minrebuild,** { **on** | **off** } **)**  \
> **composant #pragma (MinTypeInfo,** { **on** | **off** } **)**

## <a name="remarks"></a>Notes

### <a name="browser"></a>Visiteur

Vous pouvez désactiver ou activer la collecte, et spécifier des noms particuliers à ignorer lors de la collecte d'informations.

L’utilisation de l’activation et de la désactivation contrôle la collection des informations de consultation à partir du pragma. Par exemple :

```cpp
#pragma component(browser, off)
```

arrête la collecte d'informations de consultation par le compilateur.

> [!NOTE]
> Pour activer la collecte des informations de consultation avec ce pragma, vous [devez d’abord activer les informations de consultation](../build/reference/building-browse-information-files-overview.md).

L' option References peut être utilisée avec ou sans l’argument *Name* . L’utilisation de **références** sans *nom* active ou désactive la collecte des références (d’autres informations de consultation continuent à être collectées, cependant). Par exemple :

```cpp
#pragma component(browser, off, references)
```

arrête la collecte d'informations de référence par le compilateur.

L’utilisation de **références** avec *Name* et **off** empêche les références à *Name* d’apparaître dans la fenêtre d’informations de consultation. Utilisez cette syntaxe pour ignorer les noms et les types qui ne vous intéressent pas afin de réduire la taille des fichiers d'informations de consultation. Par exemple :

```cpp
#pragma component(browser, off, references, DWORD)
```

ignore les références à la valeur DWORD à partir de ce point. Vous pouvez réactiver la collecte des références à DWORD en utilisant **sur**:

```cpp
#pragma component(browser, on, references, DWORD)
```

Il s’agit de la seule façon de reprendre la collecte des références au *nom*. vous devez activer explicitement le *nom* que vous avez désactivé.

Pour empêcher le préprocesseur d’étendre le *nom* (par exemple, en développant null à 0), placez des guillemets autour de lui:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Régénération minimale

La fonctionnalité [/GM (activer la régénération minimale)](../build/reference/gm-enable-minimal-rebuild.md) déconseillée requiert que le compilateur C++ crée et stocke des informations de dépendance de classe, qui prennent de l’espace disque. Pour économiser de l’espace disque, vous `#pragma component( minrebuild, off )` pouvez utiliser chaque fois que vous n’avez pas besoin de collecter des informations de dépendance, par exemple, dans des fichiers d’en-tête immuables. Insérez `#pragma component( minrebuild, on )` après des classes immuables pour réactiver la collection de dépendances.

### <a name="reduce-type-information"></a>Réduire les informations de type

L' `mintypeinfo` option réduit les informations de débogage pour la région spécifiée. Le volume de ces informations est considérable et a un impact sur les fichiers .pdb et .obj. Vous ne pouvez pas déboguer des classes et des structures dans la zone mintypeinfo. L'utilisation de l'option mintypeinfo peut être utile pour éviter l'avertissement suivant :

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Pour plus d’informations, consultez l’option de compilateur [/GM (activer la régénération minimale)](../build/reference/gm-enable-minimal-rebuild.md) .

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
