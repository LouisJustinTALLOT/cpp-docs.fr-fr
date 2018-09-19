---
title: Erreur du compilateur C2567 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb09aacc1b81e9f0e0c9c96a496eccc89a061f37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104232"
---
# <a name="compiler-error-c2567"></a>Erreur du compilateur C2567

Impossible d’ouvrir les métadonnées dans 'fichier', fichier peut avoir été supprimé ou déplacé

Un fichier de métadonnées qui a été référencé dans la source (avec `#using`) est introuvable dans le même répertoire par le processus de back-end du compilateur telle qu’elle était par le processus de front-end du compilateur. Consultez [#using, Directive](../../preprocessor/hash-using-directive-cpp.md) pour plus d’informations.

C2567 peut être générée si vous compilez avec **/c** sur un ordinateur, puis tentez une génération de code du moment de la liaison sur un autre ordinateur. Pour plus d’informations, consultez [/LTCG (Link-time Code Generation)](../../build/reference/ltcg-link-time-code-generation.md)).

Cela peut également indiquer que votre ordinateur n’avait aucun plus de mémoire.

Pour corriger cette erreur, assurez-vous que le fichier de métadonnées est dans le même emplacement de répertoire pour toutes les phases du processus de génération.