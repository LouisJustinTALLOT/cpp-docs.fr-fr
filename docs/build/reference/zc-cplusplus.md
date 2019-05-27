---
title: /Zc:__cplusplus (Activer la macro __cplusplus mise à jour)
ms.date: 05/16/2019
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 43392438eabc7cc7f6decb1349d112a0ce5bd0f5
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837550"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (Activer la macro __cplusplus mise à jour)

L’option de compilateur **/Zc:__cplusplus** permet à la macro de préprocesseur **\_\_cplusplus** de signaler une valeur mise à jour concernant la prise en charge de normes de langage C++ récentes. Par défaut, Visual Studio retourne toujours la valeur « 199711L » pour la macro de préprocesseur **\_\_cplusplus**.

## <a name="syntax"></a>Syntaxe

> **/Zc:__cplusplus**[ **-** ]

## <a name="remarks"></a>Remarques

La macro de préprocesseur **\_\_cplusplus** est couramment utilisée pour signaler la prise en charge d’une version particulière de la norme C++. Dans la mesure où une grande quantité de code existant repose sur l’attribution de la valeur « 199711L » à cette macro, le compilateur change cette valeur seulement si vous utilisez l’option de compilateur **/Zc:__cplusplus** pour accepter explicitement ce changement. Disponible à compter de Visual Studio 2017 version 15.7, l’option **/Zc:__cplusplus** est désactivée par défaut. Dans les versions antérieures de Visual Studio et par défaut, ou si **/Zc:__cplusplus-** est spécifié, Visual Studio retourne la valeur « 199711L » pour la macro de préprocesseur **\_\_cplusplus**. L’option [/permissive-](permissive-standards-conformance.md) n’active pas **/Zc:__cplusplus**.

Quand l’option **/Zc:__cplusplus** est activée, la valeur indiquée par la macro **\_\_cplusplus** dépend du paramètre de commutateur de version [/std](std-specify-language-standard-version.md). Ce tableau liste les valeurs possibles pour la macro :

|Commutateur /Zc:__cplusplus|Commutateur /std:c++|Valeur __cplusplus|
|-|-|-|
Zc:__cplusplus|/std:c++14 (par défaut)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus- (désactivé)|Valeur quelconque|199711L
Non spécifié|Valeur quelconque|199711L

Le compilateur ne prend pas en charge les commutateurs de normes pour C++98, C++03 ou C++11.

Pour une détection plus fine des changements apportés à l’ensemble d’outils du compilateur, utilisez la macro prédéfinie [_MSC_VER](../../preprocessor/predefined-macros.md). La valeur de cette macro intégrée est incrémentée à chaque mise à jour de l’ensemble d’outils dans Visual Studio 2017 et ultérieur. La macro prédéfinie [_MSVC_LANG](../../preprocessor/predefined-macros.md) signale la version de la norme, que l’option **/Zc:__cplusplus** soit activée ou désactivée. Quand l’option **/Zc:__cplusplus** est activée, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour obtenir des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++** > **Ligne de commande**.

1. Ajoutez **/Zc:__cplusplus** ou **/Zc:__cplusplus-** au volet **Options supplémentaires**.

## <a name="see-also"></a>Voir aussi

- [/Zc (Conformité)](zc-conformance.md)
- [/std (Spécifier la version de la norme du langage)](std-specify-language-standard-version.md)
- [Macros prédéfinies](../../preprocessor/predefined-macros.md)
