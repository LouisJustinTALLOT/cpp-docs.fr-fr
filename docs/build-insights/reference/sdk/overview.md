---
title: Kit SDK C++ Build Insights
description: Vue d’ensemble du kit de développement logiciel (SDK) Visual Studio C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f53a9b6c682a0af7d8a01f6378ed0574d8fa4ca
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041170"
---
# <a name="c-build-insights-sdk"></a>Kit SDK C++ Build Insights

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Le kit de développement logiciel (SDK) C++ Build Insights est un ensemble d’API qui vous permettent de créer des outils personnalisés en plus de la plateforme C++ Build Insights. Cette page fournit une vue d’ensemble de haut niveau pour vous aider à commencer.

## <a name="obtaining-the-sdk"></a>Obtention du kit de développement logiciel

Vous pouvez télécharger le kit de développement logiciel (SDK) Build Insights en tant que package NuGet en procédant comme suit :

1. Dans Visual Studio 2017 et versions ultérieures, créez un nouveau projet C++.
1. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur votre projet.
1. Sélectionnez **gérer les packages NuGet** dans le menu contextuel.
1. En haut à droite, sélectionnez la source du package **NuGet.org** .
1. Recherchez la version la plus récente du package Microsoft. cpp. BuildInsights.
1. Choisissez **installer**.
1. Acceptez la licence.

