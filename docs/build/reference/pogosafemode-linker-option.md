---
title: / POGOSAFEMODE (exécuter PGO en mode sans échec du thread)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: bbb328bf67d7823305a43f1d61252747cf5ea29e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319718"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (exécuter PGO en mode sans échec du thread)

**L’option /POGOSAFEMODE est déconseillée à compter de Visual Studio 2015**. Utilisez le [/genprofile : exacte](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) et **/GENPROFILE:NOEXACT** options à la place. Le **/POGOSAFEMODE** de l’option spécifie que la génération instrumentée est créée pour utiliser le mode thread-safe pour la capture de données du profil lors de l’optimisation guidée par profil (PGO) les exécutions d’apprentissage.

## <a name="syntax"></a>Syntaxe

> **/POGOSAFEMODE**

## <a name="remarks"></a>Notes

Optimisation guidée par profil (PGO) a deux modes possibles pendant la phase de profilage : *mode rapide* et *mode sans échec*. Lorsque le profilage est en mode rapide, il utilise une instruction d’incrément pour incrémenter des compteurs de données. L’instruction d’incrémentation est plus rapide mais n’est pas thread-safe. Lorsque le profilage est en mode sans échec, il utilise l’instruction d’incrémentation à blocage pour incrémenter des compteurs de données. Cette instruction a les mêmes fonctionnalités que l’instruction d’incrémentation a et est thread-safe, mais il est plus lent.

Le **/POGOSAFEMODE** option définit la génération instrumentée pour utiliser le mode sans échec. Cette option peut uniquement être utilisé lorsque déconseillées [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) est spécifié pendant la phase de l’éditeur de liens d’instrumentation PGO.

Par défaut, le profilage PGO fonctionne en mode rapide. **/ POGOSAFEMODE** est nécessaire uniquement si vous souhaitez utiliser le mode sans échec.

Pour exécuter le profilage PGO en mode sans échec, vous devez utiliser soit **/genprofile : exacte** (recommandé), ou utiliser la variable d’environnement [PogoSafeMode](../environment-variables-for-profile-guided-optimizations.md) ou le commutateur de l’éditeur de liens **/POGOSAFEMODE**, selon le système. Si vous effectuez le profilage sur un x64 ordinateur, vous devez utiliser le commutateur de l’éditeur de liens. Si vous effectuez le profilage sur un x86 ordinateur, vous pouvez utiliser le commutateur de l’éditeur de liens ou définir la variable d’environnement à n’importe quelle valeur avant de commencer le processus d’instrumentation PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Dans le **génération de Code** propriété, choisissez **optimisation guidée par profil - instrumenter (/ LTCG : PGINSTRUMENT)**.

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez le **/POGOSAFEMODE** option dans le **des Options supplémentaires** boîte. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/GENPROFILE et /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimisations guidées par profil](../profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations guidées par profil](../environment-variables-for-profile-guided-optimizations.md)<br/>
