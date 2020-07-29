---
title: 'Kit de développement logiciel (SDK) C++ Build Insights : table d’événements'
description: Référence d’événement pour le kit de développement logiciel (SDK) Visual Studio C++ Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b1cf6871329fcce3166495e173360a88ac38ee0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224212"
---
# <a name="c-build-insights-sdk-event-table"></a>Kit de développement logiciel (SDK) C++ Build Insights : table d’événements

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Événements du compilateur

[COMPILER](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Événements frontaux du compilateur

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Événements principaux du compilateur

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[THREAD](#thread)\
[FONCTIONNALITÉS](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Événements de l’éditeur de liens

[ÉDITEUR](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Table d’événements

| Événement | Propriété | Description |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Type | Activité |
|  | Parents | [COMPILER](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propriétés | -Chemin d’accès absolu au fichier source d’entrée<br/>-Chemin d’accès absolu au fichier objet de sortie |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Description | Se produit au démarrage et à l’arrêt de l’étape principale du compilateur. Ce test est responsable de l’optimisation du code source C/C++ analysé et de sa conversion en code machine. |
| <a name="bottom-up"></a>BOTTOM_UP | Type | Activité |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Description | Se produit au début et à la fin de la réussite de l’analyse de l’ensemble du programme. |
| <a name="c1-dll"></a>C1_DLL | Type | Activité |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Description | Se produit au début et à l’arrêt d’un *c1.dll* ou d’un appel de *c1xx.dll* . Ces dll sont le front-end C et C++ du compilateur. Ils sont appelés uniquement par le pilote du compilateur (*cl.exe*). |
| <a name="c2-dll"></a>C2_DLL | Type | Activité |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Description | Se produit au début et à l’arrêt d’un appel de *c2.dll* . Cette DLL est le back end du compilateur. Elle est appelée par le pilote du compilateur (*cl.exe*). Elle est également appelée par l’éditeur de liens (*link.exe*) lors de l’utilisation de la génération de code durant l’édition de liens. |
| <a name="code-generation"></a>CODE_GENERATION | Type | Activité |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [FONCTIONNALITÉS](#function)<br/>[THREAD](#thread) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Description | Se produit au début et à la fin de la phase de génération de code de back end. |
| <a name="command-line"></a>COMMAND_LINE | Type | Événement simple |
|  | Parents | [COMPILER](#compiler)<br/>[ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | -Ligne de commande utilisée pour appeler *cl.exe* ou *link.exe* |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | Description | Se produit lorsque le compilateur et l’éditeur de liens ont terminé l’évaluation de la ligne de commande. La ligne de commande évaluée comprend tous les paramètres *cl.exe* et *link.exe* transmis par le biais d’un fichier réponse. Il comprend également des paramètres pour *cl.exe* et *link.exe* passés via des variables d’environnement telles que Cl, \_ CL \_ , Link et \_ Link \_ . |
| <a name="compiler"></a>COMPILER | Type | Activité |
|  | Parents | None |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Propriétés | -Version du compilateur<br/>-Répertoire de travail<br/>-Chemin d’accès absolu au *cl.exe* appelé |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Compiler](cpp-event-data-types/compiler.md) |
|  | Description | Se produit au début et à l’arrêt d’un appel de *cl.exe* . |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Type | Événement simple |
|  | Parents | [COMPILER](#compiler)<br/>[ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | -Le nom de la variable d’environnement<br/>-La valeur de la variable d’environnement. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Description | Se produit une fois pour chaque variable d’environnement existante au moment *cl.exe* ou *link.exe* est appelée. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Type | Événement simple |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | -Chemin d’accès absolu à un fichier de sortie DLL ou exécutable. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Description | Se produit lorsque l’une des entrées de l’éditeur de liens est une DLL ou un fichier image exécutable. |
| <a name="exp-output"></a>EXP_OUTPUT | Type | Événement simple |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | : Chemin d’accès absolu à un fichier de sortie *. exp* . |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Description | Se produit lorsque l’une des sorties de l’éditeur de liens est un fichier *. exp* . |
| <a name="file-input"></a>FILE_INPUT | Type | Événement simple |
|  | Parents | [COMPILER](#compiler)<br/>[ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | : Chemin d’accès absolu au fichier d’entrée.<br/>-Le type de fichier d’entrée |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Description | Se produit pour annoncer une entrée de *cl.exe* ou *link.exe* . |
| <a name="force-inlinee"></a>FORCE_INLINEE | Type | Événement simple |
|  | Parents | [FONCTIONNALITÉS](#function) |
|  | Children | None |
|  | Propriétés | : Nom de la fonction force Inline.<br/>-Taille de la fonction forcée forcée, représentée sous la forme d’un nombre d’instructions intermédiaires. |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Description | Se produit lorsqu’une fonction est forcée d’être inline dans une autre fonction par le biais de l’utilisation du **`__forceinline`** mot clé. |
| <a name="front-end-file"></a>FRONT_END_FILE | Type | Activité |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | -Chemin d’accès absolu au fichier. |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Description | Se produit lorsque le serveur frontal du compilateur démarre et arrête le traitement d’un fichier. Cet événement est récursif. La récursivité se produit lorsque le serveur frontal analyse des fichiers inclus. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Type | Activité |
|  | Parents | [COMPILER](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Propriétés | -Chemin d’accès absolu au fichier source d’entrée<br/>-Chemin d’accès absolu au fichier objet de sortie |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Description | Se produit au début et à la fin de l’étape frontale du compilateur. Ce test est responsable de l’analyse du code source C/C++ et de sa conversion en langage intermédiaire. |
| <a name="function"></a>FONCTIONNALITÉS | Type | Activité |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[THREAD](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Propriétés | -Nom de la fonction |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Fonction](cpp-event-data-types/function.md) |
|  | Description | Se produit lors du démarrage et de la fin de la génération du code pour une fonction. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Type | Événement simple |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | : Chemin d’accès absolu à un fichier de sortie de la bibliothèque d’importation. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Description | Se produit lorsque l’une des sorties de l’éditeur de liens est une bibliothèque d’importation. |
| <a name="lib-output"></a>LIB_OUTPUT | Type | Événement simple |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | : Chemin d’accès absolu à un fichier de sortie de bibliothèque statique. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Description | Se produit lorsque l’une des sorties de l’éditeur de liens est une bibliothèque statique. |
| <a name="linker"></a>ÉDITEUR | Type | Activité |
|  | Parents | None |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Propriétés | -Version de l’éditeur de liens<br/>-Répertoire de travail<br/>-Chemin d’accès absolu au *link.exe* appelé |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Éditeur de liens](cpp-event-data-types/linker.md) |
|  | Description | Se produit au début et à l’arrêt d’un appel de *link.exe* . |
| <a name="ltcg"></a>LTCG | Type | Activité |
|  | Parents | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Description | Se produit au début et à l’arrêt de la génération du code durant l’édition de liens. |
| <a name="obj-output"></a>OBJ_OUTPUT | Type | Événement simple |
|  | Parents | [COMPILER](#compiler) |
|  | Children | None |
|  | Propriétés | -Chemin d’accès absolu au fichier de sortie *. obj* |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Description | Se produit une fois pour chaque sortie *. obj* produite par *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Type | Activité |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Description | Se produit au démarrage et à l’arrêt de l’optimisation de l’éditeur de liens (/OPT : ICF) identique. |
| <a name="opt-lbr"></a>OPT_LBR | Type | Activité |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Description | Se produit au début et à l’arrêt de l’optimisation de l’éditeur de liens Long Branch (/OPT : LBR). |
| <a name="opt-ref"></a>OPT_REF | Type | Activité |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Description | Se produit au démarrage et à l’arrêt des fonctions non référencées et de l’optimisation de l’éditeur de liens (/OPT : REF). |
| <a name="pass1"></a>PASS1 | Type | Activité |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Description | Se produit au début et à la fin de l’étape 1 de l’éditeur de liens. |
| <a name="pass2"></a>PASS2 | Type | Activité |
|  | Parents | [ÉDITEUR](#linker) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Description | Se produit au début et à la fin de l’étape 2 de l’éditeur de liens. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Type | Activité |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Description | Se produit au début et à la fin de l’étape d’optimisation de l’éditeur de liens qui élimine les fonctions et les données non référencées (/OPT : REF). Elle est effectuée avant la génération de code durant l’édition de liens. |
| <a name="symbol-name"></a>SYMBOL_NAME | Type | Événement simple |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | None |
|  | Propriétés | -Une clé de type<br/> -Le nom du type |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Description | Se produit à la fin de l’étape frontale : une fois pour chaque type impliqué dans les instanciations de modèle. La clé est un identificateur numérique pour le type, tandis que le nom est sa représentation textuelle. Les clés de type sont uniques au sein de la trace en cours d’analyse. Toutefois, différentes clés provenant de différentes passes front-end du compilateur peuvent pointer vers le même type. La comparaison des types entre les différentes passes frontales du compilateur requiert l’utilisation de leurs noms. Les événements SYMBOL_NAME sont émis à la fin d’une passe frontale du compilateur, une fois que toutes les instanciations de modèle ont eu lieu. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Type | Activité |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | -Clé pour le type spécialisé<br/>-Clé pour le type du modèle principal<br/>-Le type de modèle qui a été instancié |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Description | Se produit au début et à la fin d’une instanciation de modèle. Un type de modèle principal (tel que `vector` ) est instancié, ce qui donne un type spécialisé (tel que `std::vector<int>` ). Une clé est donnée pour les deux types. Utilisez l’événement [SYMBOL_NAME](#symbol-name) pour convertir une clé en nom de type. Les clés de type sont uniques au sein de la trace en cours d’analyse. Toutefois, différentes clés provenant de différentes passes front-end du compilateur peuvent pointer vers le même type. La comparaison des types entre les différentes passes frontales du compilateur requiert l’utilisation de noms de symboles. Cet événement est récursif. La récursivité se produit dans certains cas, lorsque le serveur frontal instancie des modèles imbriqués. |
| <a name="thread"></a>THREAD | Type | Activité |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FONCTIONNALITÉS](#function) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Thread](cpp-event-data-types/thread.md) |
|  | Description | Se produit au début et à la fin de l’exécution d’un thread principal du compilateur. Un thread en cours de suspension est considéré comme terminé. Un thread en cours de réveil est considéré comme démarré. |
| <a name="top-down"></a>TOP_DOWN | Type | Activité |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [FONCTIONNALITÉS](#function)<br/>[THREAD](#thread) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Description | Se produit au début et à la fin de l’exécution de l’analyse de l’ensemble du programme. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Type | Activité |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Description | Se produit au début et à la fin de la phase d’analyse de la totalité du programme de la génération de code durant l’édition de liens. |

::: moniker-end
