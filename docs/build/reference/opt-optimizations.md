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
ms.openlocfilehash: 874c4b974348d1bef8c8c3837f46c1c27d6d304b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215190"
---
# <a name="opt-optimizations"></a>/OPT (Optimisations)

Contrôle les optimisations effectuées par LINK pendant une génération.

## <a name="syntax"></a>Syntaxe

> **/OPT :**{**ref**  |  **NOREF**} \
> **/OPT :**{**ICF**[ **=** _iterations_] | **NOICF**} \
> **/OPT :**{**LBR**  |  **NOLBR**}

## <a name="arguments"></a>Arguments

**REF** &#124; **NOREF**

**/OPT : Ref** élimine les fonctions et les données qui ne sont jamais référencées ; **/OPT : NOREF** conserve les fonctions et les données qui ne sont jamais référencées.

Lorsque/OPT : REF est activé, LINK supprime les fonctions et données empaquetées non référencées, appelées *COMDAT*. Cette optimisation porte le nom d'élimination COMDAT transitive. L’option **/OPT : Ref** désactive également la liaison incrémentielle.

Les fonctions inline et les fonctions membres définies dans une déclaration de classe sont toujours des COMDAT. Toutes les fonctions d’un fichier objet sont transformées en COMDAT si elles sont compilées à l’aide de l’option [/Gy](gy-enable-function-level-linking.md) . Pour placer **`const`** des données dans des COMDAT, vous devez les déclarer à l’aide de `__declspec(selectany)` . Pour plus d’informations sur la façon de spécifier des données pour la suppression ou le repli, consultez [selectany](../../cpp/selectany.md).

Par défaut, **/OPT : Ref** est activé par l’éditeur de liens, sauf si **/OPT : NOREF** ou [/Debug](debug-generate-debug-info.md) est spécifié. Pour remplacer cette valeur par défaut et conserver les COMDAT non référencés dans le programme, spécifiez **/OPT : NOREF**. Vous pouvez utiliser l’option [/include](include-force-symbol-references.md) pour substituer la suppression d’un symbole spécifique.

Si [/Debug](debug-generate-debug-info.md) est spécifié, la valeur par défaut de **/OPT** est **NOREF**, et toutes les fonctions sont conservées dans l’image. Pour remplacer cette valeur par défaut et optimiser une version Debug, spécifiez **/OPT : Ref**. Cela peut réduire la taille de votre fichier exécutable et peut être une optimisation utile même dans les versions Debug. Nous vous recommandons également de spécifier **/OPT : NOICF** pour conserver des fonctions identiques dans les versions Debug. Cela facilite la lecture des traces de la pile et la définition des points d’arrêt dans les fonctions qui seraient pliées ensemble dans le cas contraire.

**Pare-feu** \[ **=** _itérations_] &#124; **NOICF**

Utilisez **ICF**des \[ **=** _itérations_ICF] pour effectuer un repli COMDAT identique. Les COMDAT redondants peuvent être supprimés de la sortie de l'éditeur de liens. Le paramètre facultatif *iterations* spécifie le nombre de fois où les symboles doivent être parcourus pour les doublons. Le nombre d’itérations par défaut est 1. Des itérations supplémentaires peuvent permettre de localiser davantage de doublons n’ayant pas été détectés par pliage au cours de l’itération précédente.

Par défaut, **/OPT : ICF** est activé par l’éditeur de liens, sauf si **/OPT : NOICF** ou [/Debug](debug-generate-debug-info.md) est spécifié. Pour remplacer cette valeur par défaut et empêcher les COMDAT d’être pliées dans le programme, spécifiez **/OPT : NOICF**.

Dans une version Debug, vous devez spécifier explicitement **/OPT : ICF** pour activer le repli COMDAT. Toutefois, étant donné que **/OPT : ICF** peut fusionner des données ou des fonctions identiques, il peut modifier les noms des fonctions qui apparaissent dans les traces de la pile. Il peut également rendre impossible de définir des points d’arrêt dans certaines fonctions ou d’examiner certaines données du débogueur, et vous permet d’atteindre des fonctions inattendues lorsque vous effectuez un pas à pas détaillé dans votre code. Le comportement du code est identique, mais la présentation du débogueur peut être très déroutante. Par conséquent, nous vous déconseillons d’utiliser **/OPT : ICF** dans les versions Debug, à moins que les avantages d’un code plus réduit compensent ces inconvénients.

