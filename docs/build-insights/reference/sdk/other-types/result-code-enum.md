---
title: Énumération RESULT_CODE
description: Le C++ Kit de développement logiciel (SDK) de Build Insights RESULT_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332298"
---
# <a name="result_code-enum"></a>Énumération RESULT_CODE

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

L’énumération `RESULT_CODE` décrit les conditions de réussite et d’échec.

## <a name="members"></a>Membres

| Name | Valeur | Description |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | L'opération a réussi. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | L’une de vos fonctions de rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) a retourné la valeur `CALLBACK_CODE_ANALYSIS_FAILURE`. Cette valeur est un membre de l’énumération [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | L’une de vos fonctions de rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) a retourné la valeur `CALLBACK_CODE_ANALYSIS_CANCEL`. Cette valeur est un membre de l’énumération [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | La trace d’Suivi d’v nements pour Windows d’entrée (ETW) spécifiée n’est pas valide. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Le suivi ETW de sortie spécifié n’est pas valide. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | La structure [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) n’a pas été initialisée correctement. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | La structure [RELOG_CALLBACKS](relog-callbacks-struct.md) n’a pas été initialisée correctement. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Impossible d’ouvrir le suivi ETW d’entrée. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Une erreur s’est produite lors du traitement du suivi ETW d’entrée. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Une erreur s’est produite lors de la tentative de démarrage de la session de rejournalisation. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | Il manque des événements importants dans la trace ETW d’entrée. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Vous utilisez C++ Build Insights sur une version non prise en charge de Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | Le nom de session fourni n’est pas valide. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Cette opération requiert des privilèges d’administrateur. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Une erreur s’est produite lors de la génération d’un GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Une erreur s’est produite lors de la tentative de détermination du chemin d’accès au répertoire temporaire. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Une erreur s’est produite lors de la tentative de création d’un répertoire temporaire pour le démarrage de la session de suivi. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Une erreur s’est produite lors de la tentative de démarrage de la trace du système. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Une erreur s’est produite lors de la tentative de démarrage de la trace MSVC. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Une erreur s’est produite lors de la tentative d’arrêt de la trace MSVC. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Une erreur s’est produite lors de la tentative de démarrage de la trace du système. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Une trace a été arrêtée, mais le répertoire temporaire de la session de suivi est introuvable. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Impossible de trouver le fichier de trace pour la trace MSVC en cours d’arrêt. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Une erreur s’est produite lors de la fusion des traces à l’aide du contrôle de trace du noyau. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | une erreur inconnue s'est produite. |

::: moniker-end
