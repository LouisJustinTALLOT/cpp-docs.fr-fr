---
title: /Zc:__cplusplus (macro __cplusplus mis à jour de l’activer)
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705712"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (macro __cplusplus mis à jour de l’activer)

Le **/Zc:__cplusplus** permet d’option du compilateur le  **\_ \_cplusplus** macro de préprocesseur pour signaler une valeur mise à jour pour récente C++ normes prise en charge. Par défaut, Visual Studio retourne toujours la valeur « 199711L » pour le  **\_ \_cplusplus** macro de préprocesseur.

## <a name="syntax"></a>Syntaxe

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Notes

Le  **\_ \_cplusplus** macro de préprocesseur est couramment utilisé pour prendre en charge des rapports pour une version particulière de la norme C++. Un grand nombre de code existant semble dépendent de la valeur de cette macro correspondant à « L 199711 », le compilateur ne change pas la valeur de la macro, sauf si vous explicitement de participer à l’aide de la **/Zc:__cplusplus** option du compilateur. Le **/Zc:__cplusplus** option est disponible à partir de Visual Studio 2017 version 15.7 et est désactivée par défaut. Dans les versions antérieures de Visual Studio et, par défaut, ou si **/Zc:__cplusplus-** est spécifié, Visual Studio retourne la valeur « 199711 L » pour le  **\_ \_cplusplus** macro de préprocesseur. Le [/ permissive-](permissive-standards-conformance.md) option n’active pas **/Zc:__cplusplus**.

Lorsque le **/Zc:__cplusplus** option est activée, la valeur signalée par le  **\_ \_cplusplus** dépend de la macro la [/std](std-specify-language-standard-version.md) changement de version paramètre. Ce tableau montre les valeurs possibles de la macro :

|Commutateur de /Zc:__cplusplus|commutateur de /std:c++|valeur de __cplusplus|
|-|-|-|
Zc:__cplusplus|/ std : c ++ 14 (valeur par défaut)|201402L
Zc:__cplusplus|/ std : c ++ 17|201703L
Zc:__cplusplus|/ std : c ++ plus récente|201704L
Zc:__cplusplus-(désactivé)|Valeur quelconque|199711L
Non spécifié|Valeur quelconque|199711L

Le compilateur ne prend pas en charge les commutateurs de normes pour C ++ 98, C ++ 03 ou C ++ 11.

Pour plus précise la détection des modifications apportées à l’ensemble d’outils du compilateur, utilisez le [_MSC_VER](../../preprocessor/predefined-macros.md) macro prédéfinie. La valeur de cette macro prédéfinie est incrémentée pour chaque mise à jour de l’ensemble d’outils dans Visual Studio 2017 et versions ultérieures. Le [_MSVC_LANG](../../preprocessor/predefined-macros.md) macro prédéfinie indique la version standard si le **/Zc:__cplusplus** option est activée ou désactivée. Lorsque **/Zc:__cplusplus** est activé, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Ajouter **/Zc:__cplusplus** ou **/Zc:__cplusplus-** à la **des options supplémentaires :** volet.

## <a name="see-also"></a>Voir aussi

- [/Zc (Conformité)](zc-conformance.md)
- [/STD (version standard spécifiez language)](std-specify-language-standard-version.md)
- [Macros prédéfinies](../../preprocessor/predefined-macros.md)
