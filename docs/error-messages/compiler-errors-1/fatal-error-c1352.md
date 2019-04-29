---
title: Erreur irrécupérable C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329723"
---
# <a name="fatal-error-c1352"></a>Erreur irrécupérable C1352

Code MSIL non valide ou endommagé dans la fonction 'fonction' à partir de 'fichier' de module

Un fichier .netmodule a été passé au compilateur, mais le compilateur a détecté que le fichier était endommagé.  Demandez à l’auteur du fichier .netmodule de rechercher l’origine du problème.

Le compilateur ne recherche pas tous les types d’endommagements dans les fichiers .netmodule qu’il vérifie.  Toutefois, il vérifie que tous les chemins de contrôle d’une fonction contiennent bien une instruction return.

Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).