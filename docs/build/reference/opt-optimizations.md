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
ms.openlocfilehash: 1a6fa8b9c923ff697831c29b8004ce360baf7d77
ms.sourcegitcommit: ae2f71fe0d64f1a90ef722759fe93c82abc064ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53587887"
---
# <a name="opt-optimizations"></a>/OPT (Optimisations)

Contrôle les optimisations effectuées par LINK pendant une génération.

## <a name="syntax"></a>Syntaxe

> **/ OPT :**{**REF** | **NOREF**}<br/>
> **/ OPT :**{**ICF**[**=**_itérations_] | **NOICF**}<br/>
> **/ OPT :**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Arguments

**REF** &AMP;#124; **NOREF**

**/ OPT : REF** élimine les fonctions et les données qui ne sont jamais référencées ; **/OPT : NOREF** conserve les fonctions et les données qui ne sont jamais référencées.

Lorsque/OPT : REF est activé, LINK supprime les fonctions packagées et données, appelées *COMDAT*. Cette optimisation porte le nom d'élimination COMDAT transitive. Le **/OPT : REF** option désactive également la liaison incrémentielle.

Fonctions inline et les fonctions membres définies à l’intérieur d’une déclaration de classe sont toujours COMDAT. Toutes les fonctions dans un fichier objet sont effectuées dans des COMDAT s’il est compilé à l’aide de la [/Gy](../../build/reference/gy-enable-function-level-linking.md) option. Pour placer **const** données dans des COMDAT, vous devez la déclarer à l’aide de `__declspec(selectany)`. Pour plus d’informations sur la façon de spécifier les données de la suppression ou le repli, consultez [selectany](../../cpp/selectany.md).

Par défaut, **/OPT : REF** est activée par l’éditeur de liens, sauf si **/OPT : NOREF** ou [/DEBUG](../../build/reference/debug-generate-debug-info.md) est spécifié. Pour remplacer cette valeur par défaut et conserver les COMDAT non référencés dans le programme, spécifiez **/OPT : NOREF**. Vous pouvez utiliser la [/INCLUDE](../../build/reference/include-force-symbol-references.md) option pour substituer la suppression d’un symbole spécifique.

Si [/DEBUG](../../build/reference/debug-generate-debug-info.md) est spécifié, la valeur par défaut pour **/OPT** est **NOREF**, et toutes les fonctions sont conservées dans l’image. Pour remplacer cette valeur par défaut et optimiser une version debug, spécifiez **/OPT : REF**. Cela peut réduire la taille de votre fichier exécutable et peut être construit une optimisation utile même en mode de débogage. Nous vous recommandons également spécifier **NOICF** pour conserver identiques fonctionne en mode de débogage se génère. Cela facilite la lecture des traces de la pile et la définition des points d’arrêt dans les fonctions qui seraient pliées ensemble dans le cas contraire.

**ICF**\[**=**_itérations_] &#124; **NOICF**

Utilisez **ICF**\[**=**_itérations_] pour effectuer un repli COMDAT identique. Les COMDAT redondants peuvent être supprimés de la sortie de l'éditeur de liens. Le paramètre facultatif *itérations* paramètre spécifie le nombre de fois pour parcourir les symboles pour les doublons. Le nombre d’itérations par défaut est 1. Des itérations supplémentaires peuvent permettre de localiser davantage de doublons n’ayant pas été détectés par pliage au cours de l’itération précédente.

Par défaut, **/OPT : ICF** est activée par l’éditeur de liens, sauf si **NOICF** ou [/DEBUG](../../build/reference/debug-generate-debug-info.md) est spécifié. Pour remplacer cette valeur par défaut et COMDAT empêcher d’être pliées dans le programme, spécifiez **NOICF**.

Dans une version debug, vous devez explicitement spécifier **/OPT : ICF** pour activer le pliage COMDAT. Toutefois, étant donné que **/OPT : ICF** pouvez fusionner des données identiques ou des fonctions, elle peut modifier les noms des fonctions qui apparaissent dans les traces de pile. Il peut également rendre impossible de définir des points d’arrêt dans certaines fonctions ou examiner des données dans le débogueur et vous permet d’accéder à des fonctions inattendues lorsque vous effectuez dans votre code. Le comportement du code est identique, mais la présentation du débogueur peut être très déroutant. Par conséquent, nous ne recommandons pas que vous utilisez **/OPT : ICF** dans les versions debug, sauf si les avantages de taille réduite du code compensent ces inconvénients.

