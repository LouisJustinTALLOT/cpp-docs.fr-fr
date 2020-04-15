---
title: /OPT (Optimisations)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336223"
---
# <a name="opt-optimizations"></a>/OPT (Optimisations)

Contrôle les optimisations effectuées par LINK pendant une génération.

## <a name="syntax"></a>Syntaxe

> **/OPT:****'REF** | **NOREF'**<br/>
> **/OPT:****ICF****=**_[itérations_] **NOICF**- FRANCE<br/>
> **/OPT:****LBR** | **NOLBR**

## <a name="arguments"></a>Arguments

**REF** &#124; **NOREF**

**/OPT:REF** élimine les fonctions et les données qui ne sont jamais référencées; **/OPT:NOREF** conserve des fonctions et des données qui ne sont jamais référencées.

Lorsque /OPT:REF est activé, LINK supprime les fonctions et les données emballées non réfrécrées, connues sous le nom *de COMDATs*. Cette optimisation porte le nom d'élimination COMDAT transitive. **L’option /OPT:REF** désactive également les liaisons incrémentales.

Les fonctions inlinées et les fonctions des membres définies à l’intérieur d’une déclaration de classe sont toujours des COMDAT. Toutes les fonctions d’un fichier d’objets sont intégrées dans les COMDAT s’il est compilé en utilisant l’option [/Gy.](gy-enable-function-level-linking.md) Pour placer des données **de cône** dans les COMDAT, vous devez les déclarer en utilisant `__declspec(selectany)`. Pour plus d’informations sur la façon de spécifier les données pour la suppression ou le pliage, voir [selectany](../../cpp/selectany.md).

Par défaut, **/OPT:REF** est activé par le linker à moins que **/OPT:NOREF** ou [/DEBUG](debug-generate-debug-info.md) ne soit spécifié. Pour remplacer ce défaut et conserver les COMDAT non référés dans le programme, spécifiez **/OPT:NOREF**. Vous pouvez utiliser l’option [/INCLUDE](include-force-symbol-references.md) pour remplacer la suppression d’un symbole spécifique.

Si [/DEBUG](debug-generate-debug-info.md) est spécifié, le défaut pour **/OPT** est **NOREF**, et toutes les fonctions sont conservées dans l’image. Pour remplacer ce défaut et optimiser une version de débogé, spécifiez **/OPT:REF**. Cela peut réduire la taille de votre exécutable, et peut être une optimisation utile, même dans les constructions de débogé. Nous vous recommandons également de spécifier **/OPT:NOICF** pour préserver les fonctions identiques dans les constructions de déboges. Cela facilite la lecture des traces de la pile et la définition des points d’arrêt dans les fonctions qui seraient pliées ensemble dans le cas contraire.

**Itérations ICF**\[**=**_iterations_] &#124; **NOICF**

Utilisez les_itérations_ **ICF**\[**=**] pour effectuer le pliage IDENTIQUE COMDAT. Les COMDAT redondants peuvent être supprimés de la sortie de l'éditeur de liens. Le *paramètre d’itérations* facultatives spécifie le nombre de fois pour parcourir les symboles pour les doublons. Le nombre par défaut d’itérations est de 1. Des itérations supplémentaires peuvent permettre de localiser davantage de doublons n’ayant pas été détectés par pliage au cours de l’itération précédente.

Par défaut, **/OPT:ICF** est activé par le linker à moins **que /OPT:NOICF** ou [/DEBUG](debug-generate-debug-info.md) ne soit spécifié. Pour remplacer ce défaut et empêcher les COMDAT d’être pliés dans le programme, spécifiez **/OPT:NOICF**.

Dans une version de débogé, vous devez spécifier explicitement **/OPT:ICF** pour activer le pliage COMDAT. Cependant, parce que **/OPT:ICF** peut fusionner des données identiques ou des fonctions, il peut changer les noms de fonction qui apparaissent dans les traces de pile. Il peut également rendre impossible de définir des points d’arrêt dans certaines fonctions ou d’examiner certaines données dans le débbugger, et peut vous emmener dans des fonctions inattendues lorsque vous seul étape à travers votre code. Le comportement du code est identique, mais la présentation de débbugger peut être très déroutant. Par conséquent, nous ne recommandons pas que vous utilisez **/OPT:ICF** dans les constructions de déboges à moins que les avantages de code plus petit l’emportent sur ces inconvénients.

