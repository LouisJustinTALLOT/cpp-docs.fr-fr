---
description: 'En savoir plus sur : erreur du compilateur C2567'
title: Erreur du compilateur C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 113dfebc1ac6bde6857ea55fd6249fff12c9faae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209111"
---
# <a name="compiler-error-c2567"></a>Erreur du compilateur C2567

Impossible d’ouvrir les métadonnées dans’file', le fichier a peut-être été supprimé ou déplacé

Un fichier de métadonnées référencé dans la source (avec `#using` ) n’a pas été trouvé dans le même répertoire par le compilateur back end processus comme c’était le cas par le processus frontal du compilateur. Pour plus d’informations, consultez [#using directive](../../preprocessor/hash-using-directive-cpp.md) .

C2567 peut être provoquée si vous compilez avec **/c** sur un ordinateur, puis tentez une génération de code durant l’édition de liens sur un autre ordinateur. Pour plus d’informations, consultez [/LTCG (génération de code durant l’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md)).

Cela peut également indiquer que votre ordinateur n’a plus de mémoire.

Pour corriger cette erreur, assurez-vous que le fichier de métadonnées se trouve dans le même emplacement de répertoire pour toutes les phases du processus de génération.
