---
title: RUNTIME_FUNCTION, structure
ms.date: 11/04/2016
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
ms.openlocfilehash: 6b113f6cf1e9951f9e4578e15c9ed0af3d036fa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520248"
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