> [!NOTE]
> Parce que **/OPT:ICF** peut provoquer la même adresse d’être attribué à différentes fonctions ou la lecture uniquement des membres de données (c’est-à-dire, les variables **const** lorsqu’il est compilé par l’utilisation **/Gy),** il peut briser un programme qui dépend des adresses uniques pour les fonctions ou les membres de données lus seulement. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Les options **/OPT:LBR** et **/OPT:NOLBR** ne s’appliquent qu’aux binaires ARM. Étant donné que certaines instructions de branche de processeur ARM ont une portée limitée, si le lien détecte un saut vers une adresse hors de portée, il remplace l’adresse de destination de l’instruction de branche par l’adresse d’une « île » de code qui contient une instruction de branche qui cible la destination réelle. Vous pouvez utiliser **/OPT:LBR** pour optimiser la détection de longues instructions de branche et le placement d’îles de code intermédiaire pour minimiser la taille globale du code. **/OPT:NOLBR** demande au linker de générer des îles de code pour de longues instructions de branche comme elles sont rencontrées, sans optimisation.

Par défaut, l’option **/OPT:LBR** est définie lorsque la liaison incrémentale n’est pas activée. Si vous voulez un lien non-incrémental mais pas de longues optimisations de branche, spécifiez **/OPT:NOLBR**. **L’option /OPT:LBR** désactive les liens progressifs.

## <a name="remarks"></a>Notes

Lorsqu’il est utilisé à la ligne de commande, le lien par défaut à **/OPT:REF,ICF,LBR**. Si **/DEBUG** est spécifié, le défaut est **/OPT:NOREF,NOICF,NOLBR**.

Les optimisations **/OPT** diminuent généralement la taille de l’image et augmentent la vitesse du programme. Ces améliorations peuvent être substantielles dans les grands programmes, c’est pourquoi elles sont activées par défaut pour les constructions au détail.

L’optimisation des liens prend plus de temps à l’avant, mais le code optimisé permet également de gagner du temps lorsque le linker a moins de relocalisations à corriger et crée une image finale plus petite, et il permet d’économiser encore plus de temps quand il a moins d’informations de débogé à traiter et à écrire dans le PDB. Lorsque l’optimisation est activée, elle peut entraîner un temps de liaison plus rapide dans l’ensemble, car le faible coût supplémentaire dans l’analyse peut être plus que compensé par les économies de temps dans les passes de liaison sur les plus petits binaires.

Les arguments **/OPT** peuvent être spécifiés ensemble, séparés par des virgules. Par exemple, au lieu de **/OPT:REF /OPT:NOICF**, vous pouvez spécifier **/OPT:REF,NOICF**.

Vous pouvez utiliser l’option de liaison [/VERBOSE](verbose-print-progress-messages.md) pour voir les fonctions supprimées par **/OPT:REF** et les fonctions qui sont pliées par **/OPT:ICF**.

Les arguments **/OPT** sont souvent définis pour les projets créés par l’utilisation du dialogue **New Project** dans le Visual Studio IDE, et ont généralement des valeurs différentes pour les configurations de débogs et de libération. Si aucune valeur n’est définie pour ces options de liaison dans votre projet, vous pouvez obtenir les défauts du projet, ce qui peut être différent des valeurs par défaut utilisées par le linker à la ligne de commande.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:ICF ou OPT:REF de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de**propriété d’optimisation** **de lien de** > propriété **de** > propriété de propriété de propriété de propriété de propriété de connexion de propriété de propriété de propriété de propriété de propriété

1. Modifiez l'une des propriétés suivantes :

   - **Activer le pliage COMDAT**

   - **Informations de référence**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:LBR de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page propriété **Configuration Properties** > **Linker** > **Command Line.**

1. Entrez l’option dans **des options supplémentaires**:

   `/opt:lbr` ou `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
