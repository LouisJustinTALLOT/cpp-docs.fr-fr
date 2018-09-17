---
title: RUNTIME_FUNCTION, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718235"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION, structure

Gestion des exceptions basée sur une table nécessite une entrée de table pour toutes les fonctions qui allouent des espace de pile ou appellent une autre fonction (par exemple, les fonctions non-feuille). Les entrées de table de fonction ont le format :

|||
|-|-|
|ULONG|Adresse de début (fonction)|
|ULONG|Adresse de fin (fonction)|
|ULONG|Adresse des informations de déroulement|

La structure RUNTIME_FUNCTION doit être DWORD aligné en mémoire. Toutes les adresses sont relatives à l’image, autrement dit, ils sont des décalages de 32 bits à partir de l’adresse de départ de l’image qui contient l’entrée de table de fonction. Ces entrées sont triées et placées dans la section .pdata d’une image PE32 +. Pour les fonctions générées dynamiquement [compilateurs JIT], le runtime pour prendre en charge ces fonctions doit utiliser RtlInstallFunctionTableCallback ou RtlAddFunctionTable pour fournir ces informations pour le système d’exploitation. Cela entraîne non fiables gestion des exceptions et débogage de processus.

## <a name="see-also"></a>Voir aussi

[Données de déroulement pour la gestion des exceptions et la prise en charge du débogueur](../build/unwind-data-for-exception-handling-debugger-support.md)