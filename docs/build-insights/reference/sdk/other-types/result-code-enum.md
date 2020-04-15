---
title: RESULT_CODE enum
description: La référence enum de build Insights CMD Build Insights RESULT_CODE.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323623"
---
# <a name="result_code-enum"></a>RESULT_CODE enum

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

L’enum `RESULT_CODE` décrit les conditions de réussite et d’échec.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x000000000) | L'opération a réussi. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Une de vos fonctions de rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou `CALLBACK_CODE_ANALYSIS_FAILURE` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) retourné la valeur. Cette valeur est membre de [l’enum CALLBACK_CODE.](callback-code-enum.md) |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x0000002) | Une de vos fonctions de rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou `CALLBACK_CODE_ANALYSIS_CANCEL` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) retourné la valeur. Cette valeur est membre de [l’enum CALLBACK_CODE.](callback-code-enum.md) |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | La trace d’entrée Event Tracing for Windows (ETW) spécifiée est invalide. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | La sortie etW trace spécifiée est invalide. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x0000005) | La [structure ANALYSIS_CALLBACKS n’a](analysis-callbacks-struct.md) pas été parascée correctement. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | La [structure RELOG_CALLBACKS n’a](relog-callbacks-struct.md) pas été parascée correctement. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | N’a pas ouvert la trace ETW entrée. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Une erreur s’est produite lors du traitement de la trace ETW d’entrée. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x0000009) | Une erreur s’est produite lorsque vous essayez de commencer la session de relogging. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x000000A) | La trace d’entrée ETW manque des événements importants. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x000000B) | Vous utilisez CMD Build Insights sur une version non étayée de Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x000000C) | Le nom de session fourni est invalide. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x000000D) | Cette opération nécessite des privilèges d’administrateur. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x000000E) | Une erreur s’est produite lors de la génération d’un GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x000000F) | Une erreur s’est produite en essayant de déterminer le chemin d’annuaire temporaire. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Une erreur s’est produite alors qu’il tentait de créer un répertoire temporaire pour la séance de traçage en cours de démarrage. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Une erreur s’est produite lorsque vous essayez de démarrer la trace du système. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Une erreur s’est produite lorsque vous essayez de démarrer la trace de MSVC. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Une erreur s’est produite lorsque vous avez tenté d’arrêter la trace du SMC. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Une erreur s’est produite lorsque vous essayez de démarrer la trace du système. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Une trace a été arrêtée, mais l’annuaire temporaire de la séance de traçage ne peut pas être trouvé. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Le dossier de trace de la trace MSVC arrêté ne peut pas être trouvé. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Une erreur s’est produite lors de la fusion des traces à l’aide de Kernel Trace Control. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Une erreur inconnue s'est produite. |

::: moniker-end
