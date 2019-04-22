---
title: component
ms.date: 04/08/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 4870860650a39d27639ad18100ba37ba14aa15c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424064"
---
# <a name="component"></a>component

Contrôle la collecte des informations de consultation ou les informations de dépendance à partir de fichiers sources.

## <a name="syntax"></a>Syntaxe

> **#pragma component( browser,** { **on** | **off** }[**,** **references** [**,** *name* ]] **)** \
> **#pragma component( minrebuild, on** | **off )** \
> **#pragma component( mintypeinfo, on** | **off )**

## <a name="remarks"></a>Notes

### <a name="browser"></a>Visiteur

Vous pouvez désactiver ou activer la collecte, et spécifier des noms particuliers à ignorer lors de la collecte d'informations.

L’utilisation de l’activation et de la désactivation contrôle la collection des informations de consultation à partir du pragma. Exemple :

```cpp
#pragma component(browser, off)
```

arrête la collecte d'informations de consultation par le compilateur.

> [!NOTE]
> Pour activer la collecte des informations de consultation avec ce pragma, [informations de consultation doivent être activées au préalable](../build/reference/building-browse-information-files-overview.md).

Le `references` option peut être utilisée avec ou sans le *nom* argument. À l’aide de `references` sans *nom* Active ou désactive la collecte de références (autres informations de consultation continuent d’être collectées, toutefois). Exemple :

```cpp
#pragma component(browser, off, references)
```

arrête la collecte d'informations de référence par le compilateur.

À l’aide de `references` avec *nom* et `off` empêche les références à *nom* d’apparaître dans la fenêtre d’informations de navigation. Utilisez cette syntaxe pour ignorer les noms et les types qui ne vous intéressent pas afin de réduire la taille des fichiers d'informations de consultation. Exemple :

```cpp
#pragma component(browser, off, references, DWORD)
```

ignore les références à DWORD à partir de là. Vous pouvez activer la collecte des références sur DWORD suite à l’aide de `on`:

```cpp
#pragma component(browser, on, references, DWORD)
```

Ceci est la seule façon de reprendre la collecte des références à *nom*; vous devez explicitement activer tout *nom* que vous avez désactivé.

Pour empêcher le préprocesseur de développer *nom* (par exemple, l’extension NULL à 0), placez des guillemets autour :

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Régénération minimale

Déconseillées [/Gm (activer la régénération minimale)](../build/reference/gm-enable-minimal-rebuild.md) fonctionnalité nécessite le compilateur pour créer et stocker C++ classe les informations de dépendance, qui prend l’espace disque. Pour économiser l’espace disque, vous pouvez utiliser `#pragma component( minrebuild, off )` chaque fois que vous n’avez pas besoin collecter des informations de dépendance, par exemple, dans les fichiers d’en-tête qui ne changent pas. Insérer `#pragma component(minrebuild, on)` une fois que les classes qui ne changent pas pour activer la collection de dépendances de le rallumer.

### <a name="reduce-type-information"></a>Réduction des informations de type

Le `mintypeinfo` option permet de réduire les informations de débogage pour la région spécifiée. Le volume de ces informations est considérable et a un impact sur les fichiers .pdb et .obj. Vous ne pouvez pas déboguer des classes et des structures dans la zone mintypeinfo. L'utilisation de l'option mintypeinfo peut être utile pour éviter l'avertissement suivant :

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Pour plus d’informations, consultez le [/Gm (activer la régénération minimale)](../build/reference/gm-enable-minimal-rebuild.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)