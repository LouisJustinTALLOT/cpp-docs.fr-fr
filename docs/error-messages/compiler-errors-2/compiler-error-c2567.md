---
title: Erreur du compilateur C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366353"
---
# <a name="compiler-error-c2567"></a>Erreur du compilateur C2567

Impossible d’ouvrir les métadonnées dans 'fichier', fichier peut avoir été supprimé ou déplacé

Un fichier de métadonnées qui a été référencé dans la source (avec `#using`) est introuvable dans le même répertoire par le processus de back-end du compilateur telle qu’elle était par le processus de front-end du compilateur. Consultez [#using, Directive](../../preprocessor/hash-using-directive-cpp.md) pour plus d’informations.

C2567 peut être générée si vous compilez avec **/c** sur un ordinateur, puis tentez une génération de code du moment de la liaison sur un autre ordinateur. Pour plus d’informations, consultez [/LTCG (Link-time Code Generation)](../../build/reference/ltcg-link-time-code-generation.md)).

Cela peut également indiquer que votre ordinateur n’avait aucun plus de mémoire.

Pour corriger cette erreur, assurez-vous que le fichier de métadonnées est dans le même emplacement de répertoire pour toutes les phases du processus de génération.