> [!NOTE]
> Étant donné que **/OPT : ICF** peut entraîner la même adresse à affecter à différentes fonctions ou les membres de données en lecture seule (autrement dit, **const** lors de la compilation à l’aide de variables **/Gy**), Il peut interrompre un programme qui dépend des adresses uniques pour les fonctions ou les membres de données en lecture seule. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](../../build/reference/gy-enable-function-level-linking.md).

**LBR** &AMP;#124; **NOLBR**

Le **/OPT : LBR** et **/OPT:NOLBR** options s’appliquent uniquement aux fichiers binaires ARM. Étant donné que certaines instructions de branche de processeur ARM ont une plage limitée, si l’éditeur de liens détecte un saut vers une adresse hors limite, il remplace l’adresse de destination de l’instruction de branche par l’adresse d’un « îlot » de code contenant une instruction de branche qui cible la destination réelle. Vous pouvez utiliser **/OPT : LBR** pour optimiser la détection de longues instructions de branche et le positionnement des îlots de code intermédiaire afin de réduire la taille globale du code. **/OPT:NOLBR** indique à l’éditeur de liens pour générer des îlots de code pour les longues instructions de branche rencontrées, sans optimisation.

Par défaut, le **/OPT : LBR** option est définie lors de l’édition des liens incrémentielle ne sont pas activé. Si vous souhaitez une édition de liens non incrémentielle, mais pas les optimisations de longues branches, spécifiez **/OPT:NOLBR**. Le **/OPT : LBR** option désactive la liaison incrémentielle.

## <a name="remarks"></a>Notes

Lorsqu’il est utilisé à la ligne de commande, l’éditeur de liens par défaut est **/OPT : REF, ICF, LBR**. Si **/DEBUG** est spécifié, la valeur par défaut est **/OPT : NOREF, NOICF, NOLBR**.

Le **/OPT** optimisations généralement la taille de l’image et d’augmenter la vitesse du programme. Ces améliorations peuvent être importantes dans des programmes plus volumineux, c’est pourquoi elles sont activées par défaut pour les versions commerciales.

Optimisation de l’éditeur de liens prend plus de temps en amont, mais le code optimisé également fait gagner du temps lorsque l’éditeur de liens comporte des réadressages de moins à mettre à jour crée une image plus petite finale, et elle enregistre encore plus de temps quand il reste moins les informations de débogage pour traiter et écrire dans le fichier PDB. Lors de l’optimisation est activée, elle peut entraîner un temps de lien plus rapide en général, comme le petit coût supplémentaire dans l’analyse peut être plus que compensé par l’heure d’économies dans l’éditeur de liens passe sur les fichiers binaires plus petits.

Le **/OPT** arguments peuvent être spécifiés ensemble, séparées par des virgules. Par exemple, au lieu de **/OPT : REF NOICF**, vous pouvez spécifier **/OPT : REF, NOICF**.

Vous pouvez utiliser la [/verbose](../../build/reference/verbose-print-progress-messages.md) option de l’éditeur de liens pour afficher les fonctions qui ont été supprimées en **/OPT : REF** et les fonctions pliées par **/OPT : ICF**.

Le **/OPT** arguments sont souvent configurées pour les projets créés à l’aide de la **nouveau projet** boîte de dialogue dans l’IDE de Visual Studio, et ont généralement des valeurs différentes pour le débogage et les configurations release. Si aucune valeur n’est définie pour ces options de l’éditeur de liens dans votre projet, vous pouvez obtenir les valeurs par défaut du projet, qui peuvent être différentes des valeurs par défaut utilisés par l’éditeur de liens sur la ligne de commande.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:ICF ou OPT:REF de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Modifiez l'une des propriétés suivantes :

   - **Activation du repli COMDAT**

   - **Références**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l'option OPT:LBR de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans **des Options supplémentaires**:

   `/opt:lbr` ou `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)
