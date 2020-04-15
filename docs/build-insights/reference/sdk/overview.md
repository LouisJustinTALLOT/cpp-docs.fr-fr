---
title: Construire des aperçus SDK
description: Un aperçu du Visual Studio CMD Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323262"
---
# <a name="c-build-insights-sdk"></a>Construire des aperçus SDK

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Le SDK Build Insights de CMD Build Est une collection d’API qui vous permettent de créer des outils personnalisés au-dessus de la plate-forme de construction de CMD Insights. Cette page offre un aperçu de haut niveau pour vous aider à démarrer.

## <a name="obtaining-the-sdk"></a>Obtenir le SDK

Vous pouvez télécharger le SDK Build Insights en tant que forfait NuGet en suivant ces étapes :

1. À partir de Visual Studio 2017 et plus, créez un nouveau projet de C.
1. Dans le volet **Solution Explorer,** cliquez à droite sur votre projet.
1. Sélectionnez **Gérer les forfaits NuGet** dans le menu contextuelle.
1. En haut à droite, sélectionnez la source **nuget.org** paquet.
1. Recherchez la dernière version du forfait Microsoft.Cpp.BuildInsights.
1. Choisissez **Installer**.
1. Acceptez la licence.

Lisez la suite pour plus d’informations sur les concepts généraux entourant le SDK. Vous pouvez également accéder aux échantillons officiels [de GitHub](https://github.com/microsoft/cpp-build-insights-samples) pour voir des exemples d’applications réelles de CMD qui utilisent le SDK.

## <a name="collecting-a-trace"></a>Collecte d’une trace

L’utilisation du SDK Build Insights pour analyser les événements sortant de la chaîne d’outils MSVC exige que vous collectez d’abord une trace. Le SDK utilise Event Tracing for Windows (ETW) comme technologie de traçage sous-jacente. La collecte d’une trace peut se faire de deux façons :

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Méthode 1 : utilisation du vcperf dans Visual Studio 2019 et plus

1. Ouvrez une invitation de commande d’outils indigènes x64 surélevée pour VS 2019.
1. Exécutez la commande suivante : `vcperf /start MySessionName`
1. Générez votre projet.
1. Exécutez la commande suivante : `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Utilisez `/stopnoanalyze` la commande lors de l’arrêt de votre trace avec vcperf. Vous ne pouvez pas utiliser le SDK Build Insights pour `/stop` analyser les traces arrêtées par la commande régulière.

### <a name="method-2-programmatically"></a>Méthode 2 : programmatique

Utilisez l’une de ces fonctions de collecte de traces SDK Build Insights pour démarrer et arrêter les traces de façon programmatique. **Le programme qui exécute ces appels de fonction doit avoir des privilèges administratifs.** Seules les fonctions de démarrage et d’arrêt de traçage exigent des privilèges administratifs. Toutes les autres fonctions de la SDK Build Insights peuvent être exécutées sans elles.

### <a name="sdk-functions-related-to-trace-collection"></a>Fonctions SDK liées à la collecte de traces

| Fonctionnalités | API C++ | API C |
|--|--|--|
| Démarrer une trace | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Arrêt d’une trace | [StopTracingSession (en)](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW (en)](functions/stop-tracing-session-w.md) |
| Arrêter une trace et<br />l’analyse immédiate du résultat | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Arrêter une trace et<br />immédiatement relogging le résultat | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Les sections qui suivent vous montrent comment configurer une analyse ou une session de relogging. Il est nécessaire pour les fonctions de fonctionnalité combinée, telles que [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Consommation d’une trace

Une fois que vous avez une trace ETW, utilisez le SDK Build Insights de CMD pour le déballer. Le SDK vous donne les événements dans un format qui vous permet de développer vos outils rapidement. Nous ne vous recommandons pas de consommer la trace ETW brute sans utiliser le SDK. Le format d’événement utilisé par MSVC est sans papiers, optimisé pour évoluer vers d’énormes constructions, et difficile à donner un sens. De plus, l’API SDK Build Insights est stable, tandis que le format de traces ETW bruts est susceptible de changer sans préavis.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Types et fonctions SDK liés à la consommation de traces

| Fonctionnalités | API C++ | API C | Notes |
|--|--|--|--|
| Mise en place de rappels d’événements | [IAnalyzer (en)](other-types/ianalyzer-class.md)<br />[IRelogger IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Le SDK Build Insights de CMD fournit des événements par le biais de fonctions de rappel. Dans le C, implémentez les fonctions de rappel en créant un analyseur ou une classe de relogger qui hérite de l’interface IAnalyzer ou IRelogger. Dans C, implémentez les rappels dans les fonctions globales et fournissez des indications pour eux dans la structure ANALYSIS_CALLBACKS ou RELOG_CALLBACKS. |
| Groupes de construction | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | L’API CMD fournit des fonctions et des types d’aide pour regrouper plusieurs objets d’analyseur et de rélogger. Les groupes sont un moyen intéressant de diviser une analyse complexe en étapes plus simples. [vcperf](https://github.com/microsoft/vcperf) est organisé de cette façon. |
| Analyse ou rélogging | [Analyser](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyseA](functions/analyze-a.md)<br />[AnalyseW](functions/analyze-w.md)<br />[RelogA (RelogA)](functions/relog-a.md)<br />[RelogW (RelogW)](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analyse et rélogging

La consommation d’une trace se fait par une séance d’analyse ou une session de relogging.

L’utilisation d’une analyse régulière est appropriée pour la plupart des scénarios. Cette méthode vous donne la flexibilité `printf` de choisir votre format de sortie : texte, xml, JSON, base de données, appels REST, etc.

Le relogging est destiné à des analyses spéciales qui doivent produire un fichier de sortie ETW. À l’aide de la rélogging, vous pouvez traduire les événements Build Insights dans votre propre format d’événement ETW. Une utilisation appropriée du relogging serait d’accrocher les données de construction de CMD Insights à vos outils et infrastructures ETW existants. Par exemple, [le vcperf](https://github.com/microsoft/vcperf) utilise les interfaces de rélogging. C’est parce qu’il doit produire des données que l’analyseur de performance Windows, un outil ETW, peut comprendre. Une certaine connaissance préalable du fonctionnement etW est nécessaire si vous prévoyez d’utiliser les interfaces de réenquage.

### <a name="creating-analyzer-groups"></a>Création de groupes d’analyseurs

Il est important de savoir comment créer des groupes. Voici un exemple qui montre comment créer un groupe d’analyseur qui imprime *Bonjour, monde!* pour chaque événement de début d’activité qu’il reçoit.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>Utilisation d’événements

### <a name="sdk-types-and-functions-related-to-events"></a>Types et fonctions SDK liés aux événements

| Fonctionnalités | API C++ | API C | Notes |
|--|--|--|--|
| Événements d’appariement et de filtrage | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack (en)](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | L’API CMD offre des fonctions qui facilitent l’extraction des événements qui vous tiennent à cœur à partir de vos traces. Avec l’API C, ce filtrage doit se faire à la main. |
| Types de données d’événements | [Activité](cpp-event-data-types/activity.md)<br />[BackEndPass (BackEndPass)](cpp-event-data-types/back-end-pass.md)<br />[BottomUp (bottomUp)](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[La génération de code](cpp-event-data-types/code-generation.md)<br />[Commandline](cpp-event-data-types/command-line.md)<br />[Compilateur](cpp-event-data-types/compiler.md)<br />[CompilerPass (CompilerPass)](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Événement](cpp-event-data-types/event.md)<br />[Groupe d’événements](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExécutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput (expOutput)](cpp-event-data-types/exp-output.md)<br />[FichierInput](cpp-event-data-types/file-input.md)<br />[FichierOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile (FrontEndFile)](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass (frontEndPass)](cpp-event-data-types/front-end-pass.md)<br />[Fonction](cpp-event-data-types/function.md)<br />[ImpLibOutput (impLibOutput)](cpp-event-data-types/imp-lib-output.md)<br />[Invocation](cpp-event-data-types/invocation.md)<br />[Groupe d’invocation](cpp-event-data-types/invocation-group.md)<br />[LibOutput (LibOutput)](cpp-event-data-types/lib-output.md)<br />[Éditeur de liens](cpp-event-data-types/linker.md)<br />[LinkerGroup (linkerGroup)](cpp-event-data-types/linker-group.md)<br />[LinkerPass (LinkerPass)](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput (ObjOutput)](cpp-event-data-types/obj-output.md)<br />[OptICF (optICF)](cpp-event-data-types/opt-icf.md)<br />[OptLBR (OptLBR)](cpp-event-data-types/opt-lbr.md)<br />[OptRef (en)](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName (symbolname)](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup (en anglais)](cpp-event-data-types/template-instantiation-group.md)<br />[Fil](cpp-event-data-types/thread.md)<br />[TopDown (en)](cpp-event-data-types/top-down.md)<br />[TraceInfo (en)](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalyse](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Activités et événements simples

Les événements se présentent en deux catégories : *activités* et *événements simples.* Les activités sont des processus continus dans le temps qui ont un début et une fin. Les événements simples sont des événements ponctuels et n’ont pas de durée. Lors de l’analyse des traces DE MSVC avec le SDK Build Insights, vous recevrez des événements distincts lorsqu’une activité démarre et s’arrête. Vous ne recevrez qu’un seul événement lorsqu’un simple événement se produit.

### <a name="parent-child-relationships"></a>Relations parent-enfant

Les activités et les événements simples sont liés les uns aux autres par le biais de relations parent-enfant. Le parent d’une activité ou d’un événement simple est l’activité englobante dans laquelle ils se produisent. Par exemple, lors de la compilation d’un fichier source, le compilateur doit analyser le fichier, puis générer le code. Les activités de génération d’analyse et de code sont toutes deux des enfants de l’activité compilateur.

Les événements simples n’ont pas de durée, donc rien d’autre ne peut se produire à l’intérieur d’eux. En tant que tel, ils n’ont jamais d’enfants.

Les relations parent-enfant de chaque activité et événement simple sont indiquées dans le tableau de [l’événement.](event-table.md) Connaître ces relations est important lorsque vous consommez des événements build Insights. Vous devrez souvent compter sur eux pour comprendre le contexte complet d’un événement.

### <a name="properties"></a>Propriétés

Tous les événements ont les propriétés suivantes :

| Propriété | Description |
|--|--|
| Type d’identificateur | Un nombre qui identifie uniquement le type d’événement. |
| Identifiant d’instance | Un nombre qui identifie de façon unique l’événement dans la trace. Si deux événements du même type se produisent dans une trace, les deux obtiennent un identifiant d’instance unique. |
| Heure de début | L’heure à laquelle une activité a commencé ou l’heure où un simple événement s’est produit. |
| Identifiant de processus | Un numéro qui identifie le processus dans lequel l’événement s’est produit. |
| Identifiant de fil | Un numéro qui identifie le fil dans lequel l’événement s’est produit. |
| Indice de processeur | Un indice à base de zéro indiquant le processeur logique de l’événement émis par. |
| Nom d'événement | Une chaîne qui décrit le type d’événement. |

Toutes les activités autres que les événements simples ont également ces propriétés:

| Propriété | Description |
|--|--|
| Heure d’arrêt | Le moment où l’activité s’est arrêtée. |
| Durée exclusive | Le temps passé dans une activité, à l’exclusion du temps passé dans ses activités d’enfant. |
| Temps processeur | Le temps que le processeur a passé l’exécution du code dans le thread attaché à l’activité. Il n’inclut pas le temps où le fil attaché à l’activité dormait. |
| Heure CPU exclusive | Tout comme le temps de processeur, mais à l’exclusion du temps de processeur passé par les activités de l’enfant. |
| Responsabilité de temps de l’horloge de mur | La contribution de l’activité à l’heure globale de l’horloge murale. La responsabilité du temps de l’horloge de mur tient compte du parallélisme entre les activités. Supposons, par exemple, que deux activités non liées se déroulent en parallèle. Les deux ont une durée de 10 secondes, et exactement le même temps de départ et d’arrêt. Dans ce cas, Build Insights attribue à la fois une responsabilité de temps d’horloge murale de 5 secondes. En revanche, si ces activités se déroulent l’une après l’autre sans chevauchement, on leur confie une responsabilité de temps de 10 secondes. |
| Responsabilité exclusive de temps de l’horloge murale | Même chose que la responsabilité de temps de l’horloge murale, mais exclut la responsabilité de temps de l’horloge murale des activités de l’enfant. |

Certains événements ont leurs propres propriétés au-delà de ceux mentionnés. Dans ce cas, ces propriétés supplémentaires sont répertoriées dans le [tableau d’événements](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Événements de consommation fournis par le SDK Build Insights

#### <a name="the-event-stack"></a>La pile d’événements

Chaque fois que le SDK Build Insights de CMD vous donne un événement, il se présente sous la forme d’une pile. La dernière entrée dans la pile est l’événement actuel, et les entrées avant qu’il ne soit sa hiérarchie parente. Par exemple, les événements de démarrage et d’arrêt [de LTCG](event-table.md#ltcg) se produisent pendant le passage 1 du lien. Dans ce cas, la pile que \[vous recevrez contient: [LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. La hiérarchie parent est pratique parce que vous pouvez retracer un événement à sa racine. Si l’activité LTCG mentionnée ci-dessus est lente, vous pouvez immédiatement savoir quelle invocation de liaison a été impliquée.

#### <a name="matching-events-and-event-stacks"></a>Assortir les événements et les piles d’événements

Le SDK Build Insights de CMD vous donne chaque événement dans une trace, mais la plupart du temps vous ne vous souciez que d’un sous-ensemble d’entre eux. Dans certains cas, vous ne pouvez vous soucier d’un sous-ensemble de *piles d’événements*. Le SDK fournit des installations pour vous aider à extraire rapidement les événements ou la pile d’événements dont vous avez besoin, et à rejeter ceux dont vous n’avez pas. Il est fait à travers ces fonctions d’appariement:

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | Gardez un événement s’il correspond à l’un des types spécifiés. En avant des événements appariés à un lambda ou à un autre type callable. La hiérarchie des parents de l’événement n’est pas prise en compte par cette fonction. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Conservez un événement s’il correspond au type spécifié dans le paramètre d’une fonction de membre. Avant les événements appariés à la fonction membre. La hiérarchie des parents de l’événement n’est pas prise en compte par cette fonction. |
| [MatchEventStack (en)](functions/match-event-stack.md) | Gardez un événement si l’événement et sa hiérarchie des parents correspondent aux types spécifiés. Transmettons l’événement et les événements de hiérarchie des parents appariés à un lambda ou à un autre type callable. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Maintenez un événement si l’événement et sa hiérarchie parente correspondent aux types spécifiés dans la liste des paramètres d’une fonction de membre. Transmettons l’événement et les événements de hiérarchie des parents appariés à la fonction membre. |

Les fonctions de `MatchEventStack` correspondance de pile d’événements comme permettent des lacunes lors de la description de la hiérarchie des parents pour correspondre. Par exemple, vous pouvez dire que \[vous êtes intéressé par la pile [LINKER](event-table.md#linker), [LTCG.](event-table.md#ltcg) \] Il correspondrait \[également à la pile LINKER, [PASS1](event-table.md#pass1), LTCG.\] Le dernier type spécifié doit être le type d’événement pour correspondre, et ne fait pas partie de la hiérarchie des parents.

#### <a name="capture-classes"></a>Classes de capture

L’utilisation des `Match*` fonctions exige que vous spécifiiez les types que vous souhaitez assortir. Ces types sont sélectionnés à partir d’une liste de classes de *capture*. Les classes de capture se présentent dans plusieurs catégories, décrites ci-dessous.

| Category | Description |
|--|--|
| Exact | Ces classes de capture sont utilisées pour correspondre à un type d’événement spécifique et aucun autre. Un exemple est la classe [Compiler,](cpp-event-data-types/compiler.md) qui correspond à l’événement [COMPILER.](event-table.md#compiler) |
| Caractère générique | Ces classes de capture peuvent être utilisées pour correspondre à n’importe quel événement de la liste des événements qu’ils soutiennent. Par exemple, la wildcard [d’activité](cpp-event-data-types/activity.md) correspond à tout événement d’activité. Un autre exemple est la wildcard [CompilerPass,](cpp-event-data-types/compiler-pass.md) qui peut égaler soit le [FRONT_END_PASS](event-table.md#front-end-pass) ou [l’événement BACK_END_PASS.](event-table.md#back-end-pass) |
| Groupe | Les noms des classes de capture de groupe se terminent dans *le Groupe*. Ils sont utilisés pour correspondre à plusieurs événements du même type d’affilée, ignorant les lacunes. Ils n’ont de sens que lorsque vous faites correspondre des événements récursifs, parce que vous ne savez pas combien existent dans la pile d’événements. Par exemple, [l’activité FRONT_END_FILE](event-table.md#front-end-file) se produit chaque fois que le compilateur analyse un fichier. Cette activité est récursive parce que le compilateur peut trouver une directive inclure pendant qu’il analyse le fichier. La classe [FrontEndFile](cpp-event-data-types/front-end-file.md) ne correspond qu’à un seul FRONT_END_FILE événement dans la pile. Utilisez la classe [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) pour correspondre à la hiérarchie entière. |
| Groupe Wildcard | Un groupe wildcard combine les propriétés des wildcards et des groupes. La seule classe de cette catégorie est [InvocationGroup](cpp-event-data-types/invocation-group.md), qui correspondent et capturent tous les événements [LINKER](event-table.md#linker) et [COMPILER](event-table.md#compiler) dans une seule pile d’événements. |

Consultez la [table d’événements](event-table.md) pour savoir quelles classes de capture peuvent être utilisées pour correspondre à chaque événement.

#### <a name="after-matching-using-captured-events"></a>Après l’appariement : à l’aide d’événements capturés

Une fois qu’un `Match*` match se termine avec succès, les fonctions construisent les objets de la classe de capture et les transmettent à la fonction spécifiée. Utilisez ces objets de classe de capture pour accéder aux propriétés des événements.

#### <a name="example"></a>Exemple

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
