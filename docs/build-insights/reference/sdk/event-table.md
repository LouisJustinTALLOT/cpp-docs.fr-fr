---
title: 'C - Construire Insights SDK : table d’événements'
description: Référence de l’événement pour le Visual Studio CMD Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324134"
---
# <a name="c-build-insights-sdk-event-table"></a>C - Construire Insights SDK : table d’événements

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Événements Compilateur

[Compilateur](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Événements frontaux Compiler

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Événements de back-end Compiler

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Fil](#thread)\
[Fonction](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Événements Linker

[Linker](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1 (en)](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Table d’événement

| Événement | Propriété | Description |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Type | Activité |
|  | Parents | [Compilateur](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propriétés | - Voie absolue vers le fichier source d’entrée<br/>- Voie absolue vers le fichier d’objet de sortie |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[CompilerPass (CompilerPass)](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass (BackEndPass)](cpp-event-data-types/back-end-pass.md) |
|  | Description | Se produit au début et à l’arrêt du compilateur back-end pass. Ce laissez-passer est responsable de l’optimisation du code source C/Cmd analysé et de sa conversion en code machine. |
| <a name="bottom-up"></a>BOTTOM_UP | Type | Activité |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[BottomUp (bottomUp)](cpp-event-data-types/bottom-up.md) |
|  | Description | Se produit au début et à l’arrêt de l’ensemble de l’analyse du programme passe ascendante. |
| <a name="c1-dll"></a>C1_DLL | Type | Activité |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Description | Se produit au début et à l’arrêt d’une invocation *c1.dll* ou *c1xx.dll.* Ces DL sont l’extrémité avant C et C du compilateur. Ils sont invoqués uniquement par le pilote compilateur (*cl.exe*). |
| <a name="c2-dll"></a>C2_DLL | Type | Activité |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Description | Se produit au début et l’arrêt d’une invocation *c2.dll.* Ce DLL est l’arrière du compilateur. Il est appelé par le pilote compilateur (*cl.exe*). Il est également invoqué par le linker (*link.exe*) lorsque la génération de code lien-temps est utilisée. |
| <a name="code-generation"></a>CODE_GENERATION | Type | Activité |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [Fonction](#function)<br/>[Fil](#thread) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[La génération de code](cpp-event-data-types/code-generation.md) |
|  | Description | Se produit au début et à l’arrêt de la phase de génération de code de l’arrière. |
| <a name="command-line"></a>COMMAND_LINE | Type | Événement simple |
|  | Parents | [Compilateur](#compiler)<br/>[Linker](#linker) |
|  | Children | None |
|  | Propriétés | - La ligne de commande qui a été utilisée pour invoquer *cl.exe* ou *link.exe* |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Commandline](cpp-event-data-types/command-line.md) |
|  | Description | Se produit lorsque le compilateur et le lien sont effectués en évaluant la ligne de commande. La ligne de commande évaluée comprend tous les paramètres *cl.exe* et *link.exe* passés via un fichier de réponse. Il comprend également des paramètres pour *cl.exe* et *link.exe* \_passé via \_des\_variables de l’environnement tels que CL, \_CL , LINK, et LINK . |
| <a name="compiler"></a>Compilateur | Type | Activité |
|  | Parents | None |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Propriétés | - Version Compilateur<br/>- Annuaire de travail<br/>- Chemin absolu vers le *cl.exe* invoqué |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Compilateur](cpp-event-data-types/compiler.md) |
|  | Description | Se produit au début et l’arrêt d’une invocation *cl.exe.* |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Type | Événement simple |
|  | Parents | [Compilateur](#compiler)<br/>[Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le nom de la variable de l’environnement<br/>- La valeur de la variable de l’environnement. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Description | Se produit une fois pour chaque variable d’environnement existante au moment *cl.exe* ou *link.exe* est invoqué. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Type | Événement simple |
|  | Parents | [Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers un fichier de sortie DLL ou exécutable. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierOutput](cpp-event-data-types/file-output.md)<br/>[ExécutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Description | Se produit lorsque l’une des entrées de liaison est un DLL ou un fichier d’image exécutable. |
| <a name="exp-output"></a>EXP_OUTPUT | Type | Événement simple |
|  | Parents | [Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers un fichier de sortie *.exp.* |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput (expOutput)](cpp-event-data-types/exp-output.md) |
|  | Description | Se produit lorsque l’une des sorties de liaison est un fichier *.exp.* |
| <a name="file-input"></a>FILE_INPUT | Type | Événement simple |
|  | Parents | [Compilateur](#compiler)<br/>[Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers le fichier d’entrée<br/>- Le type de fichier d’entrée |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierInput](cpp-event-data-types/file-input.md) |
|  | Description | Se produit pour annoncer un *cl.exe* ou *link.exe* entrée. |
| <a name="force-inlinee"></a>FORCE_INLINEE | Type | Événement simple |
|  | Parents | [Fonction](#function) |
|  | Children | None |
|  | Propriétés | - Le nom de la fonction inlinée par la force.<br/>- La taille de la fonction inlinée par la force, représentée comme un nombre d’instructions intermédiaires. |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Description | Se produit quand une fonction est inlinisée de force `__forceinline` dans une autre fonction par l’utilisation du mot clé. |
| <a name="front-end-file"></a>FRONT_END_FILE | Type | Activité |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | - Chemin absolu vers le fichier. |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[FrontEndFile (FrontEndFile)](cpp-event-data-types/front-end-file.md) |
|  | Description | Se produit lorsque l’extrémité avant du compilateur démarre et cesse de traiter un fichier. Cet événement est récursif. La récursion se produit lorsque l’extrémité avant analyse les fichiers inclus. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Type | Activité |
|  | Parents | [Compilateur](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Propriétés | - Voie absolue vers le fichier source d’entrée<br/>- Voie absolue vers le fichier d’objet de sortie |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[CompilerPass (CompilerPass)](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass (frontEndPass)](cpp-event-data-types/front-end-pass.md) |
|  | Description | Se produit au début et à l’arrêt du col avant du compilateur. Ce laissez-passer est responsable de l’analyse du code source C/CM et de sa conversion en langage intermédiaire. |
| <a name="function"></a>Fonction | Type | Activité |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[Fil](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Propriétés | - Nom de la fonction |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Fonction](cpp-event-data-types/function.md) |
|  | Description | Se produit lors du démarrage et la fin de la génération du code pour une fonction. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Type | Événement simple |
|  | Parents | [Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers un fichier de sortie de bibliothèque d’importation. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput (impLibOutput)](cpp-event-data-types/imp-lib-output.md) |
|  | Description | Se produit lorsque l’une des sorties du linker est une bibliothèque d’importation. |
| <a name="lib-output"></a>LIB_OUTPUT | Type | Événement simple |
|  | Parents | [Linker](#linker) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers un fichier de sortie de bibliothèque statique. |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput (LibOutput)](cpp-event-data-types/lib-output.md) |
|  | Description | Se produit lorsque l’une des sorties du linker est la bibliothèque statique. |
| <a name="linker"></a>Linker | Type | Activité |
|  | Parents | None |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1 (en)](#pass1)<br/>[PASS2](#pass2) |
|  | Propriétés | - Version Linker<br/>- Annuaire de travail<br/>- Chemin absolu vers le *link.exe* invoqué |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Éditeur de liens](cpp-event-data-types/linker.md) |
|  | Description | Se produit au début et l’arrêt d’une invocation *link.exe.* |
| <a name="ltcg"></a>LTCG | Type | Activité |
|  | Parents | [PASS1 (en)](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Description | Se produit au début et à l’arrêt de la génération de code lien-temps. |
| <a name="obj-output"></a>OBJ_OUTPUT | Type | Événement simple |
|  | Parents | [Compilateur](#compiler) |
|  | Children | None |
|  | Propriétés | - Le chemin absolu vers le fichier de sortie *.obj* |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FichierOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput (ObjOutput)](cpp-event-data-types/obj-output.md) |
|  | Description | Se produit une fois pour chaque sortie *.obj* produite par *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Type | Activité |
|  | Parents | [PASS1 (en)](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptICF (optICF)](cpp-event-data-types/opt-icf.md) |
|  | Description | Se produit au début et à l’arrêt de l’optimisation identique du pliage COMDAT (/OPT:ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Type | Activité |
|  | Parents | [PASS1 (en)](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptLBR (OptLBR)](cpp-event-data-types/opt-lbr.md) |
|  | Description | Se produit au début et à l’arrêt de l’optimisation des liaisons à longue branche (/OPT:LBR). |
| <a name="opt-ref"></a>OPT_REF | Type | Activité |
|  | Parents | [PASS1 (en)](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[OptRef (en)](cpp-event-data-types/opt-ref.md) |
|  | Description | Se produit au début et à l’arrêt des fonctions non réenregistrées et de l’optimisation des liaisons (/OPT:REF). |
| <a name="pass1"></a>PASS1 (en) | Type | Activité |
|  | Parents | [Linker](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Description | Se produit au début et à l’arrêt du passage du linker 1. |
| <a name="pass2"></a>PASS2 | Type | Activité |
|  | Parents | [Linker](#linker) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Description | Se produit au début et à l’arrêt du passage du linker 2. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Type | Activité |
|  | Parents | [PASS1 (en)](#pass1) |
|  | Children | None |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Description | Se produit au début et à l’arrêt du passage d’optimisation des liaisons qui élimine les fonctions et les données non réfrécieuses (/OPT:REF). C’est fait avant la génération de code de lien-temps. |
| <a name="symbol-name"></a>SYMBOL_NAME | Type | Événement simple |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | None |
|  | Propriétés | - Une clé de type<br/> - Nom du type |
|  | Classes de capture | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName (symbolname)](cpp-event-data-types/symbol-name.md) |
|  | Description | Se produit à la fin de la passe frontale: une fois pour chaque type impliqué dans les instantanéisations de modèle. La clé est un identifiant numérique pour le type, tandis que le nom est sa représentation de texte. Les touches de type sont uniques dans la trace analysée. Cependant, différentes touches provenant de différentes passes frontale compilateur peuvent indiquer le même type. La comparaison des types entre les différentes passes frontales compilateur nécessite d’utiliser leurs noms. SYMBOL_NAME événements sont émis à la fin d’un pass front-end compilateur, après toutes les instantanés de modèle ont eu lieu. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Type | Activité |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propriétés | - La clé pour le type spécialisé<br/>- La clé pour le type du modèle principal<br/>- Le type de modèle qui a été instantané |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Description | Se produit au début et à la fin d’une instantanéisation de modèle. Un type de modèle `vector`primaire (tel que ) est instantané, `std::vector<int>`résultant en un type spécialisé (tel que ). Une clé est donnée pour les deux types. Utilisez [l’événement SYMBOL_NAME](#symbol-name) pour convertir une clé en nom du type. Les touches de type sont uniques dans la trace analysée. Cependant, différentes touches provenant de différentes passes frontale compilateur peuvent indiquer le même type. La comparaison des types entre les différentes passes frontales compilateur nécessite d’utiliser des noms de symboles. Cet événement est récursif. La récursion se produit dans certains cas lorsque l’extrémité avant est instantanée modèles imbriqués. |
| <a name="thread"></a>Fil | Type | Activité |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [Fonction](#function) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[Fil](cpp-event-data-types/thread.md) |
|  | Description | Se produit au début et à la fin d’une exécution de fil back-end compilateur. Un fil suspendu est considéré comme terminé. Un fil étant réveillé est considéré comme commencé. |
| <a name="top-down"></a>TOP_DOWN | Type | Activité |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [Fonction](#function)<br/>[Fil](#thread) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[TopDown (en)](cpp-event-data-types/top-down.md) |
|  | Description | Se produit au début et à l’arrêt de l’ensemble de l’analyse du programme' passage descendant. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Type | Activité |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Propriétés | None |
|  | Classes de capture | [Activité](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalyse](cpp-event-data-types/whole-program-analysis.md) |
|  | Description | Se produit au début et à l’arrêt de la phase d’analyse de l’ensemble du programme de la génération de code lien-temps. |

::: moniker-end
