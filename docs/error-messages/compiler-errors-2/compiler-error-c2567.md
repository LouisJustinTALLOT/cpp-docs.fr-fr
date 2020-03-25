---
title: Erreur du compilateur C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177454"
---
# <a name="compiler-error-c2567"></a>Erreur du compilateur C2567

Impossible d’ouvrir les métadonnées dans’file', le fichier a peut-être été supprimé ou déplacé

Un fichier de métadonnées référencé dans la source (avec `#using`) est introuvable dans le même répertoire par le compilateur back end processus comme c’était le cas par le processus frontal du compilateur. Pour plus d’informations, consultez [#using directive](../../preprocessor/hash-using-directive-cpp.md) .

C2567 peut être provoquée si vous compilez avec **/c** sur un ordinateur, puis tentez une génération de code durant l’édition de liens sur un autre ordinateur. Pour plus d’informations, consultez [/LTCG (génération de code durant l’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md)).

Cela peut également indiquer que votre ordinateur n’a plus de mémoire.

Pour corriger cette erreur, assurez-vous que le fichier de métadonnées se trouve dans le même emplacement de répertoire pour toutes les phases du processus de génération.
