---
description: En savoir plus sur:/POGOSAFEMODE (exécuter PGO en mode thread-safe)
title: /POGOSAFEMODE (exécuter PGO en mode thread-safe)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: dfe8d46a3008a1d41156d077e5b87e50ac345e18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225919"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/POGOSAFEMODE (exécuter PGO en mode thread-safe)

**L’option/POGOSAFEMODE est déconseillée à partir de Visual Studio 2015**. Utilisez plutôt les options [/GENPROFILE : exact](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) et **/GENPROFILE : noexact** . L’option de l’éditeur de liens **/POGOSAFEMODE** spécifie que la build instrumentée est créée pour utiliser le mode thread-safe pour la capture des données de profil pendant les exécutions d’apprentissage de l’optimisation guidée par profil (PGO).

## <a name="syntax"></a>Syntaxe

> **/POGOSAFEMODE**

## <a name="remarks"></a>Notes

L’optimisation guidée par profil (PGO) a deux modes possibles pendant la phase de profilage : le *mode rapide* et le *mode sans échec*. Lorsque le profilage est en mode rapide, il utilise une instruction d’incrément pour augmenter les compteurs de données. L’instruction d’incrément est plus rapide, mais n’est pas thread-safe. Lorsque le profilage est en mode sans échec, il utilise l’instruction d’incrémentation d’interverrouillage pour augmenter les compteurs de données. Cette instruction a les mêmes fonctionnalités que l’instruction d’incrément, et est thread-safe, mais elle est plus lente.

L’option **/POGOSAFEMODE** définit la build instrumentée pour qu’elle utilise le mode sans échec. Cette option peut être utilisée uniquement quand l’option [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) déconseillée est spécifiée pendant la phase de l’éditeur de liens d’instrumentation PGO.

Par défaut, le profilage PGO fonctionne en mode rapide. **/POGOSAFEMODE** est requis uniquement si vous souhaitez utiliser le mode sans échec.

Pour exécuter le profilage PGO en mode sans échec, vous devez utiliser soit **/GENPROFILE : exact** (recommandé), soit la variable d’environnement [PogoSafeMode](../environment-variables-for-profile-guided-optimizations.md) ou le commutateur de l’éditeur de liens **/POGOSAFEMODE**, selon le système. Si vous effectuez le profilage sur un ordinateur x64, vous devez utiliser le commutateur de l’éditeur de liens. Si vous effectuez le profilage sur un ordinateur x86, vous pouvez utiliser le commutateur de l’éditeur de liens ou définir la variable d’environnement sur n’importe quelle valeur avant de démarrer le processus d’instrumentation PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Dans la propriété **génération de code durant l’édition de liens** , choisissez **optimisation guidée par profil-instrument (/LTCG : PGInstrument)**.

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option **/POGOSAFEMODE** dans la zone **options supplémentaires** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/GENPROFILE et/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimisations guidées par profil](../profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations de Profile-Guided](../environment-variables-for-profile-guided-optimizations.md)<br/>