> [!NOTE]
> Comme **/OPT : ICF** peut entraîner l’assignation de la même adresse à des fonctions différentes ou des membres de données en lecture seule (autrement dit, des **`const`** variables lorsqu’elles sont compilées à l’aide de **/Gy**), elle peut arrêter un programme qui dépend d’adresses uniques pour les fonctions ou les membres de données en lecture seule. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Les options **/OPT : LBR** et **/OPT : NOLBR** s’appliquent uniquement aux binaires ARM. Étant donné que certaines instructions de branche de processeur ARM ont une plage limitée, si l’éditeur de liens détecte un saut vers une adresse hors limite, il remplace l’adresse de destination de l’instruction de branche par l’adresse d’un « îlot » de code qui contient une instruction de branche qui cible la destination réelle. Vous pouvez utiliser **/OPT : LBR** pour optimiser la détection des instructions de longue branche et le positionnement des îlots de code intermédiaires afin de réduire la taille globale du code. **/OPT : NOLBR** indique à l’éditeur de liens de générer des îlots de code pour les longues instructions de branche à mesure qu’ils sont rencontrés, sans optimisation.

Par défaut, l’option **/OPT : LBR** est définie lorsque l’édition de liens incrémentielle n’est pas activée. Si vous souhaitez un lien non incrémentiel, mais pas des optimisations de branches longues, spécifiez **/OPT : NOLBR**. L’option **/OPT : LBR** désactive les liens incrémentiels.

## <a name="remarks"></a>Notes

En cas d’utilisation sur la ligne de commande, l’éditeur de liens utilise par défaut **/OPT : REF, ICF, LBR**. Si **/Debug** est spécifié, la valeur par défaut est **/OPT : NOREF, NOICF, NOLBR**.

Les optimisations **/OPT** diminuent généralement la taille de l’image et augmentent la vitesse du programme. Ces améliorations peuvent être importantes dans des programmes plus volumineux, c’est pourquoi ils sont activés par défaut pour les versions commerciales.

L’optimisation de l’éditeur de liens prend un temps supplémentaire, mais le code optimisé permet également de gagner du temps lorsque l’éditeur de liens a moins de réadressages à corriger et crée une image finale plus petite, et il économise encore plus de temps lorsqu’il a moins d’informations de débogage à traiter et à écrire dans le fichier PDB. Lorsque l’optimisation est activée, cela peut entraîner une liaison plus rapide dans le temps, car le coût supplémentaire de l’analyse peut être plus important que le décalage par les économies de temps que l’éditeur de liens passe sur des binaires plus petits.

Les arguments **/OPT** peuvent être spécifiés ensemble, séparés par des virgules. Par exemple, au lieu de **/OPT : Ref/OPT : NOICF**, vous pouvez spécifier **/OPT : REF, NOICF**.

Vous pouvez utiliser l’option [/Verbose](verbose-print-progress-messages.md) de l’éditeur de liens pour afficher les fonctions supprimées par **/OPT : Ref** et les fonctions repliées par **/OPT : ICF**.

Les arguments **/OPT** sont souvent définis pour les projets créés à l’aide de la boîte de dialogue **nouveau projet** dans l’IDE de Visual Studio, et ont généralement des valeurs différentes pour les configurations Debug et Release. Si aucune valeur n’est définie pour ces options de l’éditeur de liens dans votre projet, vous pouvez obtenir les valeurs par défaut du projet, qui peuvent être différentes des valeurs par défaut utilisées par l’éditeur de liens au niveau de la ligne de commande.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:ICF ou OPT:REF de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Optimization** .

1. Modifiez l'une des propriétés suivantes :

   - **Activer le pliage COMDAT**

   - **Informations de référence**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:LBR de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Command Line** .

1. Entrez l’option dans **options supplémentaires**:

   `/opt:lbr` ou `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