Lisez la suite pour plus d’informations sur les concepts généraux entourant le kit de développement logiciel (SDK). Vous pouvez également accéder au [référentiel GitHub officiel des exemples de génération Insights c++](https://github.com/microsoft/cpp-build-insights-samples) pour obtenir des exemples d’applications c++ réelles qui utilisent le kit de développement logiciel (SDK).

## <a name="collecting-a-trace"></a>Collecte d’une trace

L’utilisation du kit de développement logiciel (SDK) C++ Build Insights pour analyser les événements provenant du chaîne d’outils MSVC nécessite la première collecte d’une trace. Le kit de développement logiciel (SDK) utilise Suivi d’v nements pour Windows (ETW) comme technologie de suivi sous-jacente. La collecte d’une trace peut être effectuée de deux manières :

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Méthode 1 : utilisation de vcperf dans Visual Studio 2019 et versions ultérieures

1. Ouvrez un Invite de commandes des outils natifs x64 élevé pour VS 2019.
1. Exécutez la commande suivante : `vcperf /start MySessionName`
1. Générez votre projet.
1. Exécutez la commande suivante : `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Utilisez la `/stopnoanalyze` commande lors de l’arrêt de votre trace avec vcperf. Vous ne pouvez pas utiliser le kit de développement logiciel (SDK) Build Insights C++ pour analyser les traces arrêtées par la `/stop` commande normale.

### <a name="method-2-programmatically"></a>Méthode 2 : par programmation

Utilisez l’une de ces fonctions de collection de trace du kit de développement logiciel (SDK) Build Insights C++ pour démarrer et arrêter des traces par programmation. **Le programme qui exécute ces appels de fonction doit disposer de privilèges d’administrateur.** Seules les fonctions de suivi de démarrage et d’arrêt requièrent des privilèges d’administrateur. Toutes les autres fonctions du kit de développement logiciel (SDK) Build Insights C++ peuvent être exécutées sans elles.

### <a name="sdk-functions-related-to-trace-collection"></a>Fonctions du SDK relatives à la collecte de trace

| Fonctionnalités | API C++ | API C |
|--|--|--|
| Démarrage d’une trace | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Arrêt d’une trace | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Arrêt d’une trace et<br />analyse immédiate du résultat | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Arrêt d’une trace et<br />rejournalisation immédiate du résultat | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Les sections qui suivent vous montrent comment configurer une analyse ou une session de rejournalisation. Elle est requise pour les fonctions de fonctionnalités combinées, telles que [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Consommation d’une trace

Une fois que vous avez une trace ETW, utilisez le kit de développement logiciel (SDK) Build Insights C++ pour la décompresser. Le kit de développement logiciel (SDK) vous donne les événements dans un format qui vous permet de développer rapidement vos outils. Nous vous déconseillons d’utiliser le suivi ETW brut sans utiliser le kit de développement logiciel (SDK). Le format d’événement utilisé par MSVC est non documenté, optimisé pour s’adapter à des builds énormes et difficile à comprendre. En outre, l’API du SDK C++ Build Insights est stable, tandis que le format de trace ETW brut peut faire l’objet de modifications sans préavis.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Types et fonctions de SDK liés à la consommation de trace

| Fonctionnalités | API C++ | API C | Notes |
|--|--|--|--|
| Configuration des rappels d’événements | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Le kit de développement logiciel (SDK) C++ Build Insights fournit des événements via des fonctions de rappel. En C++, implémentez les fonctions de rappel en créant un analyseur ou une classe de rejournalisation qui hérite de l’interface IAnalyzer ou IRelogger. En C, implémentez les rappels dans les fonctions globales et fournissez-leur des pointeurs dans la structure ANALYSIS_CALLBACKS ou RELOG_CALLBACKS. |
| Génération de groupes | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | L’API C++ fournit des fonctions d’assistance et des types pour regrouper plusieurs analyseurs et objets de rejournalisation. Les groupes sont un moyen pratique de diviser une analyse complexe en étapes plus simples. [vcperf](https://github.com/microsoft/vcperf) est organisé de cette manière. |
| Analyse ou rejournalisation | [Analyser](functions/analyze.md)<br />[Rejournaliser](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analyse et rejournalisation

L’utilisation d’une trace est effectuée par le biais d’une session d’analyse ou d’une session de rejournalisation.

L’utilisation d’une analyse régulière convient à la plupart des scénarios. Cette méthode vous donne la possibilité de choisir le format de sortie : `printf` texte, XML, JSON, base de données, appels REST, etc.

La reconnexion est réservée à des analyses à usage spécifique qui doivent produire un fichier de sortie ETW. À l’aide de la journalisation, vous pouvez traduire les événements de build Insights C++ dans votre propre format d’événement ETW. Une utilisation appropriée de la rejournalisation serait de raccorder les données de build Insights C++ à vos outils et infrastructure ETW existants. Par exemple, [vcperf](https://github.com/microsoft/vcperf) utilise les interfaces de rejournalisation. C’est parce qu’il doit produire des données que l’analyseur de performances Windows, un outil ETW, peut comprendre. Une connaissance préalable du fonctionnement d’ETW est nécessaire si vous envisagez d’utiliser les interfaces de rejournalisation.

### <a name="creating-analyzer-groups"></a>Création de groupes d’analyseurs

Il est important de savoir comment créer des groupes. Voici un exemple qui montre comment créer un groupe d’analyseur qui imprime *Hello, World !* pour chaque événement de démarrage d’activité qu’il reçoit.

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

### <a name="sdk-types-and-functions-related-to-events"></a>Types et fonctions du kit de développement logiciel (SDK) associés aux événements

| Fonctionnalités | API C++ | API C | Notes |
|--|--|--|--|
| Correspondance et filtrage des événements | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | L’API C++ offre des fonctions qui facilitent l’extraction des événements qui vous intéressent à partir de vos traces. Avec l’API C, ce filtrage doit être effectué manuellement. |
| Types de données d’événement | [Activité](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[Compilateur](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Event](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Fonction](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Invocation](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Éditeur de liens](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Thread](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Activités et événements simples

Les événements se présentent sous deux catégories : les *activités* et les *événements simples*. Les activités sont des processus en cours dans le temps qui ont un début et une fin. Les événements simples sont des occurrences ponctuelles et n’ont pas de durée. Lors de l’analyse des traces MSVC avec le kit de développement logiciel (SDK) C++ Build Insights, vous recevrez des événements distincts quand une activité démarre et s’arrête. Vous ne recevrez qu’un seul événement lorsqu’un événement simple se produit.

### <a name="parent-child-relationships"></a>Relations parent-enfant

Les activités et les événements simples sont liés les uns aux autres par le biais de relations parent-enfant. Le parent d’une activité ou d’un événement simple est l’activité englobante dans laquelle elles se produisent. Par exemple, lors de la compilation d’un fichier source, le compilateur doit analyser le fichier, puis générer le code. Les activités d’analyse et de génération de code sont toutes deux des enfants de l’activité du compilateur.

Les événements simples n’ont pas de durée, donc rien d’autre ne peut se produire à l’intérieur de celles-ci. Par conséquent, ils n’ont jamais d’enfants.

Les relations parent-enfant de chaque activité et événement simple sont indiquées dans la [table d’événements](event-table.md). Il est important de connaître ces relations lorsque vous consommez des événements C++ Build Insights. Vous devez souvent vous appuyer sur ces derniers pour comprendre le contexte complet d’un événement.

### <a name="properties"></a>Propriétés

Tous les événements ont les propriétés suivantes :

| Property | Description |
|--|--|
| Identificateur de type | Numéro qui identifie de façon unique le type d’événement. |
| Identificateur d’instance | Numéro qui identifie de façon unique l’événement dans la trace. Si deux événements du même type se produisent dans une trace, tous deux reçoivent un identificateur d’instance unique. |
| Heure de début | L’heure de début d’une activité ou l’heure à laquelle un événement simple s’est produit. |
| Identificateur de processus | Numéro qui identifie le processus dans lequel l’événement s’est produit. |
| Identificateur du thread | Numéro qui identifie le thread dans lequel l’événement s’est produit. |
| Index du processeur | Index de base zéro indiquant le processeur logique par lequel l’événement a été émis. |
| Nom d'événement | Chaîne qui décrit le type d’événement. |

Toutes les activités autres que les événements simples ont également les propriétés suivantes :

| Property | Description |
|--|--|
| Heure d’arrêt | Heure à laquelle l’activité s’est arrêtée. |
| Durée exclusive | Temps passé dans une activité, à l’exclusion du temps passé dans ses activités enfants. |
| Temps processeur | Temps passé par l’UC à exécuter du code dans le thread attaché à l’activité. Elle n’inclut pas l’heure à laquelle le thread attaché à l’activité était en veille. |
| Temps processeur exclusif | Identique au temps processeur, mais exclut le temps processeur passé par les activités enfants. |
| Responsabilité du temps du mur | Contribution de l’activité à l’heure d’horloge globale. La responsabilité de l’horloge du mur prend en compte le parallélisme entre les activités. Par exemple, supposons que deux activités non liées s’exécutent en parallèle. Les deux ont une durée de 10 secondes et exactement la même heure de début et de fin. Dans ce cas, la génération d’Insights affecte une responsabilité de temps horloge de 5 secondes. En revanche, si ces activités s’exécutent l’une après l’autre sans chevauchement, elles reçoivent une responsabilité de temps horloge de 10 secondes. |
| Responsabilité exclusive du temps horloge du mur | Identique à la responsabilité du temps horloge du mur, mais exclut la responsabilité du temps horloge des activités enfants. |

Certains événements ont leurs propres propriétés au-delà de celles mentionnées. Dans ce cas, ces propriétés supplémentaires sont répertoriées dans la [table d’événements](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Utilisation des événements fournis par le kit de développement logiciel (SDK) Build Insights C++

#### <a name="the-event-stack"></a>Pile des événements

Chaque fois que le kit de développement logiciel (SDK) C++ Build Insights vous donne un événement, il est fourni sous la forme d’une pile. La dernière entrée de la pile est l’événement actuel, et les entrées avant sa hiérarchie parente. Par exemple, les événements de démarrage et d’arrêt de [LTCG](event-table.md#ltcg) se produisent pendant la passe 1 de l’éditeur de liens. Dans ce cas, la pile que vous souhaitez recevoir contient : \[ [Linker](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG \] . La hiérarchie parente est pratique, car vous pouvez remonter un événement à sa racine. Si l’activité LTCG mentionnée ci-dessus est lente, vous pouvez découvrir immédiatement l’appel de l’éditeur de liens qui a été impliqué.

#### <a name="matching-events-and-event-stacks"></a>Événements et piles d’événements correspondants

Le kit de développement logiciel (SDK) C++ Build Insights vous donne chaque événement dans une trace, mais la plupart du temps, vous ne vous souciez que d’un sous-ensemble de ces événements. Dans certains cas, vous ne vous souciez que d’un sous-ensemble de *piles d’événements*. Le kit de développement logiciel (SDK) fournit des fonctionnalités qui vous permettent d’extraire rapidement les événements ou la pile d’événements dont vous avez besoin, et de rejeter ceux dont vous n’avez pas besoin. Pour ce faire, vous disposez des fonctions de correspondance suivantes :

| Fonction | Description |
|--|--|
| [MatchEvent](functions/match-event.md) | Conserver un événement s’il correspond à l’un des types spécifiés. Transférer les événements correspondants à un type lambda ou un autre type pouvant être appelé. La hiérarchie parente de l’événement n’est pas prise en compte par cette fonction. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Conservez un événement s’il correspond au type spécifié dans le paramètre d’une fonction membre. Transférer les événements correspondants à la fonction membre. La hiérarchie parente de l’événement n’est pas prise en compte par cette fonction. |
| [MatchEventStack](functions/match-event-stack.md) | Conserver un événement si l’événement et sa hiérarchie parente correspondent aux types spécifiés. Transférez l’événement et les événements de hiérarchie parente correspondants à une expression lambda ou un autre type pouvant être appelé. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Conserver un événement si l’événement et sa hiérarchie parente correspondent à ceux spécifiés dans la liste de paramètres d’une fonction membre. Transférer l’événement et les événements de hiérarchie parente correspondants à la fonction membre. |

Les fonctions de mise en correspondance des piles d’événements telles que `MatchEventStack` autorisent les intervalles lors de la description de la hiérarchie parente. Par exemple, vous pouvez indiquer que vous êtes intéressé par l' \[ [éditeur de liens](event-table.md#linker), la pile [LTCG](event-table.md#ltcg) \] . Elle correspond également à l' \[ éditeur de liens, [PASS1](event-table.md#pass1), la \] pile LTCG. Le dernier type spécifié doit être le type d’événement à mettre en correspondance et ne fait pas partie de la hiérarchie parente.

#### <a name="capture-classes"></a>Classes de capture

L’utilisation des `Match*` fonctions requiert que vous spécifiiez les types que vous souhaitez faire correspondre. Ces types sont sélectionnés dans une liste de *classes de capture*. Les classes de capture sont disponibles dans plusieurs catégories, décrites ci-dessous.

| Category | Description |
|--|--|
| Exact | Ces classes de capture sont utilisées pour mettre en correspondance un type d’événement spécifique et aucune autre. La classe [du compilateur](cpp-event-data-types/compiler.md) , qui correspond à l’événement [du compilateur](event-table.md#compiler) , en est un exemple. |
| Caractère générique | Ces classes de capture peuvent être utilisées pour mettre en correspondance n’importe quel événement de la liste des événements qu’ils prennent en charge. Par exemple, le caractère générique d' [activité](cpp-event-data-types/activity.md) correspond à n’importe quel événement d’activité. Un autre exemple est le caractère générique [CompilerPass](cpp-event-data-types/compiler-pass.md) , qui peut correspondre à l' [FRONT_END_PASS](event-table.md#front-end-pass) ou à l’événement [BACK_END_PASS](event-table.md#back-end-pass) . |
| Group | Les noms des classes de capture de groupe se terminent par *groupe*. Ils sont utilisés pour faire correspondre plusieurs événements du même type dans une ligne, en ignorant les écarts. Ils n’ont de sens que lors de la correspondance des événements récursifs, car vous ne savez pas combien existent dans la pile des événements. Par exemple, l’activité [FRONT_END_FILE](event-table.md#front-end-file) se produit chaque fois que le compilateur analyse un fichier. Cette activité est récursive car le compilateur peut trouver une directive include lors de l’analyse du fichier. La classe [FrontEndFile](cpp-event-data-types/front-end-file.md) correspond à un seul événement FRONT_END_FILE dans la pile. Utilisez la classe [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) pour correspondre à la hiérarchie include entière. |
| Groupe de caractères génériques | Un groupe de caractères génériques combine les propriétés des caractères génériques et des groupes. La seule classe de cette catégorie est [InvocationGroup](cpp-event-data-types/invocation-group.md), qui correspond et capture tous les événements de l' [éditeur de liens](event-table.md#linker) et [du compilateur](event-table.md#compiler) dans une pile d’événements unique. |

Reportez-vous à la [table d’événements](event-table.md) pour savoir quelles classes de capture peuvent être utilisées pour mettre en correspondance chaque événement.

#### <a name="after-matching-using-captured-events"></a>Après correspondance : utilisation des événements capturés

Une fois qu’une correspondance est terminée, les `Match*` fonctions construisent les objets de classe de capture et les transfèrent à la fonction spécifiée. Utilisez ces objets de classe de capture pour accéder aux propriétés des événements.

